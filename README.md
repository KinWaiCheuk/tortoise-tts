# TorToiSe

## Setup

### Python version
It was tested on `Python 3.9.16`.

### Dependencies
It is better to first create a virtual envirnoment using conda.

```shell
conda create -n tortoise python=3.9
```

To install all dependencies:

```shell
pip install -r requirements.txt
```

After that, go inside the tortoise folder and do

```shell
pip install .
```


### Generate from a string

```shell
python tortoise/do_tts.py --text "I'm going to speak this" --voice random --candidates 3 --preset high_quality --seed 101
```

### Generate from a file


```shell
 python tortoise/read.py --textfile text.txt --voice random --candidates 3 --preset high_quality --seed 101

```

This will break up the textfile into sentences, and then convert them to speech one at a time. It will output a series
of spoken clips as they are generated. Once all the clips are generated, it will combine them into a single file and
output that as well.

Sometimes Tortoise screws up an output. You can re-generate any bad clips by re-running `read.py` with the --regenerate
argument.

## Computer setup and speed
Below are the time required to generate 3 sentences of audio around 10s long.
Here's the content of the `text.txt`:

```txt
Hello everyone. This is a test file.

I have fixed the slowness by installing older packages.

The audio generation is much faster with a G P U now.
```

### Intel i9-13900 + RTX4070
__0:54__ for "Generating autoregressive samples..."

__0:03__ for "Computing best candidates using CLVP"

__0:55__ for "Transforming autoregressive outputs into audio.."
