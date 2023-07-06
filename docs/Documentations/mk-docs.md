For full documentation visit [mkdocs.org](https://www.mkdocs.org). <br>
This is the pheasants documentation [link](https://pheasant.daizutabi.net/).

    For full documentation visit [mkdocs.org](https://www.mkdocs.org). <br>
    This is the pheasants documentation [link](https://pheasant.daizutabi.net/).

##   This command will give you line break
------------
    ------------

## Commands
    `mkdocs new [dir-name]` - Create a **new** project.
* `mkdocs new [dir-name]` - Create a **new** project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.
* `mkdocs gh-deploy` - Deploy to the server
* also this gives you bullet points

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

Also identation will give you space to write code
    
    like this
    a very important
    message
or
```python
def fn():
    pass
```
    ```python
    def fn():
        pass
    ```



#Table Adding a markdown table
First Header | Second Header | Third Header
------------ | ------------- | ------------
Content Cell | Content Cell  | Content Cell
Content Cell | Content Cell  | Content Cell


    #Table Adding a markdown table
    First Header | Second Header | Third Header
    ------------ | ------------- | ------------
    Content Cell | Content Cell  | Content Cell
    Content Cell | Content Cell  | Content Cell



<br>
#Fig Linking a video {#hylink#}
<p align="center">
<iframe height="480" width="900" allow="fullscreen;"
 src="https://www.youtube.com/embed/aNLIWvk2CRY">
</iframe>
</p>



    #Fig Linking a video {#hylink#}
    <p align="center">
    <iframe height="480" width="900" allow="fullscreen;"
    src="https://www.youtube.com/embed/aNLIWvk2CRY">
    </iframe>
    </p>



#Figure A Matplotlib figure generated from a python code
```python
import matplotlib.pyplot as plt 
plt.plot([2, 4])
```

Linking something back, {#hylink#}

#Fig Adding immages
<img src="../img/2temp.jpg"
	 style="object-fit:scale-down;
            object-position: center;
            width:100%;
            height:300px;"/>


#Fig Adding two figures with a blank line
<img src="../img/2temp.jpg"
	 style="object-fit:scale-down; object-position: center; width:100%;
            height:300px;"/>
<img src="../img/2temp.jpg"
	 style="object-fit:scale-down; object-position: center; width:100%;
            height:300px;"/>