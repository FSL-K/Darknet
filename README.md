This repo is a simplified darknet version, only cifar relevant C program documents are kept, you can find the original implementation here (https://github.com/pjreddie/darknet).

Install Darknet:

Go into the ```darknet``` directory and type
```
make
```

If this works you should see a whole bunch of compiling information fly by:
```
mkdir -p obj
gcc -I/usr/local/cuda/include/  -Wall -Wfatal-errors  -Ofast....
gcc -I/usr/local/cuda/include/  -Wall -Wfatal-errors  -Ofast....
gcc -I/usr/local/cuda/include/  -Wall -Wfatal-errors  -Ofast....
.....
gcc -I/usr/local/cuda/include/  -Wall -Wfatal-errors  -Ofast -lm....
```

run darknet
```
./darknet
```
You should get the output:
```
usage: ./darknet <function>
```

Get Cifar Dataset:

Go into the ```data/``` directory and run:
```
wget https://pjreddie.com/media/files/cifar.tgz
tar xzf cifar.tgz
```

Config Files:

The cifar dataset config file is kept in the ```cfg/```  directory called ```cfg/cifar.data```, and a network config file is called ```cfg/cifar_small.cfg```.

### Getting started

Run the training code:
``` 
./darknet classifier train cfg/cifar.data cfg/cifar_small.cfg
``` 
And watch it go!
You are just telling Darknet you want to train a classifier using the following data and network cfg files. On a CPU training may take an hour or more, even for this small network.

Restarting Training:

If you stop training you can always restart it using one of the model checkpoints it saves along the way:
``` 
./darknet classifier train cfg/cifar.data cfg/cifar_small.cfg backup/cifar_small.backup
```

Validate The Model:

Now we have to see how well our model is doing. We can calculate top-1 and top-2 validation accuracy using the valid command. We can run validation on a backup, the final weights file, or any saved epoch weight file:
``` 
./darknet classifier valid cfg/cifar.data cfg/cifar_small.cfg backup/cifar_small.backup
``` 
You will see a bunch of scrolling numbers that tell you your accuracy.

# Citation

If this repo is helpful for your research, please consider citing the paper:

```BibTeX
@misc{https://doi.org/10.48550/arxiv.2207.02696,
  doi = {10.48550/ARXIV.2207.02696},
  url = {https://arxiv.org/abs/2207.02696},
  author = {Wang, Chien-Yao and Bochkovskiy, Alexey and Liao, Hong-Yuan Mark},
  keywords = {Computer Vision and Pattern Recognition (cs.CV), FOS: Computer and information sciences, FOS: Computer and information sciences},
  title = {YOLOv7: Trainable bag-of-freebies sets new state-of-the-art for real-time object detectors},
  publisher = {arXiv},
  year = {2022}, 
  copyright = {arXiv.org perpetual, non-exclusive license}
}
```

```BibTeX
@@misc{bochkovskiy2020yolov4,
      title={YOLOv4: Optimal Speed and Accuracy of Object Detection}, 
      author={Alexey Bochkovskiy and Chien-Yao Wang and Hong-Yuan Mark Liao},
      year={2020},
      eprint={2004.10934},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

```BibTeX
@@InProceedings{Wang_2021_CVPR,
    author    = {Wang, Chien-Yao and Bochkovskiy, Alexey and Liao, Hong-Yuan Mark},
    title     = {{Scaled-YOLOv4}: Scaling Cross Stage Partial Network},
    booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
    month     = {June},
    year      = {2021},
    pages     = {13029-13038}
}
```