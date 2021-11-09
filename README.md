Snap package of the [Flat Remix GTK theme](https://github.com/daniruiz/flat-remix-gtk) by [@daniruiz](https://github.com/daniruiz).


[![flat-remix-gtk](https://snapcraft.io/flat-remix-gtk/badge.svg)](https://snapcraft.io/flat-remix-gtk)


[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/flat-remix-gtk)

---

## Attributions

All credit goes to the developers of the Flat Remix GTK project.
https://github.com/daniruiz/flat-remix-gtk

## Building locally

### Requirements

* [snapcraft](https://snapcraft.io/snapcraft) (```snap install snapcraft --classic```)
* [multipass](https://snapcraft.io/multipass) (```snap install multipass```)

### Build

```sh
git clone https://github.com/jollygoose/flat-remix-gtk-snap
cd flat-remix-gtk-snap

snapcraft clean && snapcraft

# where [current-version] is the latest version/release of in the in snapcraft.yaml file.
# The --dangerous is used since this snap was built locally and does not originate from the snap store
snap install flat-remix-gtk_[current-version]_all.snap --dangerous
```

## Applying the theme

In order to work, the snap package needs to have a '[plug](https://ubuntu.com/blog/a-guide-to-snap-permissions-and-interfaces)' 
available for either 'gtk-3-themes' or 'gtk-2-themes'.

To apply to a single application:

```bash
# gtk2
sudo snap connect [snap-you-want-to-theme]:gtk-2-themes flat-remix-gtk:gtk-2-themes

# gtk3
sudo snap connect [snap-you-want-to-theme]:gtk-3-themes flat-remix-gtk:gtk-3-themes
```

To apply the theme to all gtk2 or gtk3 applications (thanks to @flexiondotorg for the handy loop):

```bash
# gtk2
for plug in $(snap connections | grep gtk-common-themes:gtk-2-themes | awk '{print $2}'); do sudo snap connect ${plug} flat-remix-gtk:gtk-2-themes; done

# gtk3
for plug in $(snap connections | grep gtk-common-themes:gtk-3-themes | awk '{print $2}'); do sudo snap connect ${plug} flat-remix-gtk:gtk-3-themes; done
```

*NOTE*: Some apps like the Ubuntu Snap Store may require logging out, and back in to load the changes.