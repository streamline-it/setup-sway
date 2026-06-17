Role Name
=========

setup-sway

Requirements
------------

None.

Role Variables
--------------

#
# defaults variables
#
-
# defaults file for setup-sway

# For the variable below, the opiniated default for super_key is set
# for the windows key "Mod4" instead of the ALT key.
setup_sway_users:
  - username: 
    super_key: "Mod4"
    wallpaper:

# following variable holds the name of the doc file listing key
# bindings
setup_sway_key_binding_filename: sway-key-bindings.txt

# custom documentation directory for the key binding doc
setup_sway_doc_filepath: /usr/local/share/doc/ro_docs

# sway config mods mostly keybindings.
setup_sway_config_mods:
  - assign [class="terminal"] 2
  - bindsym $mod+n workspace 4; exec "thunar"
  - bindsym $mod+t workspace 4; exec "mousepad"
  - bindsym $mod+SHIFT+b workspace 3; exec "firefox"
  - bindsym $mod+o workspace 5; exec "libreoffice"
  - bindsym $mod+p workspace 5; exec "lowriter"
  - bindsym $mod+q workspace 5; exec "localc"
  - exec --no-startup-id xwallpaper --zoom {{ setup_sway_wallpaper_directory }}/{{ item['wallpaper'] }}

#
# vars/main
#
# vars file for setup-sway

# wallpaper filenames
setup_sway_wallpaper_files:
  - 7drops.jpg
  - FreeBSD_Delight.jpg
  - hot_enuf.jpg
  - metal.jpg

#
# vars>FreeBSD.yml
#
# packages needed for sway
setup_sway_pkgs:
  - sway
  - swayidle
  - swaylock-effects
  - alacritty
  - dmenu-wayland
  - dmenu
  - dbus

# user's config directory for sway
setup_sway_user_config_path: ".config/sway"

# default sway config file to setup for the user
setup_sway_default_config_filepath: /usr/local/etc/sway/config

# root group for FreeBSD
setup_sway_root_group: wheel

# wallpaper directory
setup_sway_wallpaper_directory: /usr/local/share/wallpaper

Dependencies
------------

None
Example Playbook
----------------


    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

Rich O'Hara
