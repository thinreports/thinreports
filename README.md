<div align="center">
  <h1>
    <img alt="Thinreports" src="https://raw.githubusercontent.com/thinreports/thinreports/main/thinreports.png" width="80"/>
    <br/>
    Thinreports
  </h1>
  <p>A PDF generation tools for Ruby, with design tool for editing templates.</p>
</div>

## Thinreports

Thinreports is a PDF generation tool that provides [Thinreports Editor](https://github.com/thinreports/thinreports-editor), a design tool for editing templates, and [Thinreports Generator](https://github.com/thinreports/thinreports-generator), a Ruby library for generating PDFs.

## Getting Started

Thinreports allows you to create PDF layouts using the Thinreports Editor, and then load the created template files with Thinreports Generator to generate PDFs by dynamically embedding values and changing shapes and layouts.

### Two Available Formats

Currently, Thinreports supports two types of template formats. These are called Basic Format and Section Format, respectively.

The basic functionality of both formats is the same, but Section Format is more functional, expressive, and modern. Also, because of the different design philosophy, the tools and APIs used in each format are different.

### Basic Format

Basic Format is a traditional and stable format in which shapes, text, etc. are placed on a fixed size canvas and a PDF is generated.

- [Installation](https://github.com/thinreports/thinreports/blob/main/getting-started/basic-format.md#installation)
- [Quick Start](https://github.com/thinreports/thinreports/blob/main/getting-started/basic-format.md#quick-start)
- [API Reference](https://github.com/thinreports/thinreports-generator/blob/master/README.md#usage)
- [Examples](https://github.com/thinreports/thinreports-examples)
- [Rails Application Example](https://github.com/thinreports/thinreports-rails-example)

### Section Format

*Currently under development*

Section Format is a new template format that allows you to define a layout by dividing it into units called sections, and then freely combine them to generate a PDF.

- [Features](https://github.com/thinreports/thinreports/blob/main/getting-started/section-format.md#features)
- [Installation](https://github.com/thinreports/thinreports/blob/main/getting-started/section-format.md#installation)
- [Quick Start](https://github.com/thinreports/thinreports/blob/main/getting-started/section-format.md#quick-start)
- [Examples](https://github.com/thinreports/thinreports/blob/main/getting-started/section-format.md#examples)

## News

Please see [Announcements at the our GitHub Discussions](https://github.com/thinreports/thinreports/discussions/categories/announcement).

## Support

If you have questions about Thinreports, please feel free to ask them in [the our GitHub Discussions](https://github.com/thinreports/thinreports/discussions) forum.

## Contributing

Please see [Contributing to Thinreports](https://github.com/thinreports/thinreports/wiki/How-to%3A-Contributing-to-Thinreports).

## Code of Conduct

This project has adopted the [Contributor Covenant](https://github.com/thinreports/thinreports/blob/main/CODE_OF_CONDUCT.md). Unacceptable behavior can be reported to thinreports+conduct@gmail.com which is monitored by the core team.

## Development

[Releasing Thinreports](https://github.com/thinreports/thinreports/blob/main/development/RELEASING.md)
