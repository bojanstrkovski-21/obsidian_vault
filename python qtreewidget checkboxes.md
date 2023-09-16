
[](https://stackoverflow.com/posts/31342228/timeline)

I am attempting to create a tree widget that will essentially allow the user to view various breakdowns of data and have the option to delete certain items. In order to do this I want to have check boxes associated with each top level item and each child so the user can select which top level items (and thus all the children of that top level item) to delete. Or which specific children to delete. To give you a better idea I've created an example where [x] represents a checked check box and [ ] represents an empty checkbox:

```python
>Beverages Allowed in Stadium [ ]
    Soda                      [ ]
    Water                     [ ]
    Tea                       [ ]
    Spirits                   [X]
    Ale                       [ ]

>Tickets                      [X]
    Row A                     [X]
    Row B                     [X]
    Row C                     [X]
    Lawn                      [X]
```

Any suggestions how to implement this? I don't know if it makes a difference as far as difficulty, but i have allocated a separate column for the check box.

- [python](https://stackoverflow.com/questions/tagged/python "show questions tagged 'python'")
- [checkbox](https://stackoverflow.com/questions/tagged/checkbox "show questions tagged 'checkbox'")
- [pyqt](https://stackoverflow.com/questions/tagged/pyqt "show questions tagged 'pyqt'")
- [qtreeview](https://stackoverflow.com/questions/tagged/qtreeview "show questions tagged 'qtreeview'")
- [qtreewidgetitem](https://stackoverflow.com/questions/tagged/qtreewidgetitem "show questions tagged 'qtreewidgetitem'")

[Share](https://stackoverflow.com/q/31342228 "Short permalink to this question")

[Improve this question](https://stackoverflow.com/posts/31342228/edit)

Follow

[edited Jul 10, 2015 at 14:05](https://stackoverflow.com/posts/31342228/revisions "show all edits to this post")

[

![Andy's user avatar](https://i.stack.imgur.com/jFsyb.png?s=64&g=1)

](https://stackoverflow.com/users/189134/andy)

[Andy](https://stackoverflow.com/users/189134/andy)♦

49.1k6060 gold badges167167 silver badges233233 bronze badges

asked Jul 10, 2015 at 13:38

[

![sudobangbang's user avatar](https://www.gravatar.com/avatar/ad8e7219007534d01b31a4fe7a94ed6c?s=64&d=identicon&r=PG&f=y&so-version=2)

](https://stackoverflow.com/users/3119546/sudobangbang)

[sudobangbang](https://stackoverflow.com/users/3119546/sudobangbang)

1,4061010 gold badges3232 silver badges5555 bronze badges

[Add a comment](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal# "Use comments to ask for more information or suggest improvements. Avoid answering questions in comments.")

## 4 Answers

Sorted by:

23

[](https://stackoverflow.com/posts/31342831/timeline)

In addition to the [answer](https://stackoverflow.com/a/31342537/189134) you provided, you can simplify your logic by using the [`ItemIsTristate`](http://pyqt.sourceforge.net/Docs/PyQt4/qt.html#ItemFlag-enum) flag on the parent elements.

```python
from PyQt4.QtCore import * 
from PyQt4.QtGui import * 
import sys

def main(): 
    app     = QApplication (sys.argv)
    tree    = QTreeWidget ()
    headerItem  = QTreeWidgetItem()
    item    = QTreeWidgetItem()

    for i in xrange(3):
        parent = QTreeWidgetItem(tree)
        parent.setText(0, "Parent {}".format(i))
        parent.setFlags(parent.flags() | Qt.ItemIsTristate | Qt.ItemIsUserCheckable)
        for x in xrange(5):
            child = QTreeWidgetItem(parent)
            child.setFlags(child.flags() | Qt.ItemIsUserCheckable)
            child.setText(0, "Child {}".format(x))
            child.setCheckState(0, Qt.Unchecked)
    tree.show() 
    sys.exit(app.exec_())

if __name__ == '__main__':
    main()
```

---

The three most important lines of code are:

```python
parent.setFlags(parent.flags() | Qt.ItemIsTristate | Qt.ItemIsUserCheckable)
```

This one sets up the parent element to be a three state check box.

```python
child.setFlags(child.flags() | Qt.ItemIsUserCheckable)
child.setCheckState(0, Qt.Unchecked)
```

These set up the child to be selectable and set the default to unchecked. If the child's checkbox isn't given a state, the checkbox element does not appear.

---

The code above builds a very simple tree.

![Simple Tree](https://i.stack.imgur.com/lj4ZF.png)

However, if I check a check box on the parent element, all the children are automatically selected:

![Parent Selected](https://i.stack.imgur.com/T5cbU.png)

If, I wish to unselect a single child, the parent enters the partially selected (Tri-State):

![TriState](https://i.stack.imgur.com/lJ0uK.png)

If all children are unselected, the parent is automatically unselected. If the parent is unselected, all children are automatically unselected as well.

[Share](https://stackoverflow.com/a/31342831 "Short permalink to this answer")

[Improve this answer](https://stackoverflow.com/posts/31342831/edit)

Follow

[edited May 23, 2017 at 11:54](https://stackoverflow.com/posts/31342831/revisions "show all edits to this post")

[

![Community's user avatar](https://www.gravatar.com/avatar/a007be5a61f6aa8f3e85ae2fc18dd66e?s=64&d=identicon&r=PG)

](https://stackoverflow.com/users/-1/community)

[Community](https://stackoverflow.com/users/-1/community)Bot

111 silver badge

answered Jul 10, 2015 at 14:04

[

![Andy's user avatar](https://i.stack.imgur.com/jFsyb.png?s=64&g=1)

](https://stackoverflow.com/users/189134/andy)

[Andy](https://stackoverflow.com/users/189134/andy)♦

49.1k6060 gold badges167167 silver badges233233 bronze badges

- This seems to work well, however instead of getting a nice filled box, my boxes appear to just either have a horizontal dash through them or if i click it a second time it shows a check mark. Is this normal? Is there anyway I can either disable the solid dash or fix it to fill the entire box as in your example?
    
    – [sudobangbang](https://stackoverflow.com/users/3119546/sudobangbang "1,406 reputation")
    
    [Jul 10, 2015 at 14:28](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal#comment50670644_31342831)
    
- 1
    
    That is dependent on your OS and widget style. There is more documentation on that [here](http://pyqt.sourceforge.net/Docs/PyQt4/qstyle.html), but is probably out of scope for this specific question.
    
    – [Andy](https://stackoverflow.com/users/189134/andy "49,135 reputation") ♦
    
    [Jul 10, 2015 at 14:32](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal#comment50670802_31342831)
    
- Okay, Is there a way to just disable the whole fill and make it so it only has the check option?
    
    – [sudobangbang](https://stackoverflow.com/users/3119546/sudobangbang "1,406 reputation")
    
    [Jul 10, 2015 at 14:58](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal#comment50671958_31342831)
    
- 1
    
    If you only want it to be a binary checkbox and not a Tristate box, remove the `Qt.ItemIsTristate` flag and add `parent.setCheckState(0, Qt.Unchecked)` (again, a checkbox state is required for it to show). This will add the check box to the parent. You lose the automatic selection and deselection of children by removing the Tristate flag though.
    
    – [Andy](https://stackoverflow.com/users/189134/andy "49,135 reputation") ♦
    
    [Jul 10, 2015 at 15:02](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal#comment50672105_31342831)
    

- is there any easy way to return a list of all the boxes that are currently checked? Aside from writing a loop that iterates through the entire tree checking every items checkstate?
    
    – [sudobangbang](https://stackoverflow.com/users/3119546/sudobangbang "1,406 reputation")
    
    [Jul 16, 2015 at 14:35](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal#comment50881466_31342831)
    

[Show **1** more comment](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal# "Expand to show all comments on this post")

8

[](https://stackoverflow.com/posts/57820072/timeline)

I ported @andy's awesome example to PyQt5:

```python
from PyQt5 import QtWidgets
from PyQt5 import QtCore
from PyQt5 import QtGui
from PyQt5.Qt import Qt
import sys

def main(): 
    app     = QtWidgets.QApplication(sys.argv)
    tree    = QtWidgets.QTreeWidget()
    headerItem  = QtWidgets.QTreeWidgetItem()
    item    = QtWidgets.QTreeWidgetItem()

    for i in range(3):
        parent = QtWidgets.QTreeWidgetItem(tree)
        parent.setText(0, "Parent {}".format(i))
        parent.setFlags(parent.flags() | Qt.ItemIsTristate | Qt.ItemIsUserCheckable)
        for x in range(5):
            child = QtWidgets.QTreeWidgetItem(parent)
            child.setFlags(child.flags() | Qt.ItemIsUserCheckable)
            child.setText(0, "Child {}".format(x))
            child.setCheckState(0, Qt.Unchecked)
    tree.show() 
    sys.exit(app.exec_())

if __name__ == '__main__':
    main()
```

![screenshot](https://i.stack.imgur.com/RrAOX.png)

[Share](https://stackoverflow.com/a/57820072 "Short permalink to this answer")

[Improve this answer](https://stackoverflow.com/posts/57820072/edit)

Follow

answered Sep 6, 2019 at 10:14

[

![pklaus's user avatar](https://www.gravatar.com/avatar/241124474e6117343e0394108aefbc3c?s=64&d=identicon&r=PG)

](https://stackoverflow.com/users/183995/pklaus)

[pklaus](https://stackoverflow.com/users/183995/pklaus)

64788 silver badges2121 bronze badges

[Add a comment](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal# "Use comments to ask for more information or suggest improvements. Avoid comments like “+1” or “thanks”.")

4

[](https://stackoverflow.com/posts/31342537/timeline)

`QTreeWidgetItem` actually has a built in check box that you can use fairly easily.

**For example:**

```python
item = QTreeWidgetItem(self.treeWidget)

item.setCheckState(0, QtCore.Qt.Unchecked)
```

[Share](https://stackoverflow.com/a/31342537 "Short permalink to this answer")

[Improve this answer](https://stackoverflow.com/posts/31342537/edit)

Follow

[edited Nov 23, 2017 at 9:46](https://stackoverflow.com/posts/31342537/revisions "show all edits to this post")

[

![python_fan's user avatar](https://www.gravatar.com/avatar/cca0c24e205517d2609236262f745c98?s=64&d=identicon&r=PG&f=y&so-version=2)

](https://stackoverflow.com/users/8872842/python-fan)

[python_fan](https://stackoverflow.com/users/8872842/python-fan)

11322 silver badges1515 bronze badges

answered Jul 10, 2015 at 13:52

[

![sudobangbang's user avatar](https://www.gravatar.com/avatar/ad8e7219007534d01b31a4fe7a94ed6c?s=64&d=identicon&r=PG&f=y&so-version=2)

](https://stackoverflow.com/users/3119546/sudobangbang)

[sudobangbang](https://stackoverflow.com/users/3119546/sudobangbang)

1,4061010 gold badges3232 silver badges5555 bronze badges

- True, but your solution doesn't include the the hierarchical structure where the parent has a tristate that corresponds to its children's state. The example listed above does.
    
    – [MaVCArt](https://stackoverflow.com/users/5457552/mavcart "755 reputation")
    
    [Sep 2, 2016 at 14:52](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal#comment65924342_31342537)
    

[Add a comment](https://stackoverflow.com/questions/31342228/pyqt-tree-widget-adding-check-boxes-for-dynamic-removal# "Use comments to ask for more information or suggest improvements. Avoid comments like “+1” or “thanks”.")

2

[](https://stackoverflow.com/posts/41419412/timeline)

This is not an answer to your question, rather how to use the checkboxes once you have them. I used the example above from the answer marked as correct. It worked, but then when I tried to find how to know which checkboxes were marked, and I had a lot of issues. After a lot of searching I found a solution that worked for me, as I see there is no a lot of doc, so I want to leave a record for the future. Just to mention I used several solutions as invisibleRootItem in order to find the children of the parent but that didn't work.

I ended up using the class QTreeWidgetItemIterator with a flag QtGui.QTreeWidgetItemIterator.Checked in order to retreive the text of the checkboxes marked, and with that, I can continue working.

```python
def vrfs_selected(self):
    iterator = QtGui.QTreeWidgetItemIterator(self.tree, QtGui.QTreeWidgetItemIterator.Checked)
    while iterator.value():
        item = iterator.value()
        print (item.text(0))    
        iterator += 1
```

the link to the documentation [http://ftp.ics.uci.edu/pub/centos0/ics-custom-build/BUILD/PyQt-x11-gpl-4.7.2/doc/html/qtreewidgetitemiterator.html](http://ftp.ics.uci.edu/pub/centos0/ics-custom-build/BUILD/PyQt-x11-gpl-4.7.2/doc/html/qtreewidgetitemiterator.html) and an example [https://riverbankcomputing.com/pipermail/pyqt/2014-May/034315.html](https://riverbankcomputing.com/pipermail/pyqt/2014-May/034315.html)

[](https://stackoverflow.com/a/41419412 "Short permalink to this answer")