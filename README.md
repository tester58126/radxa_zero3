dtbo compile

```
cpp -nostdinc -I /usr/src/linux-headers-$(uname -r)/include -undef -x assembler-with-cpp  tc358743.dts > tc358743.dts.preprocessed
dtc -@ -i /usr/src/linux-headers-$(uname -r)/include -H epapr -I dts -O dtb -o tc358743.dtbo -Wno-unit_address_vs_reg tc358743.dts.preprocessed
```

setting 

```
root@radxa-zero3:/home/rock/test# v4l2-ctl --list-devices
rkisp-statistics (platform: rkisp):
        /dev/video15
        /dev/video16

rkcif_mipi_lvds (platform:rkcif):
        /dev/media0

rkcif (platform:rkcif_mipi_lvds):
        /dev/video0
        /dev/video1
        /dev/video2
        /dev/video3
        /dev/video4
        /dev/video5
        /dev/video6
        /dev/video7

rkisp_mainpath (platform:rkisp-vir0):
        /dev/video8
        /dev/video9
        /dev/video10
        /dev/video11
        /dev/video12
        /dev/video13
        /dev/video14
        /dev/media1
```

```
root@radxa-zero3:/home/rock/test# media-ctl -d /dev/media0 -p
Media controller API version 5.10.160

Media device information
------------------------
driver          rkcif
model           rkcif_mipi_lvds
serial          
bus info        
hw revision     0x0
driver version  5.10.160

Device topology
- entity 1: stream_cif_mipi_id0 (1 pad, 4 links)
            type Node subtype V4L flags 0
            device node name /dev/video0
        pad0: Sink
                <- "rockchip-mipi-csi2":1 [ENABLED]
                <- "rockchip-mipi-csi2":2 []
                <- "rockchip-mipi-csi2":3 []
                <- "rockchip-mipi-csi2":4 []

- entity 5: stream_cif_mipi_id1 (1 pad, 4 links)
            type Node subtype V4L flags 0
            device node name /dev/video1
        pad0: Sink
                <- "rockchip-mipi-csi2":1 []
                <- "rockchip-mipi-csi2":2 [ENABLED]
                <- "rockchip-mipi-csi2":3 []
                <- "rockchip-mipi-csi2":4 []

- entity 9: stream_cif_mipi_id2 (1 pad, 4 links)
            type Node subtype V4L flags 0
            device node name /dev/video2
        pad0: Sink
                <- "rockchip-mipi-csi2":1 []
                <- "rockchip-mipi-csi2":2 []
                <- "rockchip-mipi-csi2":3 [ENABLED]
                <- "rockchip-mipi-csi2":4 []

- entity 13: stream_cif_mipi_id3 (1 pad, 4 links)
             type Node subtype V4L flags 0
             device node name /dev/video3
        pad0: Sink
                <- "rockchip-mipi-csi2":1 []
                <- "rockchip-mipi-csi2":2 []
                <- "rockchip-mipi-csi2":3 []
                <- "rockchip-mipi-csi2":4 [ENABLED]

- entity 17: rkcif_tools_id0 (1 pad, 4 links)
             type Node subtype V4L flags 0
             device node name /dev/video4
        pad0: Sink
                <- "rockchip-mipi-csi2":1 []
                <- "rockchip-mipi-csi2":2 []
                <- "rockchip-mipi-csi2":3 []
                <- "rockchip-mipi-csi2":4 []

- entity 21: rkcif_tools_id1 (1 pad, 4 links)
             type Node subtype V4L flags 0
             device node name /dev/video5
        pad0: Sink
                <- "rockchip-mipi-csi2":1 []
                <- "rockchip-mipi-csi2":2 []
                <- "rockchip-mipi-csi2":3 []
                <- "rockchip-mipi-csi2":4 []

- entity 25: rkcif_tools_id2 (1 pad, 4 links)
             type Node subtype V4L flags 0
             device node name /dev/video6
        pad0: Sink
                <- "rockchip-mipi-csi2":1 []
                <- "rockchip-mipi-csi2":2 []
                <- "rockchip-mipi-csi2":3 []
                <- "rockchip-mipi-csi2":4 []

- entity 29: rkcif-mipi-luma (0 pad, 0 link)
             type Node subtype V4L flags 0
             device node name /dev/video7

- entity 32: rockchip-mipi-csi2 (5 pads, 29 links)
             type V4L2 subdev subtype Unknown flags 0
             device node name /dev/v4l-subdev0
        pad0: Sink
                [fmt:RGB888_1X24/1920x1080 field:none colorspace:srgb
                 crop.bounds:(0,0)/1920x1080
                 crop:(0,0)/1920x1080]
                <- "rockchip-csi2-dphy0":1 [ENABLED]
        pad1: Source
                -> "stream_cif_mipi_id0":0 [ENABLED]
                -> "stream_cif_mipi_id1":0 []
                -> "stream_cif_mipi_id2":0 []
                -> "stream_cif_mipi_id3":0 []
                -> "rkcif_tools_id0":0 []
                -> "rkcif_tools_id1":0 []
                -> "rkcif_tools_id2":0 []
        pad2: Source
                -> "stream_cif_mipi_id0":0 []
                -> "stream_cif_mipi_id1":0 [ENABLED]
                -> "stream_cif_mipi_id2":0 []
                -> "stream_cif_mipi_id3":0 []
                -> "rkcif_tools_id0":0 []
                -> "rkcif_tools_id1":0 []
                -> "rkcif_tools_id2":0 []
        pad3: Source
                -> "stream_cif_mipi_id0":0 []
                -> "stream_cif_mipi_id1":0 []
                -> "stream_cif_mipi_id2":0 [ENABLED]
                -> "stream_cif_mipi_id3":0 []
                -> "rkcif_tools_id0":0 []
                -> "rkcif_tools_id1":0 []
                -> "rkcif_tools_id2":0 []
        pad4: Source
                -> "stream_cif_mipi_id0":0 []
                -> "stream_cif_mipi_id1":0 []
                -> "stream_cif_mipi_id2":0 []
                -> "stream_cif_mipi_id3":0 [ENABLED]
                -> "rkcif_tools_id0":0 []
                -> "rkcif_tools_id1":0 []
                -> "rkcif_tools_id2":0 []

- entity 38: rockchip-csi2-dphy0 (2 pads, 2 links)
             type V4L2 subdev subtype Unknown flags 0
             device node name /dev/v4l-subdev1
        pad0: Sink
                [fmt:RGB888_1X24/1920x1080@10000/600000 field:none colorspace:srgb]
                <- "m00_b_tc35874x 2-000f":0 [ENABLED]
        pad1: Source
                -> "rockchip-mipi-csi2":0 [ENABLED]

- entity 43: m00_b_tc35874x 2-000f (1 pad, 1 link)
             type V4L2 subdev subtype Sensor flags 0
             device node name /dev/v4l-subdev2
        pad0: Source
                [fmt:RGB888_1X24/1920x1080@10000/600000 field:none colorspace:srgb]
                [dv.caps:BT.656/1120 min:1x1@0 max:10000x10000@310000000 stds:CEA-861,DMT,CVT,GTF caps:interlaced,progressive,reduced-blanking,custom]
                [dv.detect:BT.656/1120 1920x1080p30 (2200x1125) stds: flags:]
                [dv.current:BT.656/1120 1920x1080p30 (2200x1125) stds: flags:]
                -> "rockchip-csi2-dphy0":0 [ENABLED]
```

```
v4l2-ctl -d /dev/v4l-subdev2 --set-edid=file=edid.txt --fix-edid-checksums
v4l2-ctl -d /dev/v4l-subdev2 --query-dv-timings
v4l2-ctl -d /dev/v4l-subdev2 --set-dv-bt-timings query
```

test
`v4l2-ctl --device /dev/video0 --set-fmt-video=width=1920,height=1080,pixelformat=RGB3, --stream-mmap --stream-to=frame.raw --stream-count=1 --verbose`

upload frame.raw to `https://rawpixels.net/`

