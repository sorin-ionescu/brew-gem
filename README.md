brew-gem -- install gems as Homebrew formulas
=============================================

`brew gem` allows you to install any Ruby gem as a Homebrew formula.

It works by generating a stub formula for Homebrew, which looks something like this:

    class Ronn < Formula
      def initialize(*args)
        @name = "ronn"
        @version = "0.7.3"
        super
      end

      def install
        system "bundle", "install", "--path=#{libexec + name}", "--binstubs"
      end
    end

This formula installs and unpacks all the dependencies under the Cellar path. So the package is completely self contained.

Install
-------

    gem install bundler
    brew install brew-gem

Usage
-----

    brew gem heroku

Additionally, you may declare additional dependent gems that are
specifically required by the original gem. For example, let's say you
wanted to install capistrano and you need the capistrano-ext gem as
well.

    brew gem capistrano capistrano-ext

Philosophy
----------

This is **not** for installing development libraries, but for standalone binary tools that you want system wide.
