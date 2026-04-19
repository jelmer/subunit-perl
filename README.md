# Subunit for Perl

Perl bindings for [Subunit](https://github.com/testing-cabal/subunit), plus
command-line tools for running Perl test suites and diffing subunit streams.

## Installation

From CPAN:

```
cpanm Test::Subunit
```

From source:

```
perl Makefile.PL
make
make test
make install
```

## Protocols

Both the v1 (line-oriented text) and v2 (binary) protocols are supported.
See `Test::Subunit` for v1 emit/parse helpers and `Test::Subunit::V2` for v2.
`parse_results` auto-detects v2 by the `0xB3` signature byte.

## Command-line tools

### `prove-subunit`

Run a Perl test suite and emit results on stdout in the subunit protocol.
Tests are executed in-process via `TAP::Harness` — no external `prove` or
`tap2subunit` is invoked.

```
prove-subunit t/
prove-subunit --v1 -I lib t/basic.t
prove-subunit -j 4 -r t/
```

Defaults to subunit v2; pass `--v1` for the text protocol.

### `subunit-diff`

Diff two subunit streams and report tests whose outcome changed:

```
subunit-diff old.subunit new.subunit
```

## License

Apache License 2.0 or later.

## More information

See the main [Subunit homepage](https://github.com/testing-cabal/subunit) for
details. IRC channel: `#testing-cabal` on [irc.libera.chat](https://libera.chat).
