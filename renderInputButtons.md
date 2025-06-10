# renderInputButtons

## Purpose

I struggled to understand how the **select a role** and **select a company** sections were created on the fly using JS. So in my own words this is how it works:

### renderInputButtons()

`renderInputButtons(companies, "company")`

ARG_1 **companies** | **roles** stores the results from the `getCompanies()` & `getRoles()` functions found in **_salaryData.js_** returning an array of strings ['Big Data Inc.', 'Medium Data Inc.', 'Small Data Inc.'] and ['CTO', 'Technical Lead', 'Software Engineer II', 'Software Engineer I']

ARG_2 is a string which will be used later to add text to the rendered page plus **names** and **labels** for the input buttons.

### Create new sections

The core of the function creates 2 sections within the HTML page for **role** and **company**.

#### Step 1 Call renderInputButtons()

`function renderInputButtons(labels, groupName)`

The function is passed 2 arguments

**labels** An array containing the role and company name data

**groupName** Stores a string either "company" | "role"

#### Step 2 Dynamically create sections

```js
   const container = document.createElement("section)";
   container.SetAttribute("id", `${groupName}Inputs)
```

    1. Create a new HTML element <section> and set an ID attribute of either **roleInputs** | **companyInputs**

#### Step 3 Add H3 Headers

```js
let header = document.createElement("h3");
header.innerText = `Select a ${groupName}`;
container.appendChild(header);
```

    1. Create a `<h3>` element

    2. Set it's text to either **role** | **company**

    3. Append new element to its container <section>

#### Step 4 Create divs

```js
labels.forEach((label) => {
    let divElement = document.createElement("div");
    divElement.setAttribute("class", "option");
```

For each label in the array labels

    1. Create a new <div></div>

    2. Set the ***class** attribute to "option"

#### step 5 Create radio buttons

```js
let inputElement = document.createElement("input");
inputElement.setAttribute("type", "radio");
inputElement.setAttribute("name", groupName);
inputElement.setAttribute("value", label);
divElement.appendChild(inputElement);
```

For each **label** in the arrays **role** | **company**

    1. Create an <input> element

    2. Set its type to "radio"

    3. Set its name attribute to either "role" | "company"

    4. Set its value attribute to the current label (this will be either a role e.g. 'CTO' | company 'Big Data Inc.)

    5. Append new inputElement to its parent <div>

#### Step 5 Create a label for the radio inputs

```js
let labelElement = document.createElement("label");
labelElement.setAttribute("for", label);
labelElement.innerText = label;
divElement.appendChild(labelElement);
```

For each radio input

    1. Set "for" attribute to current label
    2. Set label text to current label
    3. append <label> element as child to <div>

#### Step 6 Add event listener

`inputElement.addEventListener("click", updateResults);`

Add an event listener to each radio button

    1. Call updateResults() function on "click"

### Step 7 Add new sections to the HTML page

`document.querySelector("main").prepend(container);`

Use `querySelector` to find the `<main>` element

    1. Append <container> to <main>. This effectively adds the 2 new sections created by the above code.
