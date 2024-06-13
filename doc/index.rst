PennyLane-Qrack Plugin
#######################

:Release: |release|

.. include:: ../README.rst
  :start-after:	header-start-inclusion-marker-do-not-remove
  :end-before: header-end-inclusion-marker-do-not-remove

Once PennyLane-Qrack is installed, the provided Qrack devices can be accessed straight
away in PennyLane, without the need to import any additional packages.

Devices
~~~~~~~

Currently, PennyLane-Qrack provides one Qrack device for PennyLane:

.. title-card::
    :name: 'qrack.simulator'
    :description: Qrack's simulator backend.
    :link: devices/simulator.html

.. raw:: html

        <div style='clear:both'></div>
        </br>

.. include:: ../README.rst
  :start-after:	benchmarks-start-inclusion-marker-do-not-remove
  :end-before: benchmarks-end-inclusion-marker-do-not-remove

Tutorials
~~~~~~~~~


Check out these demos to see the PennyLane-Qrack plugin in action:

.. raw:: html

    <div class="row">

.. title-card::
    :name: Intro to QAOA
    :description: <img src="https://pennylane.ai/_images/qaoa_layer.png" width="100%" />
    :link:  https://pennylane.ai/qml/demos/tutorial_qaoa_intro.html


.. raw:: html

    </div></div><div style='clear:both'> <br/>


You can use any of the qubit based `demos
from the PennyLane documentation <https://pennylane.ai/qml/demonstrations.html>`_, for example
the tutorial on `qubit rotation <https://pennylane.ai/qml/demos/tutorial_qubit_rotation.html>`_,
and simply replace ``'default.qubit'`` with the ``'qrack.simulator'`` device:

.. code-block:: python

    dev = qml.device('qrack.simulator', wires=XXX)


.. raw:: html

    <br/>

.. toctree::
   :maxdepth: 2
   :titlesonly:
   :hidden:

   installation
   support

.. toctree::
   :maxdepth: 2
   :caption: Usage
   :hidden:

   devices/simulator

.. toctree::
   :maxdepth: 1
   :caption: API
   :hidden:

   code
