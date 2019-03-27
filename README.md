# plutosdr-cessb

SSB Tx GNU Radio flowgraph for PlutoSDR - based on [Controlled Envelope SSB blocks by @drmpeg](http://www.github.com/drmpeg/gr-cessb)

![cessb-flowgraph](https://user-images.githubusercontent.com/192318/55104005-9349bd80-50ef-11e9-84e0-c24b67914b91.png)

----

## CSDR based TX commandline:

pluto: 
```
     $ netcat -l -s 192.168.2.1 -p 8011 | csdr convert_i16_f | csdr dsb_fc | csdr bandpass_fir_fft_cc 0.01 0.1 0.01 | csdr rational_resampler_ff 50 1 0.05 | csdr gain_ff 10 | csdr convert_f_i16 | leaniiotx --nbufs 32 --bufsize 0x8000 -s 2400000 --bw 200000 -f 145100000 -v -d
```

host: 
```
    $ arecord -fS16_LE -r48000 -c1 - | nc pluto.local 8011
```
 ![csdr-cmdline](https://user-images.githubusercontent.com/192318/55104017-9775db00-50ef-11e9-9a9b-7957326d8125.png)   
