# Tips and tricks

This chapter contains useful information to help you solve specific issues.

## Initialize your solution

Examples from [keil.arm.com](https://keil.arm.com) or solutions you [create from scratch](./create_app.md) from the
**Create Solution** view are already initialized and contain all the required files.

If your solution does not contain the `vcpkg-configuration.json`, `tasks.json`, and `launch.json` files, right-click
anywhere in the workspace and select **Initialize CMSIS project**. The extension generates preconfigured files
that are ready to use.

## Set current solution in workspace

To activate a solution in the **Solution** outline view, use the **Select Active Solution from workspace** option in
**Views and More Actions** ![Views and More Actions icon](./images/more-actions-icon.png).

## Enhancing the Debug Experience

To ensure the best debug experience with Arm Compiler for Embedded, make sure that your CMSIS solution files contain
the following.

### csolution.yml

In the `*.csolution.yml` file, insert the following block in `- target-types\- type` section:
  
```yml
      target-set:
        - set: 
          debugger:
            name: # set to name of your debug adapter
```

Insert the following before the `- projects` section:

```yml
  misc:
   - for-compiler: AC6
     C-CPP:
       - -gdwarf-5
     ASM:
       - -gdwarf-5
     Link:
       - --entry=Reset_Handler
```

### cproject.yml

In the `*.cproject.yml` file, add at the end:

```yml
  output:
    type:
     - elf
     - hex
     - map
```
