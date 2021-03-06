# OneEFormBrowser - OneLink E-Form Browser

OneEFormBrowser is a simple web browser using the same Microsoft IE7-based WebBrowser control used by Hyland OnBase* (pre-version 15) for displaying E-Forms in the thick client and the Unity client. OneEFormBrowser is also great for viewing other aging, cantankerous web pages.

If you've ever created e-forms you know what this means: finally, you can reliably develop, test, and maintain HTML E-Forms outside of OnBase without jumping through hoops (or as many).

If you use it to browse real websites, expect to get frequent formatting and script errors, but that's the whole point!

\* this project is not affiliated with Hyland Software.


## Keyboard Shortcuts

```
     Back: Alt + Left Arrow
  Forward: Alt + Right Arrow
 Edit Url: Alt + D
       Go: Enter; Alt + G
  Refresh: Alt + R
     Home: Alt + H
     Stop: Alt + S
    Watch: Alt + W
     Find: Ctrl + F
```

## Custom Home Page

Create a file called `home.html` and place it in the folder `resources` (same as `about.html`). It will be shown instead of the about page on start and when you use the Home button.

The file `home.html` is ignored by git.

## Live Reload

When the the Watch checkbox is checked and the textbox contains a valid local file path (network and UNC won't work), OneEFormBrowser will reload the browser window when any file changes in that folder or any of its sub-folders. 

## Keeping Everything Local

Odds are your E-Forms use external resources such as images, javascript files, and css loaded from a web server.

The easiest way to keep those resources on your local dev box without hassling with changing the references back-and-forth is to run a local web server and change the hostname to match the web server you reference. Then, modify your hosts file to redirect that name to your local web server. It's super easy with IIS (once you find your hosts file --try c:\windows\system32\drivers\etc\hosts -- and remember to start your editor As Administrator).

## Deploying and Synchronizing with OnBase

My git deployment workflow isn't very fancy, but it's mostly automated.

I push local changes to GitHub and on the server I run a script that pulls from GitHub (through a proxy) and copies runtime files as needed. This takes care of resource files but HTML files still need to get into OnBase.

I have a Unity script that automatically imports only the changed HTML files as new SYS HTML Files. It spits out a list of the changed files that I then have to manually set as the new E-form for each associated Document Type (because Hyland's API doesn't provide a way to update the E-form for a Doc Type).

## Known Issues

- Ability to change focus with the tab key is sometimes lost after loading a page from the address textbox. Clicking a control re-enables tab key. Navigating to new pages using links has no negative effect.

- Browser doesn't open pop-up windows itself, instead sending them to the system default browser.


## Trademarks

All product and company names are trademarks or registered trademarks of their respective holders. Use of them does not imply any affiliation with or endorsement by them or of them.

OnBase is a registered trademark of Hyland Software.

This open-source project is sponsored by [OneLink.net](http://www.onelink.net).


## License

- The MIT License is a permissive license that is short and to the point. It lets people do anything they want with the the code as long as they provide attribution back to OneLink and don’t hold OneLink liable.

- License text and attribution in LICENSE file in root of repository.

- Fixes and enhancements are appreciated and recommended.

- Those wishing to avoid attribution can contact OneLink for special excemptions.
