# Alien::FFI [![Build Status](https://secure.travis-ci.org/Perl5-FFI/Alien-FFI.png)](http://travis-ci.org/Perl5-FFI/Alien-FFI)

Build and make available libffi

# SYNOPSIS

In your Build.PL:

    use Module::Build;
    use Alien::FFI;
    my $builder = Module::Build->new(
      ...
      configure_requires => {
        'Alien::FFI' => '0',
        ...
      },
      extra_compiler_flags => Alien::FFI->cflags,
      extra_linker_flags   => Alien::FFI->libs,
      ...
    );
    
    $build->create_build_script;

In your Makefile.PL:

    use ExtUtils::MakeMaker;
    use Config;
    use Alien::FFI;
    
    WriteMakefile(
      ...
      CONFIGURE_REQUIRES => {
        'Alien::FFI' => '0',
      },
      CCFLAGS => Alien::FFI->cflags . " $Config{ccflags}",
      LIBS    => [ Alien::FFI->libs ],
      ...
    );

# DESCRIPTION

This distribution installs libffi so that it can be used by other Perl distributions.  If already
installed for your operating system, and it can be found, this distribution will use the libffi
that comes with your operating system, otherwise it will download it from the Internet, build and
install it for you.

# SEE ALSO

- [FFI::Platypus](https://metacpan.org/pod/FFI::Platypus)

    Write Perl bindings to non-Perl libraries without C or XS

- [FFI::CheckLib](https://metacpan.org/pod/FFI::CheckLib)

    Check that a library is available for FFI

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2014 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
