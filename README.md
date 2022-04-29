# Lua Receiver C API 
<!-- ---------------------------------------------------------------------------------------- -->

The *Receiver C API* can be used to get asynchronous messages from native code running 
in other threads.

   * Lua objects implementing the *Receiver C API* can receive asynchronous messages.
   * Native C code invoking the *Receiver C API* can send asynchronous messages from any thread.

Lua objects implementing the *Receiver C API* must
have an associated meta table entry *_capi_receiver* delivered by
the C API function *receiver_get_capi()* and the associated 
C API function *toReceiver()* must return a valid pointer for the given 
receiver object. For further documentation see [receiver_capi.h](./receiver_capi.h).

<!-- ---------------------------------------------------------------------------------------- -->

### Implementations:

   * [mtmsg] buffer objects are implementing the *Receiver C API*. If invoked, the arguments
     are appended to the buffer as a new message.

   * [mtstates] state objects are implementing the *Receiver C API*. If invoked, the state's
     callback function is invoked with the message arguments.

### Invocations:

   * [ljack] client objects are sending [JACK status messages] to a registered receiver object,
     see [ljack.client_open()] and [ljack/example02.lua].

   * [ljack] midi receiver processor objects are sending midi messages that were received from a
     JACK MIDI IN port to a registered receiver object, see [ljack.new_midi_receiver()] 
     and [ljack/example03.lua].


<!-- ---------------------------------------------------------------------------------------- -->

[mtmsg]:                     https://github.com/osch/lua-mtmsg

[mtstates]:                  https://github.com/osch/lua-mtstates

[ljack]:                     https://github.com/osch/lua-ljack
[ljack/example02.lua]:       https://github.com/osch/lua-ljack/blob/master/examples/example02.lua
[ljack/example03.lua]:       https://github.com/osch/lua-ljack/blob/master/examples/example03.lua
[ljack.client_open()]:       https://github.com/osch/lua-ljack/blob/master/doc/README.md#ljack_client_open
[ljack.new_midi_receiver()]: https://github.com/osch/lua-ljack/blob/master/doc/README.md#ljack_new_midi_receiver
[JACK status messages]:      https://github.com/osch/lua-ljack/blob/master/doc/README.md#status-messages

<!-- ---------------------------------------------------------------------------------------- -->

## License 

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this
software, either in source code form or as a compiled binary, for any purpose,
commercial or non-commercial, and by any means.

<!-- ---------------------------------------------------------------------------------------- -->
