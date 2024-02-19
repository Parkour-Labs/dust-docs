Currently it's very involved to successfully install `dust`, as it would
require you to have `cargo` installed with the required targets. You will also
need to be familiar with using git-submodules for now, as we currently have not
figured out how to ship dart packages with native code to `pub.dev`.

## Step 1. Install Cargo

Follow the instructions on [Cargo's website](https://doc.rust-lang.org/cargo/getting-started/installation.html),
and you should be good to go!

## Step 2. Add targets

```sh
# for targets relating to android
rustup target add aarch64-linux-android armv7-linux-androideabi x86_64-linux-android i686-linux-android
# for targets relating to macos
rustup target add aarch64-apple-darwin x86_64-apple-darwin
# for targets relating to ios
rustup target add aarch64-apple-ios aarch64-apple-ios-sim x86_64-apple-ios
# for targets relating to windows
rustup target add x86_64-pc-windows-msvc
# for targets relating to windows on arm
rustup target add aarch64-pc-windows-msvc
```

## Step 3. Add submodules

Create a packages folder under your project root directory. We are going to
pull down dust to a subfolder under the packages folder. You can also put dust
under the root folder of your project. It's up to you.

```
├── lib
└── packages/
    └── dust/ # we are going to put dust here!
```

`cd` into the `packages` directory, and then run:

```sh
git submodule add https://github.com/Parkour-Labs/dust.git
```

Now the dust git repository will be added to your project as a git submodule.
Note that you may face a lot of confusions if this is the first time that you
are working with a git submodule. Here are a few tips:

If you want to remove a submodule, do not delete directly. Instead, run:

```sh
git rm -rf YOUR_MODULE_PATH
```

When you want to clone down the repository on a new machine, run the following
command:

```sh
git clone --recursive-submodules YOUR_REPOSITORY_GIT_URL
```

If you typed too quickly and forgot to do the recursive cloning, then run this
git command:

```sh
git submodule update --init --recursive
```

Other than that, `git` submodules work very-much like a git repository.

### Step 3. Add to `dust` to `pubspec.yaml`

In your `pubspec.yaml`, add `dust` and `dust_generator` as follows:

```yaml
dependencies:
  # other dependencies
  dust:
    path: packages/dust/

dev_dependencies:
  # other dev dependencies
  dust_generator:
    path: packages/dust/generator/
```

### Step 4. Add other optional packages

Optionally, you may also want to add the following packages:

- `flutter_hooks`, as we provide some hook apis and it can be handy to use;
- `path`: utilities for dealing with path on various systems;
- `path_provider`: utilities for reading some special paths for your
  application. `dust` needs to know where to put its database file.
