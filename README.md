Snap package of the [Flat Remix GTK theme](https://github.com/daniruiz/flat-remix-gtk) by [daniruiz](https://github.com/daniruiz).

---

## Installing locally

Requires
* snapcraft (```snap install snapcraft```)
* multipass (```snap install multipass```)

```sh
git clone https://github.com/jollygoose/flat-remix-gtk-snap
cd flat-remix-gtk-snap

snapcraft

# where CURRENT is the latest version of flat-remix-gtk
snap install flat-remix-gtk_CURRENT_all.snap --dangerous
```

### Applying the theme

In order to work, the snap package needs to have a '[plug](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)' 
available for either gtk-3-themes or gtk-2-themes.

To findout which apps are able to use the theme, you can run:

```bash
# gtk2
for plug in $(snap connections | grep gtk-common-themes:gtk-2-themes | awk '{print $2}'); do echo ${plug}; done

# gtk3
for plug in $(snap connections | grep gtk-common-themes:gtk-3-themes | awk '{print $2}'); do echo ${plug}; done
```

To apply to a single application

```bash
# gtk2
sudo snap connect NAME_OF_YOUR_APP:gtk-2-themes flat-remix-gtk:gtk-2-themes

# gtk3
sudo snap connect NAME_OF_YOUR_APP:gtk-3-themes flat-remix-gtk:gtk-3-themes
```

To apply to all gtk2 or gtk3 applications (thanks to @flexiondotorg for the handy loop)

```bash
# gtk2
for plug in $(snap connections | grep gtk-common-themes:gtk-2-themes | awk '{print $2}'); do sudo snap connect ${plug} flat-remix-theme:gtk-2-themes; done

# gtk3
for plug in $(snap connections | grep gtk-common-themes:gtk-3-themes | awk '{print $2}'); do sudo snap connect ${plug} flat-remix-theme:gtk-3-themes; done
```

*NOTE*: Some apps like the Ubuntu Snap Store requiring logging out and back in to load the changes.