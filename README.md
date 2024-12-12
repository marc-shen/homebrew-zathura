# Zathura

Homebrew formulae to install zathura and plugins on Mac OS X

## Installation steps

### Tap the repository
```
brew tap marc-shen/zathura
```

### Install zathura
```
brew install zathura
```

With Synctex:
```
brew install zathura --with-synctex
```

### Install and link one of the two plugins

For poppler:
```
brew install zathura-pdf-poppler
mkdir -p $(brew --prefix zathura)/lib/zathura
ln -s $(brew --prefix zathura-pdf-poppler)/libpdf-poppler.dylib $(brew --prefix zathura)/lib/zathura/libpdf-poppler.dylib
```

For mupdf:
```
brew install zathura-pdf-mupdf
mkdir -p $(brew --prefix zathura)/lib/zathura
ln -s $(brew --prefix zathura-pdf-mupdf)/libpdf-mupdf.dylib $(brew --prefix zathura)/lib/zathura/libpdf-mupdf.dylib
```

### OSX_native_integration

The OSX native integration (dock, window manager) has been added to the develop branch of zathura.
You can install it by
```
# unlink installed zathura and girara
brew unlink girara
brew unlink zathura

# install HEAD
brew install girara --HEAD
brew install zathura --HEAD
mkdir -p $(brew --prefix zathura)/lib/zathura
ln -s $(brew --prefix zathura-pdf-poppler)/libpdf-poppler.dylib $(brew --prefix zathura)/lib/zathura/libpdf-poppler.dylib
```

### Copying to clipboard
Add the following to your `~/.config/zathura/zathurarc`:
```
set selection-clipboard clipboard
```
Thanks to [geigi](https://github.com/geigi) (see [#5](https://github.com/zegervdv/homebrew-zathura/issues/5))

### Operation not supported error

If you are seeing errors like this:
```
error: Can not copy to temporary file: Operation not supported
```

Try using an absolute path to the document:
```
$ zathura document.pdf
error: Can not copy to temporary file: Operation not supported
# Try:
$ zathura /path/to/document.pdf

```

## Known Issues
Currently plugins are installed in the zathura folder, which means that uninstalling
a plugin does not work.
