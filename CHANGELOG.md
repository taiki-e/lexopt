## 0.3.0 (unreleased)

The input iterator is now consumed when you create a `Parser`, instead of during parsing. This breaks certain clever code that inspects the state of the iterator, but the newly added unlimited lookahead may provide an alternative.

(If you don't know what this means then you don't have to worry.)

New:

- Add `RawArgs::as_slice()` for unlimited lookahead.
- `Parser` implements `Clone`, `Send`, and `Sync`. Its `Debug` output now shows the remaining arguments.

## 0.2.1 (2022-07-10)

New:

- Add `Parser::raw_args()` for collecting raw unparsed arguments. ([#12](https://github.com/blyxxyz/lexopt/issues/12))
- Implement `Debug` for `ValuesIter`.

Bug fixes:

- Change "missing argument at end of command" error message. ([#11](https://github.com/blyxxyz/lexopt/issues/11))

## 0.2.0 (2021-10-23)

While this release is not strictly backward-compatible it should break very few programs.

New:

- Add `Parser::values()` for options with multiple arguments.
- Add `Parser::optional_value()` for options with optional arguments.
- Add `Parser::from_iter()` to construct from an iterator that includes the binary name. ([#5](https://github.com/blyxxyz/lexopt/issues/5))
- Document how to use `Parser::value()` to collect all remaining arguments.

Changes:

- Support `=` as a separator for short options (as in `-o=value`). ([#18](https://github.com/blyxxyz/lexopt/issues/18))
- Sanitize the binary name if it's invalid unicode instead of ignoring it.
- Make `Error::UnexpectedValue.option` a `String` instead of an `Option<String>`.

Bug fixes:

- Include `bin_name` in `Parser`'s `Debug` output.

## 0.1.0 (2021-07-16)
Initial release.
