Telemetry: Recording Data on the Robot
======================================

`Telemetry <https://en.wikipedia.org/wiki/Telemetry>`__ (literally "measuring remotely") is the process of recording and sending real-time data about the performance of your robot to a real-time readout or log file.  Recording and viewing telemetry data is a crucial part of the engineering process - accurate telemetry data helps you tune your robot to perform optimally, and is indispensable for debugging your robot when it fails to perform as expected.

Recording Data from Robot Code
------------------------------

.. note:: On-robot logging of telemetry data is not yet fully supported by WPILib (it is currently scheduled for a mid-season update).  In the mean-time, teams can record their telemetry data on their driver station computer with :ref:`Shuffleboard recordings <docs/software/dashboards/shuffleboard/getting-started/shuffleboard-recording:Recording and Playback>`.

WPILib supports several different ways to record and report telemetry data on the driver station.

At the most basic level, the :ref:`Riolog <docs/software/vscode-overview/viewing-console-output:Viewing Console Output>` provides support for viewing print statements from robot code.  This is useful for on-the-fly debugging of problematic code, but does not scale as console interfaces are not suitable for rich data streams.

WPILib supports several :ref:`dashboards <docs/software/dashboards/index:Dashboards>` that allow users to more easily send rich telemetry data to the driver-station computer.  All WPILib dashboards communicate with the :ref:`NetworkTables <docs/software/networktables/networktables-intro:What is NetworkTables>` protocol, and so they are *to some degree* interoperable (telemetry logged with one dashboard will be visible on the others, but the specific widgets/formatting will generally not be compatible).  NetworkTables (and thus WPILib all dashboards) currently support the following data types:

* ``boolean``
* ``boolean[]``
* ``double``
* ``double[]``
* ``string``
* ``string[]``
* ``byte[]``

Telemetry data can be sent to a WPILib dashboard using an associated WPILib method (for more details, see the documentation for the individual dashboard in question), or by :ref:`directly publishing to NetworkTables <docs/software/networktables/networktables-intro:Writing a simple NetworkTables program>`.

While NetworkTables does not yet support serialization of complex data types (this is tentatively scheduled for 2023), *mutable* types from user code can be easily extended to interface directly with WPILib dashboards via the ``Sendable`` interface, whose usage is described in the next article.