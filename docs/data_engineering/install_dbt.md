# Install DBT locally

Installing DBT locally succesfully isn't that aweful if you understand why it can be so absolutely aweful.
At the end of the day it's just a python thing so we will treat it as such and install it as the simple python thing that it is! 

You need just a few steps to do it succesfully:

- Install the **correct** version of python (the version that dbt will work with)
- Make a virtual environment (whatever that means)
- Install DBT like you would any other python thing (however you're supposed to do that). 

## Short overview (if you know what you're doing)
- install pytnon3.10
- `python3.10 -m venv .venv`
- `source .venv/bin/activate`
- `pip install dbt-snowflake`
- link it to your snowflake account according to the dbt prompt

## Step1: Install the correct python version. 
It turns out DBT will not work if you use anything other than **python3.10** so we'll need to install that first. This is how you do it on mac.

!!! note "Fun fact"
    The B in DBT actually means "bomb". If you try to install dbt without taking proper precautions, it will quite litereally explode. 

One thing you can do is in your terminal to see your current python version is type the following:   
> `python3 --version`  
> *output: `>> Python 3.11.0`*

!!! 
As you can see above, my current python version is very cool but will cause dbt to explode, no bueno. So we need to install another python version. 

1.  Get python 3.10.7 from the [official python site](https://www.python.org/)
    - Navigate to downloads>MacOS
    - Scroll down to the bottom of the screen and find "python3.10.7"
    - Or go straight to [the python 3.10.7 page](https://www.python.org/downloads/release/python-3107/)
    - Then scroll down to the "Files" table and find "macOS 64-bit universal2 installer"
    - Download it and launch it. 
2. Install python3.10.7
    - Go to your download folders where you downloaded the `python-3.10.7-macos11.pkg` file. 
    - Double click the thing
    - A screen will pop open where you can click continue a couple of times. 
    - Click continue a couple of times until the installation is complete. 
    - When it's done a folder might pop up with all of the things you just installed, you can close this. Or not, do whatever you like.
3. Confirm that python 3.10.7 is installed
    - Open a *new* terminal
    - Let me repeat, open a *new* terminal, because your old terminal might not see the newly installed things yet. 
    - type
    > `python3 --version`
    > *output: `>> Python 3.11.0`* !!! THE WRONG ONE, WHY!!!?? -- don't worry everything will be ok. 
    - Ok if it still shows the wrong python version, don't worry that's completely normal. 
    - If it does show the correct version of python then well congratulations. 
    - To check that python3.10.7 really really is installed you can specify which python to use to do things. 
    - Instead of writing python3, you can also write python3.10. Try that now:
    >`python3.10 --version`
    >output: `Python 3.10.7` -- Succes! 

    !!! warning
        If the above didn't work for some reason try to retrace your steps and reinstall python 3.10.7.   
        If it still doesn't work. Contact me, Robert or someone else to help because oh boy you will need it 


    With the correct version of python installed you're now ready for the next step.

## Step 2: Create a virtual environment
What is a virtual environment even?

Whenever you install stuff in python the files are put in "the environment". This is just a folder where whatever packages are stored when you install them with `pip install numpy` for example. When you then write something like `import numpy` in your python scripts it will know where to look in "the environment" for the package that it needs. 

Now in real life sometimes code can get a bit complicated and package version "so and so" will start to break when you try to use it with the newest version "this one cool package". Or sometimes you might want to make an app with only a handfull of all of te thousands of packages that you've been installing in your "environment". 

That's where "virtual environments" come in. You create an entirely new space in your computer, you step into it and whenever you `pip install <some package>` it will be installed in an entirely new and entirely fresh "environment". And as a bonus, it's really easy to recreate virtual environements with all the necessary packages so they just work, no matter what machine they are on. But that's not needed for today.

Now remember that DBT is a bomb? Bombs are especially good to put inside virtual environments. This way when they explode you only have to worry about the few things that are going on inside this isolated "virtual environment" that you've installed it in. 

Let's make a virtual environment.

1. Go to the location where you want to make your dbt project.
> `cd Documents/programming/python/` (this is where I play around with code)

2. Create the virtual environment.
    -  Don't copy the below code just yet, this is just to explain how the script works
    > `python3.10 -m venv kjhakdsjfhfkajsd`
    >> `python3.10` : this part says that you want to use python3.10 to make the virtual environment  
    >> `-m venv` : this part means that you want to "-m" use a python module called "venv". This is the thing that will magically make a virtual environment  
    >> `kjhakdsjfhfkajsd` : this is the name of our environment, which is very beautiful.

    - Ok you can copy this thing now
    > `python3.10 -m venv .venv`
    This creates a virtual environment inside a hidden folder ".venv" 
    - You can view the folder that's created by typing `ls -la` in the terminal. This will show all stuff in your current directory including the hidden folders. 
    - You don't have to do this inside a hidden folder btw. `python3.10 -m venv venv` also works nicely. I just prefer to make my virtual envs in hidden folders because vscode sometimes has issues recognizing them when they are in normal folders, but watever you want will work.

3. Activate the virtual environment
    - You've created the virtual environment but you still need to "activate" it so you're actually inside it before you do anything else. 
    - copy the following if you want
    > `source .venv/bin/activate`
    >> `source`: this is a command to execute some file, we want to execute the file that "activates" our virtual environment  
    >> `.venv`: this is the name of your virtual environment  (if you named it *venv* or *kjhsdkjfh* then change this part)
    >> `/bin/activate`: this is the location of the "activation" thing we want to activate with the `source` command.

4. You should now be inside your virtual environment.
    - `/Documents/programming/python >>` : before activating the environment
    - `(.venv) /Documents/programming/python >>` : after activating the environment 

    - You can see that you're in your virtual environment by these brackets that appear before your prompt.
    - Or if you've done some fancy stuff to customize your terminal it will show in some other way. 

In summary:
```bash
cd <location that you want>
python3.10 -m venv <name you want ot call your virtual environment>
source <name of virtual environment>/bin/activate
```
    
Summary for a virtual environment named ".venv"
```bash
python3.10 -m venv .venv
source .venv/bin/activate
```


## Step3: Installing DBT
Time to install the bomb

We will basically be follwing [the tuturial of the official DBT docs](https://docs.getdbt.com/docs/get-started/pip-install)

Just as you would install a normal python thing with `pip install <normal python thing>`
We will install dbt with `pip install dbt`
!!! Error "wait don't do it just yet"
    Except! `pip install dbt` doesn't work anymore for some reason and it will explode. Don't do this. 
    Read more about this here: [DBT Documentation]

### Installing dbt for snowflake
1. Go to your folder location and activate your virtual environment like you just learnt.
```bash
pip install --upgrade pip
pip install dbt-snowflake
```
2. That was it, you now have dbt ready to go inside the virtual environment. 

### Hooking up dbt to snowflake 
To succesfully do this you'll need a snowflake account, maybe a trial account if you're just starting out.  
[Create a trial account here and follow the instructions by snowflake](https://signup.snowflake.com/)

#### Set up snowflake before you fire up dbt
- You'll need to have some idea of how snowflake works before you start doing this. Check out some of their fundamental trainings.
- Other than that you'll need some info before you set up the dbt:

| Information      | Have this ready at hand before continueing|
| ----------- | ------------------------------------ |
| Snowflake account | `https://<this_value>.snowflakecomputing.com` |
| Snowflake username   | `myusername` |
| Snowflake password   | `mysupersecretpassword`|
| Role   | `Accountadming | Sysadmin | etc..`|
| Database name   | "make this one whatever" |
| Schema   | Define this one or use the public default|
| Warehouse Name | Pick one from snowflake |

#### Fire up dbt
- Alright let's start with the fun stuff, run dbt init to start a project and follow their instructions and fill in the information that you should have gathered above.
```bash 
dbt init
```
- Now DBT has a dummy default setting ready to go so to check if the installation worked simply run the follwing.
```bash
cd <whatever you called your dbt project>
dbt run
```

#### Confirm if this worked

- Now check snowflake and you should see a new table created called `MY_FIRST_DBT_MODEL`

!!! success "You did it!"
    If this worked, please let me know! 
    If the tutorial sucked, please let me know as well and I'll make it better


## Step 4: Next steps:
- Connect this to a git repo, should be easy enough. 
- If it's not that easy let me know and I'll add that step into this tutorial 

Good luck! 
