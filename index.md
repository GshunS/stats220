# Introduce to my meme
## Three programming language icons

1. **My meme**

    - ![](myMeme.png)

2. **Why to create this meme?**
    - I learnt these 3 programming languages at stage 1 and 2.
    - I want to create an image for them.
3. **How was this meme created?**
    - This meme is made of 9 different images
    - Each promgramming language image contains 3 sub-images
    - The background color(2 images with different colors) and the language icon
    - Using ```image_composite()``` to combine the backgruond and the icon image on a specific position.
    - Finally, I uesd ```image_append()``` to put them together.
4. ***Fun stuff***
    - What is the relationship between background colors and icon colors?
5. **Extra**
    - [About R](https://www.r-project.org/about.html)
    - [About Python](https://www.python.org/about/)
    - [About Java](https://www.java.com/en/download/help/whatis_java.html)
    - Below is a image from online
    - ![](https://www.seasiainfotech.com/blog/wp-content/uploads/2018/07/javapython_Blog.jpg)
6. **The r code for my meme**

```r
library(magick)

# two background images for R
r_top_text <- image_blank(width = 200,
                          height = 100,
                          color = "#165CAA")


r_bottom_text <- image_blank(width = 200,
                             height = 100,
                             color = "#919198")
                             
# put these two background images together
r_text <- c(r_top_text, r_bottom_text) %>%
  image_append(stack = TRUE) %>%
  image_annotate(text = "R",
                 size = 30,
                 gravity = "northwest",
                 color = "#ffffff")

# get the r icon from online
r_icon <- image_read("https://www.r-project.org/Rlogo.png")

# combine the icon with the background image
r_overlap_image <- image_composite(r_text,
                                   r_icon,
                                   offset = "+0+25")

# two background images for python
python_top_text <- image_blank(width = 200,
                               height = 100,
                               color = "#FFD43B")

python_bottom_text <- image_blank(width = 200,
                                  height = 100,
                                  color = "#306998")

# put these two background images together
python_text <- c(python_top_text, python_bottom_text) %>%
  image_append(stack = TRUE) %>%
  image_annotate(text = "Python",
                 size = 30,
                 gravity = "northwest",
                 color = "#ffffff")

# get the python icon from online
python_icon <- image_read("https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/1200px-Python-logo-notext.svg.png")

# change the size of the icon
python_smaller_icon <- python_icon %>%
  image_scale(150)

# combine the icon with the background image
python_overlap_image <- image_composite(python_text,
                                        python_smaller_icon,
                                        offset = "+25+25")

# two background images for java
java_top_text <- image_blank(width = 200,
                             height = 100,
                             color = "#5382a1")


java_bottom_text <- image_blank(width = 200,
                                height = 100,
                                color = "#f89820")

# put these two background images together
java_text <- c(java_top_text, java_bottom_text) %>%
  image_append(stack = TRUE) %>%
  image_annotate(text = "Java",
                 size = 30,
                 gravity = "northwest",
                 color = "#ffffff")

# get the java icon from online
java_icon <- image_read("https://brandlogos.net/wp-content/uploads/2021/11/java-logo.png")

# change its size
java_smaller_icon <- java_icon %>%
  image_scale(200)
  
# combine the icon with the backgroud image on a specific position
java_overlap_image <- image_composite(java_text,
                                      java_smaller_icon,
                                      offset = "+0+0")

# put all three images together
final_image <- c(r_overlap_image, python_overlap_image, java_overlap_image) %>%
  image_append()
final_image

# save it on the disk.
image_write(final_image, "myMeme.png")
```
