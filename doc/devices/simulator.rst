The Simulator device
====================

You can instantiate the Qrack device in PennyLane as follows:

.. code-block:: python

    import pennylane as qml
    from catalyst import qjit # optional, for JIT compilation

    dev = qml.device('qrack.simulator', wires=2)

This device can then be used just like other devices for the definition and evaluation of QNodes within PennyLane.
A simple quantum function that returns the expectation value of a measurement and depends on three classical input
parameters would look like:

.. code-block:: python

    @qjit # optional, for JIT compilation
    @qml.qnode(dev)
    def circuit(x, y, z):
        qml.RZ(z, wires=[0])
        qml.RY(y, wires=[0])
        qml.RX(x, wires=[0])
        qml.CNOT(wires=[0, 1])
        return qml.expval(qml.PauliZ(wires=1))

You can then execute the circuit like any other function to get the quantum mechanical expectation value.

.. code-block:: python

    circuit(0.2, 0.1, 0.3)

Device options
~~~~~~~~~~~~~~

By default, Qrack will automatically and "transparently" switch between CPU-based and GPU-based methods as would
be most appropriate for best performance. Qrack will also automatically use the "hybrid simulation algorithm"
"layers" that tend to work best for general "BQP-complete" tasks like random circuit sampling.

If you'd like to use a special-case algorithm, like quantum binary decision diagrams (QBDD), or if you want more
direct control over choice of algorithm and hardware used, there are a series of boolean options users can toggle
like so:

.. code-block:: python

    dev = qml.device('Qrack.simulator', wires=2, isBinaryDecisionTree=True)


This is a complete list of boolean options and their meanings:
- `isStabilizerHybrid`: Use "hybrid" stabilizer optimization? (Default is "`True`"; non-Clifford circuits will fall back to near-Clifford or universal simulation) 
- `isTensorNetwork`: Use "tensor network" optimization? (Default is "`True`"; prevents dynamic qubit de-allocation; might function sub-optimally with "hybrid" stabilizer enabled)
- `isSchmidtDecompose`: Use Schmidt decomposition optimizations? (Default is "`True`")
- `isSchmidtDecomposeMulti`: Distribute Schmidt-decomposed qubit subsystems to multiple GPUs or accelerators, if available? (Default is "`True`"; mismatched device capacities might hurt overall performance)
- `isBinaryDecisionTree`: Use "quantum binary decision diagram" ("QBDD") methods? (Default is "`False`"; note that QBDD is CPU-only)
- `isOpenCL`: Use GPU acceleration? (Default is "`True`")
- `isHostPointer`: Allocate GPU buffer from general host heap? (Default is "`False`"; "`True`" might improve performance or reliability in certain cases, like if using an Intel HD as accelerator)

Supported operations
~~~~~~~~~~~~~~~~~~~~

The ``qrack.simulator`` device supports all PennyLane
`operations and observables <https://pennylane.readthedocs.io/en/stable/introduction/operations.html>`_:
