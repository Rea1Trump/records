# 2023-02-20
---


> This is a modified manual of dwl.

# DWL(1)                  FreeBSD General Commands Manual                 DWL(1)

# NAME
     dwl – dwm for Wayland

# SYNOPSIS
     dwl [-v] [-s startup command]

# DESCRIPTION
     dwl is a Wayland compositor based on wlroots.  It is intended to fill the
     same space in the Wayland world that dwm does for X11.

     When given the -v option, dwl writes its name and version to standard
     error and exits unsuccessfully.

     When given the -s option, dwl starts a shell process running command when
     starting.  When stopping, it sends SIGTERM to the child process and waits
     for it to exit.

     Users are encouraged to customize dwl by editing the sources, in
     particular config.h.  The default key bindings are as follows:
           Mod-[1-9]             Show only all windows with a tag.
           Mod-Ctrl-[1-9]        Show all windows with a tag.
           Mod-Shift-[1-9]       Move window to a single tag.
           Mod-Ctrl-Shift-[1-9]  Toggle tag for window.
           Mod-Space             Spawn rofi.
           Mod-Shift-Return      Spawn foot.
           Mod-[jk]              Move focus down/up the stack.
           Mod-[id]              Increase/decrease number of windows in master
                                 area.
           Mod-[hl]              Decrease/increase master area.
           Mod-Return            Move window on top of stack or switch top of
                                 stack with second window.
           Mod-Tab               Show only all windows with previous tag.
           Mod-q                 Close window.


           Mod-t                 Switch to tabbed layout.
           Mod-e                 Switch to floating layout.
           Mod-w                 Switch to monocle layout.

           Mod-Space             Switch to previous layout.

           Mod-Shift-Space       Toggle floating state of window.
           Mod-f                 Toggle fullscreen state of window.
           Mod-0                 Show all windows.
           Mod-Shift-0           Set all tags for window.
           Mod-,                 Move focus to previous monitor.
           Mod-.                 Move focus to next monitor.
           Mod-Shift-,           Move window to previous monitor.
           Mod-Shift-.           Move window to next monitor.
           Mod-Shift-q           Quit dwl.
     These might differ depending on your keyboard layout.

# ENVIRONMENT
     These environment variables are used by dwl:

     XDG_RUNTIME_DIR  A directory where temporary user files, such as the
                      Wayland socket, are stored.

     XDG_CONFIG_DIR   A directory containung configuration of various programs
                      and libraries, including libxkbcommon.

     DISPLAY, WAYLAND_DISPLAY, WAYLAND_SOCKET
                      Tell how to connect to an underlying X11 or Wayland
                      server.

     WLR_*            Various variables specific to wlroots.

     XKB_*, XLOCALEDIR, XCOMPOSEFILE
                      Various variables specific to libxkbcommon.

     XCURSOR_PATH     List of directories to search for XCursor themes in.

     HOME             A directory where there are always dear files there for
                      you.  Waiting for you to clean them up.

     These are set by dwl:

     WAYLAND_DISPLAY  Tell how to connect to dwl.

     DISPLAY          If using Xwayland, tell how to connect to the Xwayland
                      server.

# EXAMPLES
     Start dwl with s6 in the background:
           dwl -s 's6-svscan <&-'

# SEE ALSO
     foot(1), bemenu(1), dwm(1), xkeyboard-config(7)

# CAVEATS
     The child process's standard input is connected with a pipe to dwl.  If
     the child process neither reads from the pipe nor closes its standard
     input, dwl will freeze after a while due to it blocking when writing to
     the full pipe buffer.

# BUGS
     All of them.
