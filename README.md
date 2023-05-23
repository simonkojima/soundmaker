# soundmaker

# Required Packeges
numpy  
pysoundfile  

# Example
```python
import soundmaker

# create sound instance
sm = soundmaker.sound(44100)

# generate sine tone.
data, t = sm.gen_sine(100, 1) # 100Hz, 1seconds
data, w = sm.apply_window(0.1) # apply tukey window function for fadein/fadeout
rms = sm.compute_rms() # compute root mean square
print(rms)

sm.change_db(30) # change db level
rms = sm.compute_rms()
print(rms)
```

```python

# get loudness curve for 40phon
spl, freq = soundmaker.loudness(40)
print(freq)
print(spl)


freqs = [100, 1000, 2000]

sounds = list()
for idx, freq in enumerate(freqs):
    sounds.append(soundmaker.sound(44100))
    sounds[idx].gen_sine(freq, 1)

# equalize loudness level with 50 phone
soundmaker.equalize_loudness(sounds, 50)

# normalize the sound level. 
soundmaker.normalize(sounds, max_peak = 1.0)

```