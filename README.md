# KOGURE Daemon

'Kogure' is a daemon like CLI command which runs your script in background. You can 'start', 'stop' and 'restart' them and/or see their running status.


Define in JSON file, which script you allow to run, and then you can 'start', 'stop' and 'restart' them like so:

```
$ kogure start MyScript1
```

What this app does is simple. It runs your script with `nohup` if it's not
already run. 

## SETUP:

1. PLACE THIS APP SCRIPT ANYWHERE YOU WANT.

    Placing it in a directory at $ENV path is preferred for convenience.  
    So you don't need to `cd` every time or use the absolute path to run 
    'kogure'.

2. EDIT THE PATH TO YOUR JSON FILE.

    In the "User settings" section of this app, you'll find a 
    "`$path_file_json_allow`" variable which defines the path to your JSON 
    file. Change the path you prefer.

2. CHANGE MODE AS EXECUTABLE.

    Such as `$ sudo chmod +x kogure`.

3. CREATE A JOSN FILE.

    Create a JSON file in a path you specified above (STEP 2). You may copy
    the sample JSON from the repository and rename it.

4. EDIT THE JSON FILE.

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

5. RUN `kogure help` TO SEE WORKING.
    If you didn't place `kogure` in to $ENV path, you need to change the
    current directory to kogure's path and do `$ ./kogure help` or run
    it with absolute path such as `/path/to/kogure help`.

6. RUN YOUR SCRIPT LIKE A SERVICE.

```
$ kogure start MyScript1
```

If you don't understand the above or how to, this script might be dangerous
 for you or cause a problem, so I will not suggest to use it.

