Role Name
=========

setup-sway
This will setup the sway compositor for Wayland.  It includes ability to set wallpaper, setup default font for alacritty too.  It will setup default key bindings for sway to start a browser, mousepad, and thunar allong with Firefox in their own designated work spaces.  This role will also provide documentation for those keybindings to the user's home directory.

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
    terminal_font_size: 13

# following variable holds the name of the doc file listing key
# bindings
setup_sway_key_binding_filename: sway-key-bindings.txt

# custom documentation directory for the key binding doc
setup_sway_doc_filepath: /usr/local/share/doc/ro_docs

# alacritty config name
setup_sway_alacritty_filename: alacritty.toml

# set terminal for sway
setup_sway_terminal: alacritty

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

- name: setup sway
  hosts: node5.example.com
  become: true

  vars:

    setup_sway_users:
      - username: rich
        super_key: Mod4
        wallpaper: 7drops.jpg
        terminal_font_size: 13.0

  roles:

    - name: setup-sway

License
-------

BSD

Author Information
------------------

Rich O'Hara
