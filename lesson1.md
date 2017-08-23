## Lesson 1

Weaknesses:
 Math centric (Just do the code)
 Elementitis (Too seperated)
 "Good enough results" (Let's get state of the art results)

Book rec: [Make Learning Whole by David Perkins](https://www.amazon.ca/Making-Learning-Whole-Principles-Transform/dp/0470633719)

Intro to Jupyter
Shift+Tab to get documentation!

TA Note: Don't forget to conda environments

8 hours a week of work

Notebook repo: https://github.com/fastai/courses.git

? Where is the wiki: http://wiki.fast.ai/index.php/Main_Page
Forums: https://github.com/fastai/courses.git

Interesting advice: Try something for half an hour, then ask someone

AWS and Jupyter

---

## Why Deep Learning?
- Infinitely Flexible Function (Universal approximation function)
- All-purpose parameter fitting (Gradient descent)
- Fast and scalable (GPUs)

Need to use Nvidia through P2 instances
OVH is crazy cheap
There's a script for this

Suggests the CLI

Lots of fun examples

AWS Setup: https://www.youtube.com/watch?v=8rjRfW4JM2I
`sudo rm .bash_history` Don't forget this!
`dl_course` is the password

`sudo apt install awscli`

Will be starting with Cats and Dogs

Oh wow...Tmux rules

Permanent aws-aliases = `cat aws-alias.sh >> ~/.bashrc`

This is where the data lives now `http://files.fast.ai/data/`

Download all files:
 `wget -r --no-parent http://files.fast.ai/data/`

Unzipping:
`sudo apt install unzip`
`unzip dogscats.zip`

Run things on samples!

ImageNet is too carefully curated
Networks will share the biases of their data
VGG was the last really simple architecture to win ImageNet

VGG16 - Keras - Theano - CUDA-cuDNN

We look at a few images at a time (this is called mini-batching)


Oh wow, a Kaggle CLI!

pip install kaggle-cli
kg config -g -u `username` -p `password` -c `competition`
password shouldn't have ! in it (seems like a big oversight