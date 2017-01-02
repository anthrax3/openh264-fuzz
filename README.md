# openh264-fuzz
Bug #1
--
```
=================================================================
==4637==ERROR: AddressSanitizer: heap-use-after-free on address 0x62f000092410 at pc 0x00000042fa6a bp 0x7ffeffda4c00 sp 0x7ffeffda4bf0
READ of size 1 at 0x62f000092410 thread T0
    #0 0x42fa69 in WelsDec::FmoNextMb(WelsDec::TagFmo*, short) (/root/asan/openh264/h264dec+0x42fa69)
    #1 0x471797 in WelsDec::WelsDecodeSlice(WelsDec::TagWelsDecoderContext*, bool, WelsDec::TagNalUnit*) (/root/asan/openh264/h264dec+0x471797)
    #2 0x424170 in WelsDec::DecodeCurrentAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x424170)
    #3 0x4275e8 in WelsDec::ConstructAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4275e8)
    #4 0x40db32 in WelsDecodeBs (/root/asan/openh264/h264dec+0x40db32)
    #5 0x4089b9 in WelsDec::CWelsDecoder::DecodeFrameNoDelay(unsigned char const*, int, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4089b9)
    #6 0x404995 in H264DecodeInstance(ISVCDecoder*, char const*, char const*, int&, int&, char const*, char const*) (/root/asan/openh264/h264dec+0x404995)
    #7 0x402be3 in main (/root/asan/openh264/h264dec+0x402be3)
    #8 0x7f4c8cec082f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #9 0x403608 in _start (/root/asan/openh264/h264dec+0x403608)

0x62f000092410 is located 24592 bytes inside of 48147-byte region [0x62f00008c400,0x62f000098013)
freed by thread T0 here:
    #0 0x7f4c8dba22ca in __interceptor_free (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x982ca)
    #1 0x42f182 in WelsDec::InitFmo(WelsDec::TagFmo*, WelsDec::TagPps*, int, int, WelsCommon::CMemoryAlign*) (/root/asan/openh264/h264dec+0x42f182)
    #2 0x42f883 in WelsDec::FmoParamUpdate(WelsDec::TagFmo*, WelsDec::TagSps*, WelsDec::TagPps*, int*, WelsCommon::CMemoryAlign*) (/root/asan/openh264/h264dec+0x42f883)
    #3 0x423772 in WelsDec::DecodeCurrentAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x423772)
    #4 0x4275e8 in WelsDec::ConstructAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4275e8)
    #5 0x40e70f in WelsDecodeBs (/root/asan/openh264/h264dec+0x40e70f)
    #6 0x406ef9 in WelsDec::CWelsDecoder::DecodeFrame2(unsigned char const*, int, unsigned char**, TagBufferInfo*) [clone .part.3] [clone .constprop.6] (/root/asan/openh264/h264dec+0x406ef9)
    #7 0x408678 in WelsDec::CWelsDecoder::DecodeFrameNoDelay(unsigned char const*, int, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x408678)
    #8 0x404995 in H264DecodeInstance(ISVCDecoder*, char const*, char const*, int&, int&, char const*, char const*) (/root/asan/openh264/h264dec+0x404995)
    #9 0x402be3 in main (/root/asan/openh264/h264dec+0x402be3)
    #10 0x7f4c8cec082f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

previously allocated by thread T0 here:
    #0 0x7f4c8dba2602 in malloc (/usr/lib/x86_64-linux-gnu/libasan.so.2+0x98602)
    #1 0x4b5a78 in WelsCommon::WelsMalloc(unsigned int, char const*, unsigned int) (/root/asan/openh264/h264dec+0x4b5a78)
    #2 0x4b5b64 in WelsCommon::CMemoryAlign::WelsMalloc(unsigned int, char const*) (/root/asan/openh264/h264dec+0x4b5b64)
    #3 0x4b5c0f in WelsCommon::CMemoryAlign::WelsMallocz(unsigned int, char const*) (/root/asan/openh264/h264dec+0x4b5c0f)
    #4 0x42f19a in WelsDec::InitFmo(WelsDec::TagFmo*, WelsDec::TagPps*, int, int, WelsCommon::CMemoryAlign*) (/root/asan/openh264/h264dec+0x42f19a)
    #5 0x42f883 in WelsDec::FmoParamUpdate(WelsDec::TagFmo*, WelsDec::TagSps*, WelsDec::TagPps*, int*, WelsCommon::CMemoryAlign*) (/root/asan/openh264/h264dec+0x42f883)
    #6 0x423772 in WelsDec::DecodeCurrentAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x423772)
    #7 0x4275e8 in WelsDec::ConstructAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4275e8)
    #8 0x40db32 in WelsDecodeBs (/root/asan/openh264/h264dec+0x40db32)
    #9 0x4089b9 in WelsDec::CWelsDecoder::DecodeFrameNoDelay(unsigned char const*, int, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4089b9)
    #10 0x404995 in H264DecodeInstance(ISVCDecoder*, char const*, char const*, int&, int&, char const*, char const*) (/root/asan/openh264/h264dec+0x404995)
    #11 0x402be3 in main (/root/asan/openh264/h264dec+0x402be3)
    #12 0x7f4c8cec082f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)

SUMMARY: AddressSanitizer: heap-use-after-free ??:0 WelsDec::FmoNextMb(WelsDec::TagFmo*, short)
Shadow bytes around the buggy address:
  0x0c5e8000a430: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a440: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a450: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a460: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a470: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
=>0x0c5e8000a480: fd fd[fd]fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a490: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a4a0: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a4b0: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a4c0: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
  0x0c5e8000a4d0: fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd fd
Shadow byte legend (one shadow byte represents 8 application bytes):
  Addressable:           00
  Partially addressable: 01 02 03 04 05 06 07
  Heap left redzone:       fa
  Heap right redzone:      fb
  Freed heap region:       fd
  Stack left redzone:      f1
  Stack mid redzone:       f2
  Stack right redzone:     f3
  Stack partial redzone:   f4
  Stack after return:      f5
  Stack use after scope:   f8
  Global redzone:          f9
  Global init order:       f6
  Poisoned by user:        f7
  Container overflow:      fc
  Array cookie:            ac
  Intra object redzone:    bb
  ASan internal:           fe
==4637==ABORTING
```
Bug#2
--
```
ASAN:SIGSEGV
=================================================================
==23331==ERROR: AddressSanitizer: SEGV on unknown address 0x7ffbc5f0d810 (pc 0x0000004718b7 bp 0x7ffe5107f130 sp 0x7ffe5107f010 T0)
    #0 0x4718b6 in WelsDec::WelsDecodeSlice(WelsDec::TagWelsDecoderContext*, bool, WelsDec::TagNalUnit*) (/root/asan/openh264/h264dec+0x4718b6)
    #1 0x424170 in WelsDec::DecodeCurrentAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x424170)
    #2 0x4275e8 in WelsDec::ConstructAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4275e8)
    #3 0x40db32 in WelsDecodeBs (/root/asan/openh264/h264dec+0x40db32)
    #4 0x4089b9 in WelsDec::CWelsDecoder::DecodeFrameNoDelay(unsigned char const*, int, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4089b9)
    #5 0x404995 in H264DecodeInstance(ISVCDecoder*, char const*, char const*, int&, int&, char const*, char const*) (/root/asan/openh264/h264dec+0x404995)
    #6 0x402be3 in main (/root/asan/openh264/h264dec+0x402be3)
    #7 0x7ffbc872182f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #8 0x403608 in _start (/root/asan/openh264/h264dec+0x403608)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV ??:0 WelsDec::WelsDecodeSlice(WelsDec::TagWelsDecoderContext*, bool, WelsDec::TagNalUnit*)
==23331==ABORTING
```
Bug #3
--
```
ASAN:SIGSEGV
=================================================================
==1153==ERROR: AddressSanitizer: SEGV on unknown address 0x631fffff0810 (pc 0x00000047b82c bp 0x7ffd652e7c60 sp 0x7ffd652e7b70 T0)
    #0 0x47b82b in WelsDec::WelsDecodeMbCavlcPSlice(WelsDec::TagWelsDecoderContext*, WelsDec::TagNalUnit*, unsigned int&) (/root/asan/openh264/h264dec+0x47b82b)
    #1 0x4718f1 in WelsDec::WelsDecodeSlice(WelsDec::TagWelsDecoderContext*, bool, WelsDec::TagNalUnit*) (/root/asan/openh264/h264dec+0x4718f1)
    #2 0x424170 in WelsDec::DecodeCurrentAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x424170)
    #3 0x4275e8 in WelsDec::ConstructAccessUnit(WelsDec::TagWelsDecoderContext*, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4275e8)
    #4 0x40db32 in WelsDecodeBs (/root/asan/openh264/h264dec+0x40db32)
    #5 0x4089b9 in WelsDec::CWelsDecoder::DecodeFrameNoDelay(unsigned char const*, int, unsigned char**, TagBufferInfo*) (/root/asan/openh264/h264dec+0x4089b9)
    #6 0x404995 in H264DecodeInstance(ISVCDecoder*, char const*, char const*, int&, int&, char const*, char const*) (/root/asan/openh264/h264dec+0x404995)
    #7 0x402be3 in main (/root/asan/openh264/h264dec+0x402be3)
    #8 0x7fe32ace282f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x2082f)
    #9 0x403608 in _start (/root/asan/openh264/h264dec+0x403608)

AddressSanitizer can not provide additional info.
SUMMARY: AddressSanitizer: SEGV ??:0 WelsDec::WelsDecodeMbCavlcPSlice(WelsDec::TagWelsDecoderContext*, WelsDec::TagNalUnit*, unsigned int&)
==1153==ABORTING
```
