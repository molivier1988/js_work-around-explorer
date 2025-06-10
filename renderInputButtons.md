# renderInputButtons

## Purpose

I struggled to understand how the **select a role** and **select a company** sections were created on the fly using JS. So in my own words this is how it works:

### renderInputButtons()

`renderInputButtons(companies, "company")` takes 2 arguments.

The 1st **companies** | **roles** is a variable **_[main.js line 12 & 13]_** which stores the results from the `getCompanies()` & `getRoles()` functions found in **_salaryData.js_** this returns an array of strings ['Big Data Inc.', 'Medium Data Inc.', 'Small Data Inc.'] and ['CTO', 'Technical Lead', 'Software Engineer II', 'Software Engineer I']

The 2nd is a string which will be used later to add text to the rendered page plus **names** and **labels** for the input buttons.

### Create new sections

The core of the function creates 2 sections within the HTML page for **role** an **company**.

#### Step 1 Call renderInputButtons()

`function renderInputButtons(labels, groupName)`

The function is passed 2 arguments

**labels** An array containing the role and company name data

**groupName** Either "company" | "role"

#### Step 2 Dynamically create sections

```js
   const container = document.createElement("section)";
   container.SetAttribute("id", `${groupName}Inputs)
```

    => Create a new HTML element <section> and set an ID attribute of either **roleInputs** | **companyInputs**

#### Step 3 Add H3 Headers

```js
let header = document.createElement("h3");
header.innerText = `Select a ${groupName}`;
container.appendChild(header);
```

    => Create a `<h3>` element

    => set it's text to either **role** | **company**

    => append new element to its container <section>

#### Step 4 Create divs

```js
labels.forEach((label) => {
    let divElement = document.createElement("div");
    divElement.setAttribute("class", "option");
```

For each label in the array labels

    => Create a new <div></div>

    => Set the ***class** attribute to "option"

#### step 5 Create radio buttons

```js
let inputElement = document.createElement("input");
inputElement.setAttribute("type", "radio");
inputElement.setAttribute("name", groupName);
inputElement.setAttribute("value", label);
divElement.appendChild(inputElement);
```

For each **label** in the arrays **role** | **company**

    => Create an <input> element

    => Set its type to "radio"

    => Set its name attribute to either "role" | "company"

    => Set its value attribute to the current label (this will be either a role e.g. 'CTO' | company 'Big Data Inc.)

    => Append new inputElement to its parent <div>

#### Step 5 Create a label for the radio inputs

```js
let labelElement = document.createElement("label");
labelElement.setAttribute("for", label);
labelElement.innerText = label;
divElement.appendChild(labelElement);
```

For each radio input

    => Set "for" attribute to current label
    => Set label text to current label
    => append <label> element as child to <div>

#### Step 6 Add event listener

`inputElement.addEventListener("click", updateResults);`

Add an event listener to each radio button

    => Call updateResults() function on "click"

### Step 7 Add new sections to the HTML page

`document.querySelector("main").prepend(container);`

Use `querySelector` to find the `<main>` element

    => Append <container> to <main>. This effectively adds the 2 new sections created by the above code.
