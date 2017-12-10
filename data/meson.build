install_data ('init/lightdm.conf',
              install_dir: join_paths (sysconfdir, 'init'))

install_data ([ 'lightdm.conf', 'users.conf', 'keys.conf' ],
              install_dir: join_paths (sysconfdir, 'lightdm'))

install_data ('org.freedesktop.DisplayManager.conf',
              install_dir: join_paths (sysconfdir, 'dbus-1', 'system.d'))

install_data ([ 'bash-completion/dm-tool', 'bash-completion/lightdm' ],
              install_dir: join_paths (datadir, 'bash-completion', 'completions'))

install_data ([ 'pam/lightdm', 'pam/lightdm-autologin', 'pam/lightdm-greeter' ],
              install_dir: join_paths (sysconfdir, 'pam.d') )

conf_data = configuration_data ()
conf_data.set ('libexecdir', libexecdir)
configure_file (input: 'apparmor/lightdm-guest-session.in',
                output: 'lightdm-guest-session',
                configuration: conf_data,
                install_dir: join_paths (sysconfdir, 'apparmor.d') )

install_data ([ 'apparmor/abstractions/lightdm', 'apparmor/abstractions/lightdm_chromium-browser' ],
              install_dir: join_paths (sysconfdir, 'apparmor.d', 'abstractions') )

install_man ([ 'dm-tool.1', 'lightdm.1' ])
