# Software components

A [software component](https://open-cmsis-pack.github.io/cmsis-toolbox/CreateApplications/#software-components)
encapsulates a set of related functions. The **Software Components** view shows all the software components selected in
the active project of a solution.

You can:

- [Modify the software components](#modify-the-software-components-in-your-project) of the project.

- Manage the dependencies between components for each target type defined in your solution, or for all the target types at
  once.

## Software Components view

Open the **CMSIS view** and click ![Manage software components](./images/software-components-icon.png) to open the
**Software Components** view:

![The 'Software Components' ](./images/software-components-view.png)

You can:

1. Switch between *components* and *software packs*.
2. View only components that are *part of the csolution* or components from *all installed packs*.
3. Set the *context* for which the component selection applies (including layers).
4. *Select/remove* software components.
5. View *more information* about the component (name, pack, version, and description).
6. Select different *variants* of a component.
7. Open *related documentation*.

<!--
Layer icons ![Layer icon](./images/layer-icon.png) indicate which components are used in layers. In the current version,
layers are read-only, so you cannot select or clear them. Click the layer icon of a component to open the `*.clayer.yml`
file or associated files.

## Modify the software components in your project

You can add components from all the packs available, not just the packs that are already selected for a project.

### Modify the context displayed

- In the **Project** drop-down list, select the project for which you want to modify software components.

- In the **Target** drop-down list, select a specific target type. If you want to modify all the target types at once,
  select **All Targets**. Note that you might have only one target.

- In the **Software packs** drop-down list, you can filter on the components available from the packs listed in your
  solution with the **Solution: &lt;Solution-name&gt;** option. You can display the components from all installed packs with
  the **All installed packs** option.

### Select components

Check that the **All** toggle button is selected to display all the components available. Switch to **Selected** to display
only the components that are already selected.

Use the checkboxes to select or clear components as required. For some components, you can also select a vendor, variant,
or version. The `cproject.yml` file is automatically updated.
-->

### Validation

In the **Software Components view**, you can manage the dependencies between components and solve validation issues.
Issues are highlighted with a yellow exclamation mark icon ![Issue icon](./images/issue-icon.png).

![Validation errors](./images/validation-error.png)

If there are validation issues:

1. Either click on ![Issue icon](./images/issue-icon.png) and select the issue in the pop-up box (a) or
2. Click the "Resolve" button for access to the pop-up box (a).
3. Once a components with validation issues is opened, you can use the "eye" icon to see which component is
   missing/affected (b).
4. Use the "Apply" button to select the missing components (only available if there is no choice between different
   components available).

When done, don't forget to **Save** the changes!
