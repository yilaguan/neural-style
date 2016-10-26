# neural-style

An implementation of [neural style][paper] in TensorFlow.

This implementation is a lot simpler than a lot of the other ones out there,
thanks to TensorFlow's really nice API and [automatic differentiation][ad].

TensorFlow doesn't support [L-BFGS][l-bfgs] (which is what the original authors
used), so we use [Adam][adam]. This may require a little bit more
hyperparameter tuning to get nice results.

TensorFlow seems to be [slower][tensorflow-benchmarks] than a lot of the other
deep learning frameworks out there. I'm sure this implementation could be
improved, but it would probably take improvements in TensorFlow itself as well
to get it to operate at the same speed as other implementations. As of now, it
seems to be around 3x slower than implementations using Torch.

##Install
(1)You need install some requirements before you install tensorflow.
`sudo apt-get isntall python-pip python-dev python-setuptools build-essential
sudo pip install --upgrade pip
sudo pip install --upgrade virtualenv`

(2)after than you can check whether pip is upgrade:
`pip --version`

pip 8.1.1 from /usr/local/lib/python2.7/dist-packages (python 2.7)

(3)And you need to install tensorflow in your ubuntu, the cammand as below:
`sudo pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.10.0-cp27-none-linux_x86_64.whl`

Of course , you can use the last version of tensorflow.And as above, the tensorflow CPU only and ubuntu 64-bit

(4)install neural-style
`git clone https://github.com/yilaguan/neural-style.git`

(5)please download [net] in the root of neural-style





## Running

`python neural_style.py --content <content file> --styles <style file> --output <output file>`

(run `python neural_style.py --help` to see a list of all options)

## Example 1

Running it for 500-2000 iterations seems to produce nice results. With certain
images or output sizes, you might need some hyperparameter tuning (especially
`--content-weight`, `--style-weight`, and `--learning-rate`).

The following example was run for 1000 iterations to produce the result (with
default parameters):

![output](examples/1-output.jpg)

These were the input images used (me sleeping at a hackathon and Starry Night):

![input-content](examples/1-content.jpg)

![input-style](examples/1-style.jpg)

## Example 2

The following example demonstrates style blending, and was run for 1000
iterations to produce the result (with style blend weight parameters 0.8 and
0.2):

![output](examples/2-output.jpg)

The content input image was a picture of the Stata Center at MIT:

![input-content](examples/2-content.jpg)

The style input images were Picasso's "Dora Maar" and Starry Night, with the
Picasso image having a style blend weight of 0.8 and Starry Night having a
style blend weight of 0.2:

![input-style](examples/2-style1.jpg)
![input-style](examples/2-style2.jpg)

## Requirements

* [TensorFlow](https://www.tensorflow.org/versions/master/get_started/os_setup.html#download-and-setup)
* [NumPy](https://github.com/numpy/numpy/blob/master/INSTALL.rst.txt)
* [SciPy](https://github.com/scipy/scipy/blob/master/INSTALL.rst.txt)
* [Pillow](http://pillow.readthedocs.io/en/3.3.x/installation.html#installation)
* [Pre-trained VGG network][net] (MD5 `8ee3263992981a1d26e73b3ca028a123`) - put it in the top level of this repository

## License

Copyright (c) 2015-2016 Anish Athalye. Released under GPLv3. See
[LICENSE.txt][license] for details.

[net]: http://www.vlfeat.org/matconvnet/models/beta16/imagenet-vgg-verydeep-19.mat
[paper]: http://arxiv.org/pdf/1508.06576v2.pdf
[l-bfgs]: https://en.wikipedia.org/wiki/Limited-memory_BFGS
[adam]: http://arxiv.org/abs/1412.6980
[ad]: https://en.wikipedia.org/wiki/Automatic_differentiation
[tensorflow-benchmarks]: https://github.com/soumith/convnet-benchmarks
[license]: LICENSE.txt
