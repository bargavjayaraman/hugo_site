---
title: 'Xbox One X HDD Loading Test'
subtitle: 'Is internal HDD of Xbox One X faster than external HDD?'
summary: A hypothesis testing approach to evaluate the Xbox One X HDD.
authors:
- admin
tags:
- Gaming
- Hypothesis Testing

categories: []
date: "2019-12-08T00:00:00Z"
lastmod: "2019-12-08T00:00:00Z"
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 1
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---


With the advent of 4K UHD and HDR games, it is not uncommon nowadays that your Xbox One X stock HDD of 1 TB gets filled quickly with just a handful of games. And my case is no different, within one year of purchasing the console, I already ran out of hard disk space. So I did what any gamer would do in my situation; I ordered a [4TB external hard drive](https://www.bestbuy.com/site/seagate-expansion-4tb-external-usb-3-0-portable-hard-drive-black/4820200.p?skuId=4820200) [Yay!]. Now that I planned to transfer some games from my internal HDD to the external HDD, curiosity plagued the researcher in me! Is the internal HDD faster at loading games than the external HDD? Or is it the other way around? Both schools of thoughts have their own reasoning. On one hand internal HDD is, well, internal. It uses [SATA 3](https://en.wikipedia.org/wiki/Serial_ATA) connection supporting upto 600 MB/s of bandwidth. On the other hand, external HDD uses [USB 3.0](https://en.wikipedia.org/wiki/USB_3.0) connection supporting upto 625 MB/s of bandwidth. Both the hard drives have rotation speed of 5400 RPM, so it is still an apple to apple comparison. 

Note that this idea of comparing the loading speeds of internal and external HDDs is not novel. There are already many videos and blogs on this topic - be it for computers or consoles. What's new in this blog is to evaluate this in a [*cough*] scientific way - using hypothesis testing. Let's get into a [somewhat] scientific evaluation!

## Hypothesis testing on game loading task
Game loading time is measured (in *mm:ss*) as the time taken to launch the game - from clicking on the game till the point where the player gets the control of the playable character, as shown in this [video](https://www.youtube.com/watch?v=MQ_pDLMI650). I recorded the loading time for 10 AAA title games, with the exception of Forza Motorsport 7, where I recorded till the point where the main menu appears. Launching a race involves lot of manual selection process, which could add more variability in recording time.

The null hypothesis is $H_0:$ *"game loading time of internal HDD is same as that of external HDD"*, and the alternate hypothesis is $H_a:$ *"game loading time of internal HDD is not same as that of external HDD"*.

## Experimental observations
The game loading times are reported in the table below.
<table>
    <tr>
        <th>Game Title</th> <th>Internal HDD Time <br>(<i>mm:ss</i>)</th> <th>External HDD Time <br>(<i>mm:ss</i>)</th>
    </tr>
    <tr>
        <td>Assassin's Creed Origins</td> <td>01:48.50</td> <td>01:51.05</td>
    </tr>
    <tr>
        <td>Tomb Raider</td> <td>00:50.95</td> <td>00:41.78</td>
    </tr>
    <tr>
        <td>Rise of Tomb Raider</td> <td>02:32.14</td> <td>02:15.54</td>
    </tr>
    <tr>
        <td>Shadow of Tomb Raider</td> <td>01:36.63</td> <td>01:24.30</td>
    </tr>
    <tr>
        <td>Halo Master Chief Collection</td> <td>00:57.29</td> <td>00:46.89</td>
    </tr>
    <tr>
        <td>Batman: Arkham Assylum</td> <td>01:09.88</td> <td>01:03.00</td>
    </tr>
    <tr>
        <td>Batman: Arkham City</td> <td>01:13.94</td> <td>01:12.30</td>
    </tr>
    <tr>
        <td>Batman: Arkham Knight</td> <td>01:39.64</td> <td>01:36.14</td>
    </tr>
    <tr>
        <td>Forza Horizon 4</td> <td>02:33.74</td> <td>02:04.31</td>
    </tr>
    <tr>
        <td>Forza Motorsport 7</td> <td>01:00.00</td> <td>00:50.69</td>
    </tr>
</table>

Since there is a one-to-one correspondence of each game, we can use [paired sample T-test](https://www.statisticshowto.datasciencecentral.com/probability-and-statistics/t-test/). 
We can calculate the $t$-value for the paired sample T-test using a simple formula:

$t-value = \frac{D_1 / N}{\sqrt{\frac{D_2 - D_1^2 / N}{N(N-1)}}}$

Where $N$ is the total number of games ($N = 10$), $D_1$ is the total difference between loading times of internal and external HDDs ($D_1 = 96.71$) and $D_2$ is the total squared difference between loading times of internal and external HDDs ($D_2 = 1641.4153$). The calculated $t$-value comes out to be 3.4526 which is greater than the threshold $t$-value of 3.250 for a significance threshold of 0.005. Hence we can reject the null hypothesis $H_0$ with 99.5% confidence and conclude that [*my*] external HDD is faster than the internal HDD of [*my*] Xbox One X. 


## Disclaimer on the validity of results
The above results are for a single loading of each game, and the loading time might vary by a few seconds across multiple runs. Ideally, average loading time should be used for such experiments. However, it should be noted that if the same game is loaded multiple times, the consequent loading will be faster due to *memory caching*. To avoid caching, games should be loaded in an alternative fashion. Finally, it is important to put a disclaimer that the reported results are for my hardware, and these results *might* vary for others. So take it with a grain of salt! :P


## Conclusion
Keeping the above disclaimer in mind, I conclude that my external HDD loads games faster than the stock HDD of my Xbox One X. This benefit might be attributed to the extra 25 MB/s bandwidth of USB 3.0 interface used by the external HDD.
