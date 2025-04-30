

## 分辨率(Resolution)
!!! note "分辨率"

    图片分辨率和视频分辨率在概念上相似，但应用领域和具体含义有一些不同。图片分辨率有两个含义，视频分辨率只有一个含义。

    两者的主要区别在于应用场景：
    
    - 图片分辨率更多用于静态图像，考虑到显示和打印的清晰度。
    - 视频分辨率用于动态影像，关注的是每一帧图像的像素数，从而影响视频播放时的清晰度和细节程度。

    === "图片分辨率"

        1.通常指图像的像素大小，即宽度和高度的像素数乘积。例如，1920x1080px的图片表示图像宽度为1920px，高度为1080px。

        2.还可以指图像的像素密度(Pixel Density)，通常以像素每英寸(Pixel Per Inch, PPI)表示，用来衡量图像的细节和清晰度，特别是在打印时。


        | Term       | Description                          | Context                | Physical Size          |
        |------------|--------------------------------------|------------------------|------------------------|
        | **Pixel**  | Smallest unit in digital images      | Screens, bitmap graphics | Depends on display PPI |
        | **Point**  | Absolute unit (1pt = 1/72 inch)      | Print, LaTeX, vectors  | Fixed: ~0.353mm        |
        | **Dot**    | Physical ink dot in printing         | Printers, PDF output   | Depends on device DPI  |

        When displayed on a screen, dots corresponds to pixels. So we can immediately deduce the figure size will be exactely 600×600 pixels. Same is true if you save the figure in a bitmap format like `jpg` or `png`.

        This confirms that the image geometry is 600×600 while the resolution is 39.37 ppc which corresponds to 39.37*2.54 ≈ 100 dpi.

        If you were to include this image inside a document while keep the same dpi, you would need to set the size of the image to 15.24cm by xxcm. If you reduce the size of the image in your document, let's say by a factor of 3, this will mechanically increase the figure dpi to 300 in this specific case.
        
        For a scientific article, publisher will generally request figures dpi to be between 300 and 600. To get things right, it is thus good to konw what will be the physical dimension of your figure once inserted into your document.

        In $\LaTeX$, a point(pt) corresponds to 1/72.27 inches while in matplotlib it corresponds to 1/72 inches.

    === "视频分辨率"
    
        指视频每一帧的像素大小，即每一帧图像的宽度和高度的像素数。
        
        视频分辨率只有一个含义，表示像素大小，不涉及像素密度（PPI），因为视频主要用于显示而非打印。

        !!! tip "常见的视频分辨率"

            - 标清(SD, Standard Definition)。宽高比为4:3
                - 480p: 640x480，这是传统电视和一些网络视频的分辨率。
            - 高清(HD, High Definition)。宽高比为16:9
                - 720p: 1280x720，一般称为“准高清”，常用于网络视频和一些高清电视台。
                - 1080p: 1920x1080，称为“全高清”，是目前电视和网络视频的主流分辨率。
            - 超高清(UHD, Ultra High Definition)。宽高比为16:9
                - 4K: 3840x2160，4K电视和视频逐渐普及，提供更高的清晰度和细节。
                - 8K: 7680x4320，是目前最高的消费级视频分辨率，主要用于高端电视和专业显示器。
            - 其他常见分辨率
                - 1440p: 2560x1440，宽高比为16:9，介于1080p和4K之间，常用于高端电脑显示器。




## 计算机存储单位

计算机存储单位有两种：字节(Byte)和比特(bit)。1Byte=8 bit，1MB=8Mb

**MB** 和 **Mb**，即兆字节(megabyte[^1])和兆比特(megabit)。

[^1]: 1MB=1024KB=1024*1024B, 但有时我们认为倍数是1000，故Megabyte is a million bytes (MB), and gigabyte is a billion bytes (GB).

在办理宽带时，电信商经常会说，我们提供的是“千兆宽带”。这里的单位，实际上是Mbps，意思是说它们的宽带能提供最高 1000Mbps 的传输速度。请注意，这里的b是小写的。Mbps，就是Mb per second，代表传输速度。

而我们常说的，下载一个文件有多少多少M，这里的单位是MB。请注意，这里的B是大写的。

所以“千兆宽带”（1000 Mbps），理论上的最高下载速度，是每秒钟最多下125MB的文件。


## 码率，也称为比特率(bit rate)

码率的单位是 Mbps。所以，**一个视频的平均码率计算方式为：**

**码率**（单位为 Mbps）**=文件大小**（单位为 MB）**✖️8➗ 视频时长**（单位为秒）


## 编码方式

## 刷新率

## 色深


> References: 
>
> [Scientific Visualization: Python + Matplotlib](https://github.com/rougier/scientific-visualization-book)