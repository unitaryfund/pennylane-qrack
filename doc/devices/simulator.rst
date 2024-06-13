The Simulator device
====================

You can instantiate the qrack device in PennyLane as follows:

.. code-block:: python

    import pennylane as qml

    dev = qml.device('qrack.simulator', wires=2)

This device can then be used just like other devices for the definition and evaluation of QNodes within PennyLane.
A simple quantum function that returns the expectation value of a measurement and depends on three classical input
parameters would look like:

.. code-block:: python

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


.. note::

    For more information, check the
    `Qrack documentation <https://qrack.readthedocs.io/en/latest/>`_  for details.




Supported operations
~~~~~~~~~~~~~~~~~~~~

The ``qrac.simulator`` device supports all PennyLane
`operations and observables <https://pennylane.readthedocs.io/en/stable/introduction/operations.html>`_:
