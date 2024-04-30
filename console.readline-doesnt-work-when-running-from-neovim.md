# `Console.ReadLine()` Not Waiting For Input When Running Program From Within NeoVim

## Problem

I was working on a simple `C#` console app which involved a `Console.ReadLine()` statement. I tried to test it by running the command `:!dotnet run` from within NeoVim, but the program did not wait for my input.

## Solution

Type the `dotnet run` command directly into the terminal.
