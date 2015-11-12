### 5. Windows Development Example

In order to get started developing for Pyblish on the Windows platform, let's set-up your environment.

> Much of this also applies to other platforms.

You will need:

1. Git
1. Python (2.7)
1. Pyblish
 
If you are interested in working with the UI, then you will also need PyQt5.

##### 5.1 PyQt

Assuming you already have Git and Python installed on your local machine, let's start with PyQt.

```bash
# Open up a terminal and run this.
mkdir pyblishdev
cd pyblishdev
git clone https://github.com/pyqt/python-qt.git
set PYTHONPATH=%CD%\python-qt;%PYTHONPATH%
python -c "import util;util.createqtconf()"
```

Now let's test the installation to make sure all is well.

```python
# Open up Python and run this.
import sys
from PyQt5 import QtWidgets
app = QtWidgets.QApplication(sys.argv)
button = QtWidgets.QPushButton("Hello")
button.setFixedSize(400, 400)
button.show()
app.exec_()
```

##### 5.2 Pyblish

The exact repositories to clone depends on which areas you are interested in developing for, but here are the basics.

```bash
# Required
git clone https://github.com/pyblish/pyblish

# For UI development
git clone https://github.com/pyblish/pyblish-qml
git clone https://github.com/pyblish/pyblish-rpc

# To integrate with a new host
git clone https://github.com/pyblish/pyblish-integration

# To integrate with existing host
git clone https://github.com/pyblish/pyblish-maya
git clone https://github.com/pyblish/pyblish-nuke
git clone https://github.com/pyblish/pyblish-houdini
git clone https://github.com/pyblish/pyblish-hiero
git clone https://github.com/pyblish/pyblish-modo

# To be ready for anything
# ALL OF THE ABOVE
```

Each of these repositories are set-up in the same way; at the root level there is a Python package. So what we need to do is somehow expose this package onto your PYTHONPATH.

How you choose to do that is not important, but here are some ideas.

1. Append the absolute path to each repository to your PYTHONPATH
2. Create a "junction" to each Python package within each repository in some directory on your PYTHONPATH.
 