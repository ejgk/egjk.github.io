Similar to https://moritzmolch.com/932 but applied for a newer version.

https://ankiweb.net/shared/info/24411424 works as well, however it only allows
binding the existing functionalities and disallow things like

    lambda: self._getTypedAnswer() if self.state == "question"
        else self._answerCard(4)

which shows the answer if the question is shown, otherwise answers
with option 4. (to make the add-on support the setting above, change the
main Python file of the add-on)

First it's necessary to find the installation directory. On Linux it can
usually be found by `which anki` and `cat $(which anki)`.

It may be in `/usr/share/anki`.

Go to `aqt/reviewer.py` and edit the `_shortcutKeys` function.
Note that there must be no conflict (you can delete
the existing default shortcuts)

Also: avoid conflict with `setShortcut` calls in `aqt/forms/main.py`
and `globalShortcuts` in `setupKeys` function in `aqt/main.py`.
