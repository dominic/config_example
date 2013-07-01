# config_example

An example for keeping secrets out of your code

### Using secrets

In the example above, our program `example.py` relies on two environment variables - `MY_SECRET` and `MY_OTHER_SECRET`

If you try to run `example.py` without setting up the environment correctly, you'll see the following error:

```sh
$ python example.py 
Traceback (most recent call last):
  File "example.py", line 6, in <module>
    print os.environ['MY_SECRET']
  File "/usr/local/Cellar/python/2.7.5/Frameworks/Python.framework/Versions/2.7/lib/python2.7/UserDict.py", line 23, in __getitem__
    raise KeyError(key)
KeyError: 'MY_SECRET'
```

### Set up your config

1. Create a new file to hold your environment variables - I like `.env` or just plain `env`
2. Add your environment file to your `.gitignore` file
3. Add your configuration to your environment file in the following format: 

```sh
export MY_SECRET=1234567890
export MY_OTHER_SECRET="The five boxing wizards jump quickly."
```

### Running your code

To run your program now, you must first load your environment file into your current shell session. You can do that with the [`source`](http://ss64.com/bash/source.html) command.

```sh
source .env
```

And now run your program normally:

```sh
$ python example.py 
1234567890
The five boxing wizards jump quickly.
```

If your config changes frequently, you can make sure it's always up-to-date by loading it everytime you run your program with this shorthand:

```sh
$ source .env; python example.py 
```
