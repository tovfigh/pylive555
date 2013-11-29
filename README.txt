Mike McCandless, mikemccand at gmail.com

This contains a small Python wrapper around the Live555 Streaming
Media APIs, so that you can load video frames.  It only wraps a tiny,
tiny subset of all of Live555's APIs, specifically the APIs necessary
to pull frames via RTSP/RTP from an IP camera.

I've only tested on Linux with Python 3, with the surprisingly
excellent Lorex LNB2151/LNB2153 cameras, with H264 video.  Please
report back if you succeed with other cameras.

INSTRUCTIONS:

  * First, download and compile/install the Live555 library from
    http://www.live555.com/liveMedia/public, and unzip/tar it and run:

    * ./genMakefiles linux
    * export CPPFLAGS=-fPIC CFLAGS=-fPIC
    * make
    * [optional: make install]

  * If you unxip/tar'd Live55 in this directory, to the subdirectory
    "live", then you can skip this step; otherwise, you'll need to
    edit INSTALL_DIR in setup.py to point to the live headers
    and libraries.

  * Build the python bindings: python3 setup.py build; make sure
    there are no errors

  * Run the example

      python3 example.py 10.17.4.118 1 10 out.264
    
    That will record 10 seconds of H264 video from the camera at
    10.17.4.118, channel 1, saving it to the file out.264.