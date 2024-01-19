# DXP Components for Vue applications

## How to use?

# Contribution Guideline

1. Fork the repository and clone it locally from the `main` branch. Before starting your work make sure it's up to date with current `main` branch.
2. Pick an issue from [here](https://github.com/hotwax/dxp-components/issues). Write in the issue comment that you want to pick it, if you can't assign yourself. **Please stay assigned to one issue at a time to not block others**.
3. Create a branch for your edits. Use the following branch naming conventions: **dxp-components/issue-number**.
4. Please add issue number to your commit message.
5. Propose a Pull Request to `main` branch containing issue number and issue title.
6. Use [Pull Request template](https://github.com/hotwax/dxp-components/blob/main/.github/PULL_REQUEST_TEMPLATE.md) (it's automatically added to each PR) and fill as much fields as possible to describe your solution.
7. Reference any relevant issues or other information in your PR.
8. Wait for review and adjust your PR according to it.
9. Congrats! Your PR should now me merged in!

If you can't handle some parts of the issue then please ask for help in the comment. If you have any problems during the implementation of some complex issue, feel free to implement just a part of it.

## Report a bug or request a feature

Always define the type of issue:
* Bug report
* Feature request

While writing issues, please be as specific as possible. All requests regarding support with implementation or application setup should be sent to.

# Join the community on Discord
If you have any questions or ideas feel free to join our <a href="https://discord.gg/SwpJnpdyg3" target="_blank">Discord channel</a>

# The license

DXP Components is completely free and released under the Apache v2.0 License. Check <a href="https://github.com/hotwax/dxp-components/blob/main/LICENSE" target="_blank">LICENSE</a> for more details.

# Components
## DxpImage 
### Introduction
<li> dxpImage component is designed to handle the loading and display of images.</li>
<li> It provides functionality to efficiently manage different types of image sources, including local assets, external web URLs, and images from a resource server.</li>

### Basic Usage 
<li>TThe component dynamically loads and displays the specified image, considering different source scenarios, such as local assets, web URLs, or resource server images.</li>

### Props
#### 1. src
<table>
  <tr>
    <th>Descrption</th>
    <td>It's specifying that the component expects a prop named src.n this component props.src to access the value of the src.</td>
  </tr>
  <tr>
    <th>Type</th>
    <td>string</td>
  </tr>
  <tr>
    <th>Required</th>
    <td>False</td>
  </tr>
   <tr>
    <th>Default value </th>
    <td>‘context.defaultImgUrl’</td>
  </tr>
</table>

## Technical Implementation
#### 1. setImageUrl()
The setImageUrl function is responsible for determining the appropriate image URL based on the provided props.src and the configured resourceUrl.
<li>If props.src contains 'assets/', assigns directly to imageUrl for local assets.</li>
<li>If props.src starts with 'http', checks image existence; if true, assigns to imageUrl for web URLs.</li>
<li>If not local or web, assumes resource server image, appends to resourceUrl, and assigns if URL exists.</li>

#### 2. checkIfImageExists()

<li>Returns a Promise</li>
<li>Resolves to true if the image loads successfully, rejects with false on error.</li>
<li>Logs an error message to the console if the image doesn't exist</li>

#### 2. onMounted()

<li>onMounted() hook activates when the component is added to the DOM.</li>
<li>It calls the setImageUrl function.</li>
<li>During the initial rendering, it sets the image URL based on the logic within setImageUrl.</li>

#### 2. onUpdated()

<li>onUpdated() hook activates on component re-renders.</li>
<li>Like onMounted, it calls setImageUrl.</li>
<li>Ensures dynamic updating of the image URL based on changes in reactive dependencies during re-renders.</li>

## Recommendation
<li>Use the component to load and display images stored as local assets within the project directory.</li>
<li>Employ the component to fetch and showcase images from external web URLs.</li>
<li>Use the component to display images fetched from a resource server.</li>
<li>Component's dynamic nature, allowing it to adapt different image sources based on the provided <b>props.src</b>. This is useful in scenarios where image sources can vary at runtime.</li>
