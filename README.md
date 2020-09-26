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
deps="dep1 dep2 dep3 dep4"
author="me"
type=main
sources=('wget:save_to_filename:http://link/to/something')
sha256sums=('sha256sum or SKIP')
unpack() {
some commands for unpacking source files
}
package() {
$pkgdir is / (like install -m 755 file $pkgdir/usr/bin/$name)
$srcdir is where ${sources[@]} save
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
package : version-release dep1 dep2 dep3 dep4@Description
package2 : version-release nothing@Description
```
