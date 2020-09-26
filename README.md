# aupkg
Simple linux package manager.

## build file structure for `aupkg makepkg`
```
name=pkgname
ver=1
rel=1
arch="x86_64"
desc='Description.'
license="MIT"
deps="dep1 dep2 dep3 dep4" # If package has no dependencies, deps="nothing"
author="me"
type=main
sources=('wget:save_to_filename:http://link/to/something')
sha256sums=('sha256sum or SKIP')
unpack() {
# some commands for unpacking source files
msg "Unpacking..."
}
build() {
# some commands for compiling source files
msg "Building..."
}
package() {
# $pkgdir is / (like install -m 755 file $pkgdir/usr/bin/$name)
# $srcdir is where ${sources[@]} save
msg "Installing..."
}
```

## Database structure for server
/package
```
package_name.tar
second_package_name.tar
```

/package/.DB
```
package : version-release dep1 dep2 dep3 dep4 @ Description
package2 : version-release nothing @ Description
```

## Exit codes:
1 - The script is not executed as root \
2 - Some files not found (installation) \
3 - Some dependencies isn't installed \
4 - Some variables from `build` file not exists \
5 - Some files of `$pkgname` is exists in filesystem \
6 - Unknown compression method \
7 - Invalid arguments \
8 - Package not installed \
9 - Folder for `makepkg` not exists \
10 - checksum error \
11 - Removing `$dep` breaks `$pkgname` \
12 - Removing `$dep` in `$pkgname` breaks some other packages \
13 - Package `$pkgname` not found \
14 - Database file not found \
15 - Failed to fetch database file \
16 - Failed to install dependencies \
17 - Something occurs while upgrade
