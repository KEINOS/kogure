# KOGURE Daemon

'Kogure' is a daemon like CLI command app which helps you run your script in background. 

This is a simple alternate command script in case you have no access to use `system.d` nor `init.d` or feel it's too much to use them.

What this app does is simple. It runs your script with `nohup` if it's not already run. And you can 'start', 'stop' and 'restart' them and/or see their running status.

## BASIC USAGE

Define in the JSON file which script you allow to run. And then you can 'start', 'stop' and 'restart' them like so:

```ShellSession
$ ./kogure start MyScript1
Process started.
PID: 65944
```

```ShellSession
$ ./kogure stop MyScript1
Process 65944 stopped.
```

```ShellSession
$ ./kogure status
MyScript1	Off
MyScript2	Off
MyScript3	On (PID: 65946)
```


## BEFORE SETUP:

1. PREPARE YOUR SCRIPT

    Make ready your script be called as below:
    
    ```
    $ /path/to/MyScript1
    ```
    
    This means your script needs the below functions:

    - Has a valid `shebang`.
    - Runs in a loop.
    - Does the normal termination processing when kill signal was received. 

## SETUP:

1. PLACE [THIS DAEMON-LIKE APP SCRIPT](https://github.com/KEINOS/kogure/blob/master/kogure) ANYWHERE YOU WANT.

    Placing it in a directory at `$ENV` path is preferred for convenience.  
    So you don't need to `cd` every time or use the absolute path to run 'kogure'.

2. EDIT THE PATH OF JSON FILE IN THE APP SCRIPT.

    In the "User settings" section of this app, you'll find a "`$path_file_json_allow`"  variable. This variable defines the path to your JSON file.
    Change the path you prefer.

3. CHANGE MODE AS EXECUTABLE.

    Such as `$ sudo chmod +x kogure`.

5. CREATE A JOSN FILE.

    Create a JSON file in a path you specified above (STEP 2). You may copy the [sample JSON](https://github.com/KEINOS/kogure/blob/master/sample-kogure_allow.json) from the repository and rename it.

6. EDIT THE JSON FILE.

    This JSON file defines which script you allow to run. The format are:

    ```json
    {
         "<name of script>": "<path of yourscript>",
         "MyScript1": "/path/to/MyScript1.php",
         "MyScript2": "/path/to/MyScript1.py",
    }
    ```

    NOTE: Your script MUST have a valid shebang and set mode as executable.
    Also if you want your script run like a service, you need to loop your
    script endlessly.

7. RUN `kogure help` TO SEE WORKING.
    If you didn't place `kogure` in to $ENV path, you need to change the
    current directory to kogure's path and do `$ ./kogure help` or run
    it with absolute path such as `/path/to/kogure help`.

8. RUN YOUR SCRIPT LIKE A SERVICE.

```
$ kogure start MyScript1
```

If you don't understand the above or how to, this script might be dangerous
 for you or cause a problem, so I will not suggest to use it.

