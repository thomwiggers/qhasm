QHASM
=====
Modified version of [qhasm][qhasm] for ARM11.
This was done to support my implementation of [Prøst on ARM11][proest].

Notes and changes
=================

* Since the machine description is a shell script, and the Raspberry Pi
on which I was running this was quite slow, it has a small modification
to cache the output the machine description shell script. [commit][2]

* it has a [flag-setting 'and'][3] and [support for the = flag][4]

* Some syntax fixes in generated code

* Some hacks to overcome register allocator limitations (>32 bit loads
have restrictions the allocator doesn't understand) e.g. [commit][5]

* Some [bespoke modifications][6] to have even wider stores.

There is also a 'stackless' branch, where the stack pointer is made
available to the register allocator. This is the version used by my
Prøst implementation. This modification does of course mean that you
can't use the stack anymore, and need to store/load the stack pointer
somewhere (as in [this line][7]).

If you have any further questions, feel free to ask me.

Cheers,

Thom Wiggers

[1]: https://thomwiggers.nl/proest/
[2]: https://github.com/thomwiggers/qhasm/commit/16b045842201c01abd353fdb3c5a576802b32309
[3]: https://github.com/thomwiggers/qhasm/commit/2dd73992255ac2cbc7909fbd9ab9835b3d3056d0
[4]: https://github.com/thomwiggers/qhasm/commit/2942400319ab19117e4c2fbff70a8714c5a07e37
[5]: https://github.com/thomwiggers/qhasm/commit/8e92dc014dfc0974a44aa73f219ffc4a94ac4fe0
[6]: https://github.com/thomwiggers/qhasm/commit/fae76c3c5c23fa1a7f4c3bbe14504b9fe73d3e6a
[7]: https://github.com/thomwiggers/proest-arm11/blob/master/proest_unrolled.pq#L112

[proest]: https://thomwiggers.nl/proest
[qhasm]: http://qhasm.cr.yp.to
