# NAME

Return::Type::Lexical - Same thing as Return::Type, but lexical

# VERSION

version 0.002

# SYNOPSIS

    use Return::Type::Lexical;
    use Types::Standard qw(Int);

    sub foo :ReturnType(Int) { return "not an int" }

    {
        no Return::Type::Lexical;
        sub bar :ReturnType(Int) { return "not an int" }
    }

    my $foo = foo();    # throws an error
    my $bar = bar();    # returns "not an int"

    # Can also be used with Devel::StrictMode to only perform
    # type checks in strict mode:

    use Devel::StrictMode;
    use Return::Type::Lexical check => STRICT;

# DESCRIPTION

This module works just like [Return::Type](https://metacpan.org/pod/Return%3A%3AType), but type-checking can be enabled and disabled within
lexical scopes.

There is no runtime penalty when type-checking is disabled.

# METHODS

## import

The `check` attribute can be used to set whether or not types are checked.

# BUGS

Please report any bugs or feature requests on the bugtracker website
[https://github.com/chazmcgarvey/Return-Type-Lexical/issues](https://github.com/chazmcgarvey/Return-Type-Lexical/issues)

When submitting a bug or request, please include a test-file or a
patch to an existing test-file that illustrates the bug or desired
feature.

# AUTHOR

Charles McGarvey <chazmcgarvey@brokenzipper.com>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2020 by Charles McGarvey.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
