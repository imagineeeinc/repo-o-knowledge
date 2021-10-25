# The Rust Section

This section is for rust based knowledge

# Contents

- [Instalation on windows](#instalation-on-windows)
- [Rust On Bare Metal](#rust-on-bare-metal)

# Instalation on windows
[Based on this answer on stackoverflow (follow this for a more in depth beginer friendly approach)](https://stackoverflow.com/questions/21196525/rust-installation-on-windows/68835925#68835925)

Requirements:
- Basic knowledege of rust toolchain and gnu
- improvise where needed

1. Install [MSYS2](https://www.msys2.org/), make sure to remeber the instalation loacation and replace the '%msys2 instalation location%' with the instaltaion location when needed
2.  - Find the 'MSYS2 MSYS' shortcut in the start menu (or '%msys2 instalation location%\msys2_shell.cmd -msys'), Admin privileges required if instaled in Program folder or a place where the privileges is required
    - Run `pacman -Syu`
    - Run `pacman -Su`
3.  - Find the 'MSYS2 MinGW 64-bit' shortcut in the start menu (or '%msys2 instalation location%\msys64\msys2_shell.cmd -mingw64'), Admin privileges required if instaled in Program folder or a place where the privileges is required
    - Run `pacman -S mingw-w64-x86_64-toolchain`
      - If needed run `pacman -S --needed base-devel mingw-w64-x86_64-toolchain`
    - choose default installation and `y` when asking to install
    - Install cmake (optinal) `pacman -S --needed base-devel cmake`
4.  - Download the windows rust Installer from [here](https://www.rust-lang.org/tools/install)
    - Run `rustup-init.exe` (It is better to launch a console with cmd.exe and launch rustup-init.exe from there)
      - choose "Continue? (y/N)" by typing y and hitting the Enter key
      - choose "2) Customize installation" using the keyboard
      - paste or type the option:  `x86_64-pc-windows-gnu`
      - Press enter for the rest of the options
      - Finally type "1" as input in the console, then press Enter, to choose the option "1 to proceed" with the Current installation Options
5.  - create a file in `C:\Users\your-username-folder\.cargo\`
    - call it `config`
    - Full path: `C:\Users\your-username-folder\.cargo\config`
    - add these depending on what compiler you want to use:
      - Clang [Recomended] (faster, performent, less memory usage):
        ```
        [target.x86_64-pc-windows-gnu]
        linker = "D:\\Applications\\msys64\\mingw64\\bin\\clang++.exe"
        ar = "D:\\Applications\\msys64\\mingw64\\bin\\llvm-ar.exe"
        ```
      - GCC
        ```
        [target.x86_64-pc-windows-gnu]
        linker = "D:\\Applications\\msys64\\mingw64\\bin\\gcc.exe"
        ar = "D:\\Applications\\msys64\\mingw64\\bin\\ar.exe"
        ```
6.  - Adding these folders to your path
    - Right click on "My Computer" and select "properties"
    - Click on Advanced System Settings
    - In the Advanced tab, click on "Environment Variables"
    - under 'System variables' click on the PATH Variable and add the locations of your 'cargo\bin folder' and mingw64\bin folder, (plus msys64):
      - Cargo (Rust): `C:\Users\your-username-folder\.cargo\bin
      - mingw64: `%msys2 instalation location%\msys64`
      - msys2 (msys64): `%msys2 instalation location%`
7.  - Restart computer if needed
    - Run `cargo -v && rustc -v` to find the cargo and rustc version and to check if they are configured right
    - Run`rustc --print cfg` to check the toolchain is right
    - Make a test project to see if everything is compiling fine
      - Simple hello world:
        ```
        fn main() {
          println!("Hello World!");
        }
        ```

# Rust on bare metal

Writting programs and os that run on bare metal is my dream but its complex and information on it scarce or to complex for a mediocre JavaScript developer (like me). So, I compiled a list of links and information for developing for bare metal with rust (I chose rust because, rust is a beuatiful performant languge)

- [Embeded Graphics Libary](https://crates.io/crates/embedded-graphics)
- [How to write x86 bare-metal hello world in Rust (*by* Yushi Omote)](https://yushiomote.org/posts/baremetal)
- [UI on bare metal - How did Redox os do it?](https://www.reddit.com/r/rust/comments/fpr52q/how_did_redox_os_make_its_gui/)
- [Learn os dev with rassberypi and rust](https://github.com/rust-embedded/rust-raspberrypi-OS-tutorials)

