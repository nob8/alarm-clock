# Goal statement
* Implement a fully-featured alarm clock in multiple languages
* Each language should most naturally model the alarm clock's operation using its native data modeling tools
* To keep the source and test files together (And any external dependency management), each language will be a top-level folder in this repository. For example:
  * Java - /java/src/org/nickbeau/alarmclock, /java/tst/org/nickbeau/alarmclock, and /java/pom.xml
  * F# - /fsharp/AlarmClock.sln, fsharp/AlarmClock/AlarmClock.fsproj
  * Rust - /rust/Cargo.toml, /rust/src/alarmclockbase, /rust/src/alarmclockdata,
  * etc
* Also keeping in spirit with the goal of expressing using a language's natrual modeling behavior, code organization within a language directory should be a language-idomatic structure, and should not try to mimic other language structures

# Languages
The thing I find most interesting is to explore the implementation and tradeoffs between various runtimes. So, the list of languages I plan to try are:


| Language    | Runtime        |
|-------------|----------------|
| Java        | JVM            |
| F#          | CLR/.NET Core  |
| Rust        | LLVM           |
| Elixir      | BEAM           |
| Typescript  | V8             |
| Raku/Perl6  | MoarVM         |

After all the runtimes are covered, going back for some alternatives could be interesting too:

* Clojure - More tightly focused on immutability than F#, different approach to currying
* OCaml - A none-of-the-above native target
* Nim - The hot stuff from imperative programming land
