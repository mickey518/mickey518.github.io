---
layout: posts
title:  "Java Sound API 使用入门"
date:   2022-04-22 08:00:00 +0800
tags:   Java JavaSoundAPI
categories: Java
toc:    true
---

Java Sound API 官方地址：[JAVA Sound Guide](https://docs.oracle.com/javase/8/docs/technotes/guides/sound/programmer_guide/contents.html)  [JavaDoc](https://docs.oracle.com/javase/8/docs/api/index.html?javax/sound/sampled/Clip.html)

## 概要

`Java Sound API` 的数字音频架构，可通过`javax.sound.sampled` 包访问

`Java Sound API` 包括对数字音频和 MIDI 数据的支持。这两个主要的功能模块在单独的包中提供：

-   `javax.sound.sampled` 此包指定了用于捕获、混合和播放数字（采样）音频的接口。
-   `javax.sound.midi` 这个包提供了 MIDI 合成、排序和事件传输的接口。


另外两个包允许服务提供者（与应用程序开发者相反）创建自定义软件组件，以扩展 `Java Sound API` 实现的功能：

-   `javax.sound.sampled.spi`
-   `javax.sound.midi.spi`

![Java sound class-diagram](http://plantuml.mickey.wang:8665/plantuml/svg/nHjhS-EuxRj-XMRsYpBd-1TajkVOogrRlyQFR6zkRZAAH2UwbILLbDBujjlVNZv4yI6Iakoq_R0R4GH040190AH_XcLGbDKfSVyQl0KkpAeqSiCaWF0sYeEN8ZWvfEN-WRhVnwH_38DJde1el8XJS4XHHvm4pmdmtqEGbt6Mkj-Tdzoxksa1WX9y_koQyBoRddYxieZJbnldXnEd9IYEGGYq0csoeaI3_x38Z576y_IO4I6_e-cNSVZ39P3bVBfTRxwiLtwhQp5V-K_pLGi-NIyta-d-QJRVJLkTkuq_-Pk_RS6_-9EPPPZrOU_SkdJERXgS06ezPra2WjIDuIwhYX38YiEqtXJF-UuldqUKSbIJO1tNl5v0kKBiYDfLXXBm59JXAu0UDWXHbjW9_b452VJMpt-0iCGTo2RkQm1Vfrb4sTJ3bHdzyB3XWcTO5a5OkcRJm3mUJweepXxY16n148626edH_cXw7x82oOWdf82yUPfN9HeN1AUReRI7xM8m3VxK40bYD5G2h4FCBcgze5rKLDIkDKJTOHQK0RO-CS1R5aTkbeFKexCdCnyXDZUcJkOM_opY4dZFvnByzZice4IzlO4ocsRf6oWWsWWsHVOMczo2u8xzDCmYv7I__OvrG2V3OD2xwKct3mhqlqodhXZMkwlo76qg8F9q_6HAcMytvIMoAcRWWtCzsWSUAHoqGeXZKmZinQotE1rIT3cxMPRhbbvBGebTr-AQ9d4k7pnubIpMwytJTBtQprU7zM6t-DMuvjILrC9J9eUvOmEXSnmiGFfIlX9NJZ9w6YpZiCWW2BCq4de9IrXJRJ8OapDO70zAf0qAPYlYBB8itsI847ggn0dgylfl1jFib6C0yfcoo1Aambkt_aQE6D8lw7mI3qM5njkVSp1gYB0ad0FM1JWzWw86GUCvrbl6CHuF2Ih9X652D6CFhVmta9PageHLYVv3tyHsUQtoTln4YCZ1FI8JPZOXcpcQ9lvB9aTuuYMCHHATGZRxS3qqKZ0DoB6CuFkaVxtnLotWTB7U-IteRZ_PxZNGzSQYvMi35_D43oba6rSJ5HXZO2ko6WZRaRd_z5evVCLmDr8M2byWMiyOkWua_vUj__-m4r7XxWnBS6hllQlr_Wd5wTFvmzoV8M45yGGw6ZWmkcNy3WeI5zTR1swJ6BoDrlHxd4h2Qc9iCMB1GC9GYi1DDFGKxg3X1o_kvqUkUOHckz2ZaBCCeU2_dhd7C6qbp6ncpY1g67CHuSWmE5MOo4E660SVGcWQ_A98JeuAhs9by8gBeqD9c8yBopHpl3Jc73xR3vjadxaDocS7aB8iSG19ayqEcgzLnhwvx20YlPny8kJmeUxIz60Gz0p-m11KRv0vNZQarGM6Yc1tA9vpgsWZBRDrLNuC8sgGM_40WMLpzh6y7QjVWsDAymteIese2-ihdeQArPpDCt0CggG-eZ7jI3ZjL8Ac_b1NqY86gAEO4MQW7uUWqr5gN8cZRLGzUPUiHB5n0SNeepqQhnBUwdnoakT5bXSn2eW4DXtaakan5WPuFL1QscDet258aRD7k2TiSse2XLqRvz4quqK0ORjsZ-HFZNNaQJE2V44Hw3B8xshzq_3qiuiL18eo1ahwgMwjP9dWD5XJG-iYkvvar9PS6-hN1OFxHZy4AcgeMQ-UfS1WrHF1eE3QkBZZB6G25yJtoeOa1_e4ydNos4uf9uSsQFxme0DEsvddQjOgrDSjy5w25BOoT27Z6NrCuYCMztqsw92AkxonVPTATAIFdqTAGDiKpZho8HbFdn1r5SwKmFkwgZIoHdHPKTfFgvEOKLDJeLc_1Kc5TW06eMrvGn1ewH9bn2DkS5OvUyJaWYFmrK9xE8ngd43f4SUjHu3SUfpRiEKbo6rQMbl_qT_UMqjTFPJxa6Ga2cYqUyG0znIdyQawyNRmBhNp0eGnMMfqrwxo24cm0KMSHNn1LcbSGjv4J1V1CqW4IF2kGkA8GUX86gEACbEh4bJfV-nYz4jQ-IDb7xYQRzk1I2y6K_abzsb0IwfF1KYLhcmm1wn41RQiDTa2HrfmhMLvj0qpeNYc70Gx2dNfr_XOUeeQXZkrg5-JLoydkxs_VVfbCbzfpes_F-ryjF_hEhR-_h1T6LQ9dgpkCr0-hXU7PVlmsapQgFUJnMGrrTHE9ylDmd_QJlQ-TPtQj-7s1XmLGPnoynoJ2egt2FXrWTZCSkKkRLkbAJl9XBWpBECtq2_skA-EHtHAnN_o2APvGj2AKQIwDgjuBz1VSw_kfaFotWLu8mvjypUcEFRqu5QfQz2u4zPR6DgT-AmOB7WNO9RhVucnU5NKXs88hc8TUXAnkeniJmhLbbe42ot5QOkcMufpxtwfS4duo7A5Jowh8hcW_a0mQcjAiKLgGI0i6WLWeURfFJvVA3Xy3T8K9An9qWXYDSQ8G6e-R2RFyOkVHd6GzaerD0a0NHXD3OoV4UmVXGZFGgvaOSWf35nbPeo584sZTw5mAI-qNQD_qJbsYX74lcbjYTO-q3XIm_o1sKHntNjcbuz8R5ItLTR1nOxRb3xbOwo1RgRBfztybvK_CtOVLXq83ulrPA_jFImcNxKT4zoXNlz98N5jvl_-9T0MRTB5i_PEYkwl82YIynOS4pGUsk9d80dEJUIdTCvJacYLvvesGTCnaSfzAcK4mk2yZzMRCIujonRvwfE-3A-xQbVtDNEIlTutJ4paicZFJZa0zLCKUSpOFBt_oLEoUpg0c4mmJWNAYP2V0YNOFo91v0ucf2RgbzdJ-9pjQBQetaBN3jw53YQA5C1pitEnlVQZlvxhGnRD618VzfeQocQp-FMfHmveZotn4OuBVY2jwn147JIRyvf71TryQ9K1Co2nLgiUORzmrM0erwlTFAHWPC1TRQyhMlFDB0-MC1YsoLHXeIVtSDcW4BEVq_2ro59yO5BKbijMQHj9UJ7Nz0UbTEUcShIvAAyNQRRmkeLS9CeAteu038kOl9iGaSWrW-ohn1pM1Fs2VKlSapdeaGYf06TSqXPw0MrFSRgN5LaDFFrGlPaNovfMcA2KHuc4rWn3UZSblPYIBbWnc5jQt5a49WAB5WgH98WYSMVmn4Q3L81JzWOiU5qFbhXRaKp7JH2CV5bo8JAB-flfbBIr6SeLoObu6uf55DkG_46khBd5-4HpMF4QevsHS1IKtRBtPQUW-9QJ9YsJkZbAw--3y1jDm-hWXG4HRuw9IJSwRB43KxGp1SETifIVilTiDbgvM6ml8aYlteGRZAPEh2aQM-l8DKluBSwR1v7jceIoo4WJAqXwPba050mepbHyuqjgcEieDNJPgVwjFct12m11nSFSHAxHT-U4RUgzuA6uSjbh_zc0_N70HMy2XW-bkyR_cBS0ZInNFmQuc1FxfK67Ssv0SOeXrBoMLBg5_B0JQSJZJSV1Gu-J87qPyuUPT_-wlHtqSoR7UAmQMU5V6Jd6NoZzD1xRVvlas8yfwx1c1itQDjBBB-akP89V_JcsfwXcIla5jTFd9RX9bxhNs4xdSzM-ed5suwgCap59JUhAZzM_2A9ZV_5jcfByi7gORrjV55kjPLPmXsBLTnWcHheTv4BNam-YovnGkEvqkgw0JLDIhqolSBmXhCnSnEikf_FkrJIjrgNP5VFgnyjkxduRbMasqfNCfJjkDnCnzBGl0RcIUvcXvJAEqwCsPf99Kn2wmjmcRiBssTH-h1iemxh0NKZzm36NZ4oQu7K7OS-TL6KsnU4i3XNi8fj5jUtqme1nDXQZTUDWQd3czCeehKxPAt-uJieklX245Oezp-Fx0CQX43FQH-28piyWZQfJyXy0 "Java sound class-diagram")

_Package `javax.sound` class-diagram:_

## 要点：格式、混合器和线条

要使用 `Java Sound API` 播放或捕获声音，您至少需要三样东西：`格式化音频数据`、`混音器`和`线路`

### 什么是`格式化音频数据`？

格式化的音频数据是指多种标准格式中的任何一种的声音。`Java Sound API` 区分 `数据格式` 和 `文件格式`。

#### 数据格式

`数据格式`告诉您如何解释一系列“原始”采样音频数据的字节，例如已经从声音文件中读取的样本，或者从麦克风输入中捕获的样本。例如，您可能需要知道有多少位构成一个样本（声音的最短瞬间的表示），同样您可能需要知道声音的采样率（样本应该以多快的速度相互跟随）。设置播放或捕获时，您指定正在捕获或播放的声音的数据格式。

在 `Java Sound API` 中，数据格式由一个`AudioFormat`对象表示，该对象包括以下属性：

-   编码技术，通常是脉冲编码调制 (`PCM`)
-   通道数（单声道 1 个，立体声 2 个等）
-   采样率（每秒采样数，每个通道）
-   每个样本的位数（每个通道）
-   帧率
-   帧大小（以字节为单位）
-   字节顺序（大端或小端）


`PCM` 是声音波形的一种编码。`Java Sound API` 包括两种使用线性量化幅度的 `PCM` 编码，以及`有符号`或`无符号` `整数值`。线性量化意味着存储在每个样本中的数字与该瞬间的原始声压成正比（任何失真除外），并且与该瞬间随着声音振动的扬声器或耳膜的位移成正比。例如，光盘使用`线性 PCM 编码`的声音。`Mu-law` 编码和 `a-law` 编码是常见的`非线性编码`，可提供更压缩的音频数据版本；这些编码通常用于电话或语音录音。非线性编码使用非线性函数将原始声音的振幅映射到存储的值。

`一帧`包含特定时间`所有通道`的数据。对于 `PCM` 编码的数据，帧只是所有通道中同时采样的集合，对于给定的瞬间，没有任何附加信息。在这种情况下，帧速率等于采样率，帧大小（以字节为单位）是通道数乘以以比特为单位的样本大小，再除以字节中的比特数。

对于其他类型的编码，一帧可能包含除样本之外的附加信息，并且帧速率可能与采样速率完全不同。例如，考虑 `MP3`（MPEG-1 音频第 3 层）编码，当前版本的 `Java Sound API` 中没有明确提及，但 `Java Sound API` 的实现或第三方可以支持它服务提供者。在 `MP3` 中，每一帧都包含一系列样本的一束压缩数据，而不仅仅是每个通道的一个样本。因为每一帧都封装了整个系列的样本，所以帧速率比采样速率要慢。该帧还包含一个标题。尽管有标头，但以字节为单位的帧大小小于同等数量的 `PCM` 帧的以字节为单位的大小。（毕竟 `MP3` 的目的是比 `PCM` 数据更紧凑。

#### 文件格式

`文件格式`指定了声音文件的结构，不仅包括文件中原始音频数据的格式，还包括文件中可以存储的其他信息。声音文件有多种标准类型，例如 `WAVE`（也称为 `WAV`，通常与 `PC` 相关联）、`AIFF`（通常与 `Macintoshes` 相关联）和 `AU`（通常与 `UNIX` 系统相关联）。不同类型的声音文件具有不同的结构。例如，它们可能在文件的“标题”中具有不同的数据排列方式。标头包含通常在文件的实际音频样本之前的描述性信息，尽管某些文件格式允许描述性和音频数据的连续“块”。标头包括用于将音频存储在声音文件中的数据格式规范。

在 `Java Sound API` 中，文件格式由一个`AudioFileFormat` 对象表示，该对象包含：

-   文件类型（`WAVE`、`AIFF` 等）
-   文件的长度（以`字节`为单位）
-   文件中包含的音频数据的长度（以`帧`为单位）
-   `AudioFormat` 对象，指定文件中包含的音频数据的数据格式


该类`AudioSystem`（在第 3 章“[访问音频系统资源](https://docs.oracle.com/javase/8/docs/technotes/guides/sound/programmer_guide/chapter3.html)”中进行了描述）提供了读取和写入不同文件格式的声音以及在不同数据格式之间进行转换的方法。一些方法允许您通过一种称为`AudioInputStream`. An `AudioInputStream`是泛型 Java `InputStream`类的子类，它封装了一系列可以顺序读取的字节。在其超类中， `AudioInputStream`该类添加了字节的音频数据格式（由`AudioFormat` 对象表示）的知识。通过将声音文件作为 `AudioInputStream`，您可以立即访问样本，而不必担心声音文件的结构（其标题、块等）。单个方法调用为您提供了有关数据格式和文件类型所需的所有信息。

### 什么是混音器？

许多用于声音的应用程序编程接口 (API) 都使用了音频 `设备` 的概念。设备通常是物理输入/输出设备的软件接口。例如，声音输入设备可能代表声卡的输入功能，包括麦克风输入、线路电平模拟输入，可能还有数字音频输入。

在 `Java Sound API` 中，设备由`Mixer`对象表示。混音器的目的是处理一个或多个音频输入流和一个或多个音频输出流。在典型情况下，它实际上将多个传入流混合在一起成为一个传出流。一个`Mixer`对象可以表示物理设备（例如声卡）的混音能力，它可能需要混合从各种输入进入计算机的声音，或者来自应用程序并进入输出的声音。

或者，一个 `Mixer`对象可以代表完全在软件中实现的混音功能，而不需要与物理设备的任何固有接口。

在 `Java Sound API` 中，声卡上的麦克风输入等组件本身并不被视为设备（即混音器），而是混音器的进出_端口。_端口通常提供进入或离开混音器的单个音频流（尽管流可以是多声道的，例如立体声）。混音器可能有几个这样的端口。例如，代表声卡输出功能的混音器可能会将多个音频流混合在一起，然后将混合后的信号发送到连接到混音器的任何或所有各种输出端口。这些输出端口可以是（例如）耳机插孔、内置扬声器或线路电平输出。

为了理解 `Java Sound API` 中混音器的概念，它有助于可视化物理混音控制台，例如在现场音乐会和录音室中使用的那些。（见下图。）

![物理调音台](http://seafile.mickey.wang:8665/d/c4f377ab9d49414f9661/files/?p=%2F%E7%89%A9%E7%90%86%E8%B0%83%E9%9F%B3%E5%8F%B0.gif&raw=1)

_物理混音台_

物理混音器具有“条”（也称为“切片”），每个表示单个音频信号进入混音器进行处理的路径。该条具有旋钮和其他控件，您可以通过它们控制该条中信号的音量和声像（在立体声图像中的位置）。此外，混音器可能有一条用于混响等效果的单独总线，该总线可以连接到内部或外部混响单元。每个条带都有一个电位器，用于控制条带的信号有多少进入混响混音。然后将混响（“湿”）混合与来自条带的“干”信号混合。物理混音器将此最终混音发送到输出总线，该总线通常会发送到磁带录音机（或基于磁盘的录音系统）和/或扬声器。

想象一下以立体声录制的现场音乐会。来自舞台上许多麦克风和电子仪器的电缆（或无线连接）插入到混音控制台的输入端。如图所示，每个输入都进入混音器的单独条带。音响工程师决定增益、声像和混响控制的设置。所有条带和混响单元的输出混合在一起进入两个通道。这两个通道连接到混音器的两个输出端，插入的电缆连接到立体声磁带录音机的输入端。取决于音乐的类型和大厅的大小，这两个通道可能还通过放大器发送到大厅的扬声器。

现在想象一个录音室，其中每个乐器或歌手都被录制到多轨录音机的单独轨道上。乐器和歌手全部录制完毕后，录音工程师会执行“混音”，将所有录音轨道组合成可以在光盘上分发的双通道（立体声）录音。在这种情况下，每个混音器条的输入不是麦克风，而是多轨录音的一个轨道。再一次，工程师可以使用条带上的控件来决定每个轨道的音量、声像和混响量。混音器的输出再次进入立体声录音机和立体声扬声器，就像现场音乐会的例子一样。

这两个示例说明了混音器的两种不同用途：捕获多个输入通道，将它们组合成更少的轨道，并保存混合，或者在将它们混合到更少的轨道时播放多个轨道。

在 `Java Sound API` 中，混音器可以类似地用于输入（捕获音频）或输出（播放音频）。在输入的情况下， 混音器获取用于混音的音频的_源是一个或多个输入端口。_混合器将捕获和混合的音频流发送到它的 _目标_，它是一个带有缓冲区的对象，应用程序可以从中检索这个混合的音频数据。在音频输出的情况下，情况正好相反。混音器的音频源是一个或多个对象，其中包含一个或多个应用程序将其声音数据写入其中的缓冲区；并且混音器的目标是一个或多个输出端口。

### 什么是线？

物理混音控制台的比喻对于理解 `Java Sound API` 的 `line` 概念也很有用。

线路是数字音频“管道”的一个元素，即用于将音频移入或移出系统的路径。通常这条线是进入或离开混音器的路径（尽管从技术上讲，混音器本身也是一种线）。

音频输入和输出端口是线路。这些类似于连接到物理调音台的麦克风和扬声器。另一种线路是数据路径，应用程序可以通过该路径从混音器获取输入音频或将输出音频发送到混音器。这些数据路径类似于连接到物理调音台的多轨录音机的轨道。

`Java Sound API` 中的行与物理混音器的行之间的一个区别是，流经 `Java Sound API` 中的行的音频数据可以是单声道或多声道（例如立体声）。相比之下，物理混音器的每个输入和输出通常是单个声音通道。为了从物理混音器获得两个或更多通道的输出，通常使用两个或更多物理输出（至少在模拟声音的情况下；数字输出插孔通常是多通道的）。在 `Java Sound API` 中，一行中的通道数由`AudioFormat`当前流经该行的数据的数量指定。

## 音频输出配置中的线路

现在让我们检查一些特定类型的线路和混音器。下图显示了一个简单的音频输出系统中不同类型的线，它可能是 `Java Sound API` 实现的一部分：

![音频输出线路的可能配置](http://seafile.mickey.wang:8665/d/c4f377ab9d49414f9661/files/?p=%2F%E9%9F%B3%E9%A2%91%E8%BE%93%E5%87%BA%E7%BA%BF%E8%B7%AF%E7%9A%84%E5%8F%AF%E8%83%BD%E9%85%8D%E7%BD%AE.gif&raw=1)

_音频输出线路的可能配置_

在此示例中，应用程序已访问音频输入混合器的一些可用输入：一个或多个 `剪辑` 和 `源数据线`。剪辑是混音器输入（一种线），您可以在播放之前将音频数据加载到其中；源数据线是接受实时音频数据流的混音器输入。应用程序将音频数据从声音文件预加载到剪辑中。然后它将其他音频数据推送到源数据线，一次一个缓冲区。混音器从所有这些线路读取数据，每条线路都可能有自己的混响、增益和声像控制，并将干音频信号与湿（混响）混音混合。混音器将其最终输出传送到一个或多个输出端口，例如扬声器、耳机插孔和线路输出插孔。

尽管在图中将各种线描绘为单独的矩形，但它们都归混合器“所有”，并且可以被视为混合器的组成部分。混响、增益和声相矩形表示混音器可以对流经线路的数据应用的处理控制（而不是线路）。

请注意，这只是 `API` 支持的可能混合器的一个示例。并非所有音频配置都具有图示的所有功能。单个源数据线可能不支持平移，混音器可能不实现混响，等等。

## 音频输入配置中的线路

一个简单的音频输入系统可能类似：

![音频输入线路的可能配置](http://seafile.mickey.wang:8665/d/c4f377ab9d49414f9661/files/?p=%2F%E9%9F%B3%E9%A2%91%E8%BE%93%E5%85%A5%E7%BA%BF%E8%B7%AF%E7%9A%84%E5%8F%AF%E8%83%BD%E9%85%8D%E7%BD%AE.gif&raw=1)

_音频输入线路的可能配置_

在这里，数据从一个或多个输入端口流入混音器，通常是麦克风或线路输入插孔。应用增益和声像，混频器通过混频器的目标数据线将捕获的数据传送到应用程序。目标数据线是混合器输出，包含流输入声音的混合。最简单的混频器只有一条目标数据线，但有些混频器可以同时将捕获的数据传送到多条目标数据线。

## 线路接口层次结构

现在我们已经看到了一些关于什么是线和混合器的功能图，让我们从稍微更程序化的角度来讨论它们。几种类型的线路由基本`Line` 接口的子接口定义。接口层次结构如下所示。

![线路接口层次结构](http://seafile.mickey.wang:8665/d/c4f377ab9d49414f9661/files/?p=%2F%E7%BA%BF%E8%B7%AF%E6%8E%A5%E5%8F%A3%E5%B1%82%E6%AC%A1%E7%BB%93%E6%9E%84.gif&raw=1)

_线路接口层次结构_

基本接口 `Line`描述了所有行共有的最小功能：

-   控件数据线和端口通常有一组控制，这些控制会影响通过该线的音频信号。`Java Sound API` 指定了控制类，这些控制类可用于处理声音的各个方面，例如：增益（以分贝为单位影响信号的音量）、声像（影响声音的左右定位、混响（将混响添加到声音模拟不同类型的房间声学）和采样率（影响播放速率和声音的音高）。
-   打开或关闭状态 一条线路的成功开通保证了资源已经分配给线路。混音器的行数有限，因此在某些时候，多个应用程序（或同一个）可能会争夺混音器的行数。关闭一条线表示该线使用的任何资源现在都可以释放。
-   活动一条线在打开或关闭时会生成事件。的子接口`Line` 可以引入其他类型的事件。当一条线路生成一个事件时，该事件将发送到所有已注册“侦听”该线路上的事件的对象。应用程序可以创建这些对象，注册它们以侦听线路事件，并根据需要对事件做出反应。


我们现在将检查接口的子`Line` 接口。

`Ports`是用于将音频输入或输出到音频设备或从音频设备输出的简单线路。如前所述，一些常见的端口类型是麦克风、线路输入、CD-ROM 驱动器、扬声器、耳机和线路输出。

当然，`Mixer` 接口代表一个混音器，正如我们所见，它代表硬件或软件设备。该 `Mixer`接口提供了获取混音器线路的方法。其中包括将音频馈送到混音器的源线和混音器将其混合音频传送到的目标线。对于音频输入混音器，源线是输入端口，例如麦克风输入，目标线是 `TargetDataLines`（如下所述），它们将音频传递给应用程序。另一方面，对于音频输出混音器，源线是`Clips`或 `SourceDataLines`（如下所述），应用程序向其馈送音频数据，而目标线是输出端口，例如扬声器。

A`Mixer`被定义为具有一个或多个源行和一个或多个目标行。请注意，此定义意味着混合器不需要实际混合数据；它可能只有一个源代码行。`Mixer`API 旨在涵盖各种设备，但典型情况下支持混合。

`Mixer` 接口支持同步；也就是说，您可以指定将混合器的两条或多条线路视为同步组。然后，您可以通过向组中的任何线路发送一条消息来启动、停止或关闭所有这些数据线路，而不必单独控制每条线路。使用支持此功能的混音器，您可以在线路之间获得样本精确的同步。

通用 `Line`接口不提供开始和停止播放或录制的方法。为此，您需要一条数据线。除了 a 之外，该 `DataLine`接口还提供以下与媒体相关的附加功能`Line`：

-   音频格式每条数据线都有与其数据流相关的音频格式。
-   媒体位置数据行可以报告其在媒体中的当前位置，以样本帧表示。这表示自数据线打开以来由数据线捕获或渲染的样本帧数。
-   缓冲区大小这是数据线内部缓冲区的大小（以字节为单位）。对于源数据线，内部缓冲区是可以写入数据的缓冲区，而对于目标数据线，内部缓冲区是可以从中读取数据的缓冲区。
-   电平（音频信号的当前幅度）
-   开始和停止播放或捕捉
-   暂停和恢复播放或捕捉
-   刷新（从队列中丢弃未处理的数据）
-   Drain（阻塞直到所有未处理的数据都从队列中排出，并且数据行的缓冲区变空）
-   活动状态如果数据线参与到混音器或从混音器主动呈现或捕获音频数据，则该数据线被认为是活跃的。
-   活动 `START``STOP`当从或到数据线的主动呈现或捕获数据开始或停止时 ，会产生事件。


A `TargetDataLine`从混音器接收音频数据。通常，混音器从麦克风等端口捕获音频数据；它可能会在将数据放入目标数据线的缓冲区之前处理或混合此捕获的音频。该 `TargetDataLine`接口提供了从目标数据线的缓冲区中读取数据以及确定当前有多少数据可供读取的方法。

A `SourceDataLine`接收用于播放的音频数据。它提供了将数据写入源数据行的缓冲区以进行回放的方法，以及确定该行准备接收多少数据而不阻塞的方法。

A`Clip`是一条数据线，音频数据可以在播放之前加载到该数据线中。由于数据是预先加载的而不是流式传输的，因此剪辑的持续时间在播放之前是已知的，您可以选择媒体中的任何起始位置。剪辑可以循环播放，这意味着在播放时，两个指定循环点之间的所有数据将重复指定次数或无限次。

## 示例代码

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import javax.sound.sampled.*;
import java.io.ByteArrayInputStream;
import java.io.IOException;
import java.nio.ByteBuffer;
import java.nio.ByteOrder;
import java.util.Arrays;

public class AudioExample {
    private static final Logger LOGGER = LoggerFactory.getLogger(AudioExample.class);
    /**
     * 定义音频播放格式 16k采样率 24位 单声道 有符号 大端编码
     */
    private static final AudioFormat audioFormat = new AudioFormat(16000.0f, 24, 1, true, true);
    /**
     * 定义音频输出线路
     */
    private static SourceDataLine sourceDataLine;

    public static void main(String[] args) {
        printAudioFormats();
        // 生成10秒钟的单频正弦模拟信号
        double[] audio = GenerationUtils.generateRandomSin(16000 * 10, 16000, 1, 0, 65, 131, 262, 523, 1046, 2089, 4058);
        // 计算下数据组中的最大值和最小值，用于将模拟信号归一
        double max = Arrays.stream(audio).max().getAsDouble();
        double min = Arrays.stream(audio).min().getAsDouble();

        try {
            openSoundLine();
            playSound(audio, max, min);
            closeSoundLine();
        } catch (LineUnavailableException | IOException e) {
            e.printStackTrace();
        }
    }

    /**
     * 关闭音频输出线路缓存
     */
    private static void closeSoundLine() {
        sourceDataLine.drain();
        sourceDataLine.stop();
        sourceDataLine.close();
    }

    /**
     * 处理并播放提供的 double 模拟信号
     *
     * @param audio double 模拟信号
     * @param max   模拟信号中的最大阈值
     * @param min   模拟信号中的最小阈值
     * @throws IOException
     */
    private static void playSound(double[] audio, double max, double min) throws IOException {
        // 模拟信号填充为音频字节数据
        byte[] soundDataLineBytes = fillDoubleSignal2SoundDataLineBytes(audioFormat, audio, max, min);
        // 将音频字节数据转换为音频输入流
        AudioInputStream audioInputStream = new AudioInputStream(new ByteArrayInputStream(soundDataLineBytes), audioFormat, soundDataLineBytes.length);
        // 将音频输入流写入到音频输出线路中，进行播放
        long totalToRead = audioInputStream.getFrameLength();
        int total = 0;
        byte[] data = new byte[sourceDataLine.getBufferSize()];
        while (total %3C totalToRead) {
            int read = audioInputStream.read(data, 0, data.length);
            if (read <= -1) break;
            total += read;
            sourceDataLine.write(data, 0, data.length);
        }
    }

    /**
     * 以指定格式打开音频输出线路，并开始数据IO，<b%3E调用完此方法后，必须要开始向 SourceDataLine 中写入音频数据</b>
     *
     * @throws LineUnavailableException 如果由于资源限制无法打开该行
     * @throws IllegalArgumentException 如果format未完全指定或无效
     * @throws IllegalStateException    如果线路已经打开
     * @throws SecurityException        如果由于安全限制而无法打开该行
     */
    public static void openSoundLine() throws LineUnavailableException {
        // 获取支持指定的音频格式的输出线路
        LOGGER.info("audioFormat: {}", audioFormat.toString());
        sourceDataLine = AudioSystem.getSourceDataLine(audioFormat);
        sourceDataLine.open(audioFormat);
        sourceDataLine.start();
    }

    /**
     * 将double的模拟信号按照提供的格式填充到音频输出线路中
     *
     * @param format    音频格式
     * @param source    double 模拟信号
     * @param doubleMax 模拟信号最大值
     * @param doubleMin 模拟信号最小值
     * @return 输出音频字节数据
     */
    public static byte[] fillDoubleSignal2SoundDataLineBytes(AudioFormat format, double[] source, double doubleMax, double doubleMin) {
        // 最大值、最小值 绝对值中的最大值
        double max = Math.max(Math.abs(doubleMax), Math.abs(doubleMin));
        // 字节缓冲流
        int bufferSize = source.length * format.getChannels() * format.getFrameSize();
        ByteBuffer byteBuffer = ByteBuffer.allocate(bufferSize);
        if (format.isBigEndian()) {
            byteBuffer.order(ByteOrder.BIG_ENDIAN);
        } else {
            byteBuffer.order(ByteOrder.LITTLE_ENDIAN);
        }
        if (format.getSampleSizeInBits() == 24) {
            for (double v : source) {
                // 归一 double value.
                double valMax1 = v / max;
                // 如果 double 计算完仍然超过 1，强制设置为 1，最小值同理为 -1.
                if (valMax1 > 1) {
                    valMax1 = 1d;
                } else if (valMax1 < -1) {
                    valMax1 = -1d;
                }
                // 将归一后的 double 数据转换为 3 个字节的 int 数据
                int value = (int) (valMax1 * (Math.pow(2, 23) - 1));
                if (byteBuffer.order() == ByteOrder.BIG_ENDIAN) {
                    byteBuffer.put(new byte[]{(byte) (value >> 16), (byte) (value >> 8), (byte) value});
                } else {
                    byteBuffer.put(new byte[]{(byte) value, (byte) (value >> 8), (byte) (value >> 16)});
                }
            }
        } else if (format.getSampleSizeInBits() == 16) {
            for (double v : source) {
                // 归一 double value.
                double valMax1 = v / max;
                // 如果 double 计算完仍然超过 1，强制设置为 1，最小值同理为 -1.
                if (valMax1 > 1) {
                    valMax1 = 1d;
                } else if (valMax1 < -1) {
                    valMax1 = -1d;
                }
                // 将归一后的 double 数据转换为 2 个字节的 int 数据
                short value = (short) (valMax1 * Short.MAX_VALUE);
                if (byteBuffer.order() == ByteOrder.BIG_ENDIAN) {
                    byteBuffer.put(new byte[]{(byte) (value >> 8), (byte) value});
                } else {
                    byteBuffer.put(new byte[]{(byte) value, (byte) (value >> 8)});
                }
            }
        } else if (format.getSampleSizeInBits() == 8) {
            for (double v : source) {
                // 归一 double value.
                double valMax1 = v / max;
                // 如果 double 计算完仍然超过 1，强制设置为 1，最小值同理为 -1.
                if (valMax1 > 1) {
                    valMax1 = 1d;
                } else if (valMax1 < -1) {
                    valMax1 = -1d;
                }
                byteBuffer.put((byte) (valMax1 * Byte.MAX_VALUE));
            }
        }
        return byteBuffer.array();
    }

    /**
     * 打印硬件支持的音频输出格式
     */
    public static void printAudioFormats() {
        // 测试声音格式
        Mixer.Info[] mixerInfoArr = AudioSystem.getMixerInfo();
        for (Mixer.Info mixerInfo : mixerInfoArr) {
            Mixer mixer = AudioSystem.getMixer(mixerInfo);
            LOGGER.info("Mixer info: {}, Mixer class: {}", mixer.getMixerInfo(), mixer.getClass().getName());

            Line.Info[] sourceLineInfoArr = mixer.getSourceLineInfo();
            for (Line.Info info : sourceLineInfoArr) {
                boolean isDataLineClass = Arrays.asList(info.getLineClass().getInterfaces()).contains(DataLine.class);
                if (isDataLineClass) {
                    LOGGER.info("    Line info: {}, class: {}", info, info.getLineClass().getName());
                    AudioFormat[] formats = ((DataLine.Info) info).getFormats();
                    LOGGER.info("        -------------------- audio formats -----------------------");
                    for (AudioFormat format : formats) {
                        LOGGER.info("        " + format);
                    }
                }
            }
            LOGGER.info("======================================================");
        }
    }
}
```

## 备注

1.  直接音频混音器始终是 Windows 上的默认设置。如果启用了 Solaris 音频混音器，它们是 Solaris 上的默认设置（请参阅混音器的 Solaris 手册页）。在 Linux 上，只有当有支持混合的设备时，它们才是默认设置。
2.  因为它们是“直接的”，所以直接音频混音器不支持`SAMPLE_RATE`控制。
3.  可以通过 `sound.properties`文件选择默认混音器。

---
