Routing and Vuetify

 Last updated: November 4, 2025

routing

vuetify

Overview

This guide covers the basics of integrating Vuetify (a Material Design component library) into your Vue.js application and implementing routing between pages.



Getting Started with Vuetify

Vuetify is a Material Design component library that provides pre-built UI components for Vue.js applications.



Finding Components

Search for Vuetify 2 documentation

Navigate to the Get Started section

Browse the UI Components library





Adding Vuetify Components

Example: Adding Card Components

Navigate to the Cards section in Vuetify documentation and copy the component code.



In your component file (e.g., HomeSection1.vue):



<template>

  <!-- Paste the Vuetify card component here -->

  <!-- Remove the outer <template> tags from the copied code -->

  <v-card>

    <!-- Card content -->

  </v-card>

</template>



<script>

export default {

  data() {

    return {

      // Component data from Vuetify example

    }

  }

}

</script>

 Copy

Important: When copying from Vuetify examples:



Remove the outer <template> tags (top and bottom)

Remove the outer <script> tags (top and bottom)

Keep only the component content





Creating Navigation with App Bar and Drawer

Basic Navigation Structure

Use ChatGPT or Vuetify documentation to generate an app bar and navigation drawer structure.



Key Components:



<v-app-bar> - Top navigation bar

<v-navigation-drawer> - Side navigation drawer

Important: The v-app Tag

⚠️ Critical Rule: Never use the <v-app> tag within your components. It is already present at the root level of your application.



Only copy the <v-navigation-drawer> and <v-app-bar> components.



Implementing Top Navigation

In your TopNav.vue component:



<template>

  <div>

    <v-navigation-drawer v-model="drawer">

      <v-list>

        <v-list-item 

          v-for="item in items" 

          :key="item.title"

          :to="item.route"

        >

          <v-list-item-title>{{ item.title }}</v-list-item-title>

        </v-list-item>

      </v-list>

    </v-navigation-drawer>



    <v-app-bar>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-btn to="/">Home</v-btn>

      <v-btn to="/about">About</v-btn>

      <v-btn to="/contact">Contact</v-btn>

    </v-app-bar>

  </div>

</template>



<script>

export default {

  data() {

    return {

      drawer: false,

      items: [

        { title: 'Home', route: '/' },

        { title: 'About', route: '/about' },

        { title: 'Contact', route: '/contact' }

      ]

    }

  }

}

</script>

 Copy

![Navigation bar with drawer - IMAGE PLACEHOLDER]



Implementing Routing

Using the to Prop

Vuetify components support Vue Router integration through the to prop:



<!-- Button navigation -->

<v-btn to="/">Home</v-btn>

<v-btn to="/about">About</v-btn>

<v-btn to="/contact">Contact</v-btn>



<!-- List item navigation -->

<v-list-item to="/about">About</v-list-item>

 Copy

The to prop works with many Vuetify components for seamless routing.



Wrapping Content with v-main

The v-main Component

To ensure proper layout, especially with app bars and navigation drawers, wrap your router view in a <v-main> tag.



In your PagesContainer.vue:



<template>

  <div>

    <TopNav />

    <v-main>

      <!-- Your page components -->

      <HomePage v-if="$route.path === '/'" />

      <AboutPage v-if="$route.path === '/about'" />

      <ContactPage v-if="$route.path === '/contact'" />

    </v-main>

  </div>

</template>

 Copy

This ensures content appears below the app bar and adjusts properly with the navigation drawer.



Conditional Rendering with Routes

Problem: Components Rendering on All Pages

If you don't add route conditions, components will render on every page:



<!-- ❌ Wrong: Renders on all pages -->

<ContactSection1 />

<ContactSection2 />

 Copy

Solution: Add Route Conditions

<!-- ✅ Correct: Only renders on /contact route -->

<ContactSection1 v-if="$route.path === '/contact'" />

<ContactSection2 v-if="$route.path === '/contact'" />

 Copy

Complete Example:



<template>

  <v-main>

    <!-- Home page sections -->

    <HomeSection1 v-if="$route.path === '/'" />

    <HomeSection2 v-if="$route.path === '/'" />

    

    <!-- About page sections -->

    <AboutSection1 v-if="$route.path === '/about'" />

    <AboutSection2 v-if="$route.path === '/about'" />

    

    <!-- Contact page sections -->

    <ContactSection1 v-if="$route.path === '/contact'" />

    <ContactSection2 v-if="$route.path === '/contact'" />

  </v-main>

</template>

 Copy

Adding More Vuetify Components

Example Components

Calendar Component (in ContactSection1):



<template>

  <v-calendar></v-calendar>

</template>



<script>

export default {

  data() {

    return {

      // Calendar data

    }

  }

}

</script>

 Copy

Carousel Component (in ContactSection2):



<template>

  <v-carousel>

    <v-carousel-item

      v-for="(item, i) in items"

      :key="i"

      :src="item.src"

    ></v-carousel-item>

  </v-carousel>

</template>

 Copy

Component Integration Workflow

Find the component in Vuetify documentation

Copy the template code (remove outer <template> tags)

Copy the script code (remove outer <script> tags)

Paste into your component

Add route conditions if needed

Test navigation between pages

Vuetify API Documentation

The Vuetify documentation provides detailed API references for each component, including:



Props - Component properties and configuration

Events - Available event handlers

Slots - Customization points

Examples - Working code samples

Explore the API section to understand how to customize components for your specific needs.



Best Practices

✅ Always remove outer <template> and <script> tags when copying

✅ Never use <v-app> tag within components

✅ Wrap page content in <v-main> for proper layout

✅ Add route conditions to prevent components from rendering on all pages

✅ Use the to prop for navigation instead of manual routing

✅ Check Vuetify documentation for component-specific requirements

Summary

Vuetify provides pre-built Material Design components

Use <v-app-bar> and <v-navigation-drawer> for navigation

The to prop enables easy routing in Vuetify components

Wrap content in <v-main> for proper layout

Use v-if="$route.path === '/path'" for conditional rendering

Always consult Vuetify documentation for component APIs and examples

Next Steps

In the upcoming lessons, we'll dive deeper into:



Advanced Vuetify layouts and grid systems

Component customization and theming

Creating complex, responsive layouts effortlessly

Continue exploring the Vuetify documentation to discover more components and possibilities!

Pages and Components

 Last updated: October 30, 2025

components

pages

vue

Overview

In Site Guru Platform, components are the building blocks of your application. Each component can represent a UI element, layout, or feature module that you can reuse across different pages.



This guide walks you through creating a new component and linking it to a page or another component.



Step 1: Create a Component

Navigate to the Frontend section of your project.

On the left-hand sidebar, you will see a list of all existing components.

Click the “+” (plus) button located above the component list.

Enter the name of your new component.

Click the “Create” button.

Once completed, your new component will appear in the sidebar, ready for editing.







Step 2: Link the Component to a Page

After creating the component, you’ll need to link it to a page (or another component) to make it functional.



Navigate to the page where you want to use the component.

Click the “Link” button.

From the popup window, select your newly created component.

Copy the auto-generated code snippet provided.

Paste the code inside your target page or component file.

Your component is now successfully linked and ready to use.















Step 3: Add Conditional Rendering (Optional)

You can control the visibility of components dynamically using Vue conditional directives:



<a-comp  v-if="!($route.path=='/login')"  entity_id="1000678t1761285064396c7" comp_name="adminNavbar" />

<b-comp v-if="!($route.path=='/login')" entity_id="1000678t1761285067417c8" comp_name="adminSidebar" />

﻿

<v-main app dark class="main-container">

<a-comp v-if="!$auth.loggedIn && $route.path=='/login'" entity_id="1000678t1761285205089c13" comp_name="loginPage" /> 

<c-comp v-else entity_id="1000678t1761285144300c12" comp_name="adminContainer" />

</v-main>

 Copy

This allows you to render different components based on your project’s logic or state.



Summary

✅ Create a component from the frontend page sidebar.

✅ Link it to a page using the link popup and copy-paste snippet.

✅ Control visibility using v-if, v-else-if, and v-else for dynamic UI rendering.

Props and Events in Vue.js

 Last updated: November 4, 2025

props

events

Overview

This guide covers how to pass data between parent and child components using props and events in Vue.js applications.



What are Props?

Props (properties) are used to pass data from a parent component to a child component. They enable one-way data flow from parent to child.



Basic Props Usage

In the parent component (PagesContainer), you can pass props to the child component (HomePage):



<HomePage my-organisation="SiteGrow" />

 Copy

![Props flow from parent to child - IMAGE PLACEHOLDER]



In the child component, accept the prop:



export default {

  props: ['my-organisation'],

  // ... other options

}

 Copy

Then use it in the template:



<template>

  <h1 class="text-center">{{ myOrganisation }}</h1>

</template>

 Copy

Passing Dynamic Props

You can pass variables as props instead of static strings. Use the : shorthand (v-bind) to bind dynamic values:



Parent Component:



export default {

  data() {

    return {

      organisationName: 'SiteGrow Private Limited'

    }

  }

}

<HomePage :my-organisation="organisationName" />

 Copy

The colon (:) before the prop name tells Vue to treat the value as a JavaScript expression rather than a string.



![Dynamic props binding - IMAGE PLACEHOLDER]



Events: Child to Parent Communication

While props pass data down from parent to child, events allow child components to communicate back to their parents.



Emitting Events from Child

In the child component, use $emit to send events to the parent:



export default {

  data() {

    return {

      myAge: 25,

      users: ['John', 'Jane', 'Bob']

    }

  },

  methods: {

    sendEvent() {

      this.$emit('event-from-home-page', {

        age: this.myAge,

        users: this.users

      });

    }

  }

}

<template>

  <button @click="sendEvent">Send Event to Parent</button>

</template>

 Copy

![Event emission from child to parent - IMAGE PLACEHOLDER]



Listening to Events in Parent

In the parent component, listen for the event using @ (v-on shorthand):



<HomePage @event-from-home-page="getEventFromChild" />

 Copy

Define the handler method:



export default {

  methods: {

    getEventFromChild(event) {

      console.log('Event is coming');

      console.log(event); // { age: 25, users: [...] }

    }

  }

}

 Copy

The event data is automatically passed as the first parameter to your handler method.



![Event handling in parent component - IMAGE PLACEHOLDER]



Key Concepts

Props Flow

Direction: Parent → Child

Type: One-way data binding

Purpose: Pass data down the component tree

Events Flow

Direction: Child → Parent

Type: Event emission

Purpose: Notify parent of actions or send data up

![Complete props and events flow diagram - IMAGE PLACEHOLDER]



Syntax Reference

Passing Props

<!-- Static string -->

<ChildComponent prop-name="static value" />



<!-- Dynamic value (variable) -->

<ChildComponent :prop-name="variableName" />

 Copy

Emitting Events

// Emit event with data

this.$emit('event-name', dataPayload);



// Emit event with multiple data points

this.$emit('event-name', {

  property1: value1,

  property2: value2

});

 Copy

Listening to Events

<ChildComponent @event-name="handlerMethod" />

 Copy

Best Practices

Use kebab-case for prop names in templates (my-organisation)

Use camelCase for prop names in JavaScript (myOrganisation)

Always validate props in production applications

Keep event names descriptive to indicate their purpose

Avoid mutating props directly in child components

Next Steps

In the next section, we'll explore global variables and how to define properties that are accessible across all components, as opposed to these local component properties covered here.



Summary

Props enable passing data from parent to child components

$emit sends events from child to parent components

Event handlers in the parent receive emitted data as parameters

Props and events work together to create reactive component communication


Vue Component Fundamentals
 Last updated: October 30, 2025
files
structure
Overview
This comprehensive guide covers the essential building blocks of Vue.js components. Understanding these concepts is crucial for building reactive and maintainable Vue applications.

![Vue component fundamentals overview - IMAGE PLACEHOLDER]

Table of Contents
This guide is organized into the following sections:

1. Component Structure & Lifecycle Hooks
Learn about Vue component anatomy and lifecycle hooks (created, mounted, destroyed)

Topics covered:

Component structure overview
created() hook
mounted() hook
destroyed() hook
Lifecycle execution flow
→ Read the full Lifecycle Hooks guide

2. Data Properties
Understanding reactive data and how to use it in your components

Topics covered:

Defining data properties
Using data in templates (mustache syntax)
Accessing data in script
Working with arrays and objects
→ Read the full Data Properties guide

3. Computed Properties
Learn how to create derived values that automatically update

Topics covered:

What are computed properties
Defining computed properties
Computed vs methods
Performance benefits
Reactivity with computed properties
→ Read the full Computed Properties guide

4. Methods
Working with functions in Vue components

Topics covered:

Defining methods
Calling methods from templates
Event handling with methods
Methods vs inline expressions
Best practices
→ Read the full Methods guide

5. Watchers
Observe and react to data changes

Topics covered:

What are watchers
Watching data properties
Watching computed properties
Watcher limitations
Common use cases
→ Read the full Watchers guide

6. Complete Example: Putting It All Together
A comprehensive example showing how all concepts work together

Topics covered:

Complete reactive component
Execution flow
Property access patterns
Best practices summary
→ Read the full Complete Example guide

Quick Reference
Component Structure
export default {
  props: [],           // From parent
  data() {},          // Local state
  computed: {},       // Derived values
  watch: {},          // Observers
  methods: {},        // Functions
  created() {},       // Lifecycle
  mounted() {},       // Lifecycle
  destroyed() {}      // Lifecycle
}
 Copy
Access Patterns


 | Location   | Pattern                 | Example               |
|-------------|--------------------------|------------------------|
| Template   | `{{ propertyName }}`     | `{{ myAge }}`         |
| Script     | `this.propertyName`      | `this.myAge`          |
| Attributes | No mustache              | `@click="method()"`   |

 Copy
Learning Path
Recommended order for beginners:

Start with Data Properties to understand reactive state
Move to Methods to learn about functions and event handling
Learn Computed Properties for derived values
Understand Lifecycle Hooks for initialization and cleanup
Master Watchers for advanced reactivity patterns
Study the Complete Example to see everything in action
Prerequisites
Before diving into these topics, you should be familiar with:

Basic JavaScript (ES6+)
Vue.js basics and installation
Component creation
Template syntax
Next Steps
After mastering these fundamentals, you'll be ready to learn:

Props: Passing data from parent to child
Events: Communication from child to parent
Global State Management: Vuex or Pinia
Advanced Lifecycle Hooks: beforeMount, beforeDestroy, etc.
Additional Resources
Vue.js Official Documentation
Vue.js API Reference
Vue.js Style Guide
Click on any section above to dive deeper into that specific topic.


Component Lifecycle Hooks
 Last updated: October 30, 2025
 
What are Lifecycle Hooks?
Lifecycle hooks are special methods that execute automatically at specific stages of a component's lifecycle. They allow you to run code when a component is created, mounted, updated, or destroyed.

![Component lifecycle diagram - IMAGE PLACEHOLDER]

Main Lifecycle Hooks
1. created()
When it runs: After the component instance is created, but before mounting to the DOM.

Use cases:

Fetching data from APIs
Initializing data properties
Setting up non-DOM related functionality
export default {
  data() {
    return {
      users: []
    }
  },
  created() {
    console.log('Homepage component is created');
    // Ideal for API calls
    this.fetchUsers();
  },
  methods: {
    fetchUsers() {
      // Fetch data from database
    }
  }
}
 Copy
What's available:

✅ Data properties
✅ Computed properties
✅ Methods
❌ DOM elements (not yet mounted)
![created() hook execution - IMAGE PLACEHOLDER]

2. mounted()
When it runs: After the component is mounted to the DOM.

Use cases:

DOM manipulation
Initializing third-party libraries
Setting up event listeners
Accessing $refs
export default {
  mounted() {
    console.log('Homepage component is mounted');
    // DOM is now available
    this.$refs.myElement.focus();
  }
}
 Copy
What's available:

✅ Data properties
✅ Computed properties
✅ Methods
✅ DOM elements (fully rendered)
![mounted() hook execution - IMAGE PLACEHOLDER]

3. destroyed()
When it runs: After the component is destroyed and removed from the DOM.

Use cases:

Cleanup operations
Removing event listeners
Clearing timers/intervals
Canceling API requests
export default {
  data() {
    return {
      timer: null
    }
  },
  mounted() {
    this.timer = setInterval(() => {
      console.log('Timer running');
    }, 1000);
  },
  destroyed() {
    console.log('Home component is destroyed');
    // Cleanup
    if (this.timer) {
      clearInterval(this.timer);
    }
  }
}
 Copy
![destroyed() hook execution - IMAGE PLACEHOLDER]

Lifecycle Flow Example
Navigating Between Routes
When using route conditions (v-if="$route.path === '/home'"):

Scenario 1: Navigate to Home

1. created() executes   → "Homepage component is created"
2. mounted() executes   → "Homepage component is mounted"
 Copy
Scenario 2: Navigate Away from Home (to About)

1. destroyed() executes → "Home component is destroyed"
 Copy
Scenario 3: Navigate Back to Home

1. created() executes   → "Homepage component is created" (again)
2. mounted() executes   → "Homepage component is mounted" (again)
 Copy
![Route navigation lifecycle - IMAGE PLACEHOLDER]

Calling Methods from Lifecycle Hooks
You can execute methods from within lifecycle hooks:

export default {
  data() {
    return {
      myAge: 35
    }
  },
  methods: {
    incrementAgeBy20() {
      this.myAge += 20;
    }
  },
  created() {
    console.log('Component created');
    // Call method on creation
    this.incrementAgeBy20();
  }
}
 Copy
Other Lifecycle Hooks (Overview)
While created(), mounted(), and destroyed() are the most commonly used, Vue provides additional hooks:

| Hook              | When It Runs                                  |
|-------------------|-----------------------------------------------|
| `beforeCreate()`  | Before data initialization                    |
| `beforeMount()`   | Before mounting to DOM                        |
| `beforeUpdate()`  | Before DOM updates after data change          |
| `updated()`       | After DOM updates                             |
| `beforeDestroy()` | Before component destruction                  |
 Copy
Best Practices

✅ Use created() for API calls and data initialization
✅ Use mounted() for DOM-dependent operations
✅ Always clean up in destroyed() (timers, listeners, etc.)
✅ Keep lifecycle hooks focused and single-purpose
❌ Don't manipulate DOM in created() (it's not available yet)
❌ Don't perform async operations in destroyed()
Common Patterns
Pattern 1: Fetch Data on Load
export default {
  data() {
    return {
      items: [],
      loading: true
    }
  },
  async created() {
    try {
      this.items = await api.fetchItems();
    } finally {
      this.loading = false;
    }
  }
}
 Copy
Pattern 2: Initialize Library
export default {
  mounted() {
    // Initialize chart library
    this.chart = new Chart(this.$refs.canvas, {
      // configuration
    });
  },
  destroyed() {
    // Clean up chart
    if (this.chart) {
      this.chart.destroy();
    }
  }
}
 Copy
Summary
created(): Component created, data available, no DOM yet
mounted(): Component in DOM, everything available
destroyed(): Component removed, cleanup time
Hooks execute automatically at specific lifecycle stages
Use them for initialization, DOM access, and cleanup

Site Guru
Data Properties
 Last updated: October 30, 2025
 
What are Data Properties?
Data properties are local reactive variables that store component state. When data properties change, Vue automatically updates the parts of your template that use them.

![Data reactivity concept - IMAGE PLACEHOLDER]

Defining Data Properties
Data is defined as a function that returns an object containing your properties:

export default {
  data() {
    return {
      // Your properties go here
    }
  }
}
 Copy
Basic Types
export default {
  data() {
    return {
      // String
      myName: 'ABC',
      
      // Number
      myAge: 35,
      
      // String
      myCountry: 'India',
      
      // Boolean
      isActive: true,
      
      // Null
      selectedItem: null
    }
  }
}
 Copy
Complex Types
export default {
  data() {
    return {
      // Array
      users: [
        { id: 1, name: 'A' },
        { id: 2, name: 'B' },
        { id: 3, name: 'C' }
      ],
      
      // Object
      user: {
        firstName: 'John',
        lastName: 'Doe',
        email: 'john@example.com'
      },
      
      // Array of strings
      tags: ['vue', 'javascript', 'frontend']
    }
  }
}
 Copy
![Data types examples - IMAGE PLACEHOLDER]

Using Data in Templates
Mustache Syntax (Double Curly Braces)
Display data properties using {{ propertyName }}:

<template>
  <div>
    <p>{{ myName }}</p>
    <p>{{ myAge }}</p>
    <p>{{ myCountry }}</p>
  </div>
</template>
 Copy
Output:

ABC
35
India
 Copy
Displaying Arrays and Objects
<template>
  <div>
    <!-- Arrays display as JSON -->
    <p>{{ users }}</p>
    
    <!-- Access array items -->
    <p>{{ users[0].name }}</p>
    
    <!-- Access object properties -->
    <p>{{ user.firstName }} {{ user.lastName }}</p>
  </div>
</template>
 Copy
![Template data binding - IMAGE PLACEHOLDER]

Accessing Data in Script
Use this.propertyName to access data properties within component methods:

export default {
  data() {
    return {
      myAge: 35,
      myName: 'John'
    }
  },
  methods: {
    logData() {
      // Access data properties
      console.log(this.myAge);    // 35
      console.log(this.myName);   // "John"
    },
    updateAge() {
      // Modify data properties
      this.myAge = 40;
    }
  },
  created() {
    // Access in lifecycle hooks
    console.log(this.myAge);
  }
}
 Copy
Modifying Data Properties
Direct Assignment
methods: {
  updateName() {
    this.myName = 'Jane';
  },
  incrementAge() {
    this.myAge = this.myAge + 1;
    // Or shorthand:
    this.myAge++;
  }
}
 Copy
Array Methods
methods: {
  addUser() {
    this.users.push({ id: 4, name: 'D' });
  },
  removeFirstUser() {
    this.users.shift();
  },
  updateFirstUser() {
    this.users[0].name = 'Updated';
  }
}
 Copy
Object Properties
methods: {
  updateUser() {
    this.user.firstName = 'Jane';
    this.user.email = 'jane@example.com';
  },
  replaceUser() {
    this.user = {
      firstName: 'Alice',
      lastName: 'Smith',
      email: 'alice@example.com'
    };
  }
}
 Copy
![Data modification and reactivity - IMAGE PLACEHOLDER]

Data Properties are Local
Important: Data properties are component-scoped. They only exist within the component where they're defined.

// HomeComponent.vue
export default {
  data() {
    return {
      myAge: 35  // Only available in HomeComponent
    }
  }
}

// AboutComponent.vue
export default {
  data() {
    return {
      myAge: 25  // Different instance, independent from HomeComponent
    }
  }
}
 Copy
Each component instance has its own isolated data.

Working with Arrays
Looping Through Arrays
<template>
  <div>
    <div v-for="user in users" :key="user.id">
      {{ user.name }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [
        { id: 1, name: 'A' },
        { id: 2, name: 'B' },
        { id: 3, name: 'C' }
      ]
    }
  }
}
</script>
 Copy
Filtering Arrays
computed: {
  activeUsers() {
    return this.users.filter(user => user.active);
  }
}
 Copy
Common Patterns
Pattern 1: Toggle Boolean
data() {
  return {
    isVisible: false
  }
},
methods: {
  toggle() {
    this.isVisible = !this.isVisible;
  }
}
<template>
  <div>
    <button @click="toggle">Toggle</button>
    <p v-if="isVisible">Now you see me!</p>
  </div>
</template>
 Copy
Pattern 2: Form Input Binding
data() {
  return {
    username: '',
    email: ''
  }
}
<template>
  <form>
    <input v-model="username" placeholder="Username">
    <input v-model="email" placeholder="Email">
    <p>Username: {{ username }}</p>
    <p>Email: {{ email }}</p>
  </form>
</template>
 Copy
Pattern 3: Counter
data() {
  return {
    count: 0
  }
},
methods: {
  increment() {
    this.count++;
  },
  decrement() {
    this.count--;
  },
  reset() {
    this.count = 0;
  }
}
 Copy
Best Practices
✅ Always return an object from data()
✅ Initialize all properties (even if null/empty)
✅ Use descriptive property names
✅ Keep data structure simple and flat when possible
✅ Use null or appropriate defaults for optional data
❌ Don't directly mutate props (use data properties instead)
❌ Don't use reserved words as property names
Why is Data a Function?
// ✅ Correct - Function returns new object for each instance
data() {
  return {
    count: 0
  }
}

// ❌ Wrong - All instances would share the same object
data: {
  count: 0
}
 Copy
Using a function ensures each component instance gets its own isolated data object.

Summary
Data properties store component state
Defined as a function returning an object
Access with this.propertyName in script
Display with {{ propertyName }} in templates
Changes trigger automatic UI updates (reactivity)
Properties are local to each component instance

Computed Properties
 Last updated: October 30, 2025
 
What are Computed Properties?
Computed properties are derived values that automatically update when their dependencies change. They're like formulas in a spreadsheet—when the input changes, the output recalculates automatically.

![Computed properties concept - IMAGE PLACEHOLDER]

Defining Computed Properties
Computed properties are defined as functions that return a value:

export default {
  data() {
    return {
      myAge: 35
    }
  },
  computed: {
    myAgeAfter10Years() {
      return this.myAge + 10;
    }
  }
}
 Copy
Using in Templates
Access computed properties just like data properties (no parentheses):

<template>
  <div>
    <p>Current Age: {{ myAge }}</p>
    <p>Age after 10 years: {{ myAgeAfter10Years }}</p>
  </div>
</template>
 Copy
Output:

Current Age: 35
Age after 10 years: 45
 Copy
![Computed property in template - IMAGE PLACEHOLDER]

How Computed Properties Work
Automatic Reactivity
When myAge changes, myAgeAfter10Years automatically recalculates:

export default {
  data() {
    return {
      myAge: 35
    }
  },
  computed: {
    myAgeAfter10Years() {
      return this.myAge + 10;  // Depends on myAge
    }
  },
  methods: {
    incrementAge() {
      this.myAge += 20;  // This triggers recalculation
    }
  }
}
 Copy
Flow:

Button clicked
myAge changes from 35 to 55
myAgeAfter10Years automatically recalculates to 65
Template updates to show new values
![Computed reactivity flow - IMAGE PLACEHOLDER]

Computed vs Methods
Methods Approach (Not Recommended for Display)
methods: {
  getAgeAfter10Years() {
    return this.myAge + 10;
  }
}
<template>
  <p>{{ getAgeAfter10Years() }}</p> <!-- Called every render -->
</template>
 Copy
Computed Approach (Recommended)
computed: {
  ageAfter10Years() {
    return this.myAge + 10;
  }
}
<template>
  <p>{{ ageAfter10Years }}</p> <!-- Cached, only recalculates when needed -->
</template>
 Copy
Key Differences
| Aspect               | Methods                            | Computed                            |
|----------------------|-------------------------------------|-------------------------------------|
| Caching              | ❌ No caching                       | ✅ Cached                          |
| Call syntax          | `method()` with `()`                | `property` without `()`             |
| Re-evaluation        | Every render                        | Only when dependencies change       |
| Use case             | Actions, events                     | Derived data, calculations          |
| Performance          | Lower (for display)                 | Higher (for display)                |

 Copy
Accessing Multiple Data Properties
export default {
  data() {
    return {
      firstName: 'John',
      lastName: 'Doe',
      age: 30
    }
  },
  computed: {
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    isAdult() {
      return this.age >= 18;
    },
    greeting() {
      return `Hello, ${this.fullName}! You are ${this.age} years old.`;
    }
  }
}
 Copy
Working with Arrays
export default {
  data() {
    return {
      users: [
        { id: 1, name: 'Alice', active: true },
        { id: 2, name: 'Bob', active: false },
        { id: 3, name: 'Charlie', active: true }
      ]
    }
  },
  computed: {
    activeUsers() {
      return this.users.filter(user => user.active);
    },
    userCount() {
      return this.users.length;
    },
    activeUserNames() {
      return this.activeUsers.map(user => user.name).join(', ');
    }
  }
}
 Copy
![Complex computed properties - IMAGE PLACEHOLDER]

Computed Properties with Dependencies
export default {
  data() {
    return {
      price: 100,
      quantity: 2,
      taxRate: 0.1
    }
  },
  computed: {
    subtotal() {
      return this.price * this.quantity;
    },
    tax() {
      return this.subtotal * this.taxRate;  // Depends on another computed
    },
    total() {
      return this.subtotal + this.tax;  // Depends on multiple computed
    }
  }
}
 Copy
Computed properties can depend on:

✅ Data properties
✅ Other computed properties
✅ Props
❌ Methods (they don't trigger reactivity)
Accessing in Script
Use this.computedPropertyName:

export default {
  data() {
    return {
      myAge: 35
    }
  },
  computed: {
    myAgeAfter10Years() {
      return this.myAge + 10;
    }
  },
  methods: {
    logAge() {
      console.log(this.myAgeAfter10Years);  // Access computed in method
    }
  },
  created() {
    console.log(this.myAgeAfter10Years);  // Access in lifecycle hook
  }
}
 Copy
Common Patterns
Pattern 1: Filtering Lists
data() {
  return {
    searchQuery: '',
    items: [
      { id: 1, title: 'Vue.js Guide' },
      { id: 2, title: 'React Tutorial' },
      { id: 3, title: 'Vue Router Docs' }
    ]
  }
},
computed: {
  filteredItems() {
    return this.items.filter(item => 
      item.title.toLowerCase().includes(this.searchQuery.toLowerCase())
    );
  }
}
 Copy
Pattern 2: Sorting Lists
data() {
  return {
    sortBy: 'name',
    users: [
      { id: 1, name: 'Charlie', age: 30 },
      { id: 2, name: 'Alice', age: 25 },
      { id: 3, name: 'Bob', age: 35 }
    ]
  }
},
computed: {
  sortedUsers() {
    return [...this.users].sort((a, b) => {
      return a[this.sortBy] > b[this.sortBy] ? 1 : -1;
    });
  }
}
 Copy
Pattern 3: Conditional Display
data() {
  return {
    user: {
      isLoggedIn: true,
      role: 'admin'
    }
  }
},
computed: {
  canEdit() {
    return this.user.isLoggedIn && this.user.role === 'admin';
  },
  userStatus() {
    return this.user.isLoggedIn ? 'Online' : 'Offline';
  }
}
<template>
  <button v-if="canEdit">Edit</button>
  <span>{{ userStatus }}</span>
</template>
 Copy
Performance Benefits
Caching Example
computed: {
  expensiveCalculation() {
    console.log('Computing...');
    let result = 0;
    for (let i = 0; i < 1000000; i++) {
      result += i;
    }
    return result;
  }
}
<template>
  <div>
    <p>{{ expensiveCalculation }}</p>  <!-- Computed once -->
    <p>{{ expensiveCalculation }}</p>  <!-- Uses cached value -->
    <p>{{ expensiveCalculation }}</p>  <!-- Uses cached value -->
  </div>
</template>
 Copy
Console output: "Computing..." appears only once (not three times)

![Computed caching benefit - IMAGE PLACEHOLDER]

Best Practices
✅ Use computed for derived data and calculations
✅ Keep computed properties pure (no side effects)
✅ Use descriptive names (e.g., fullName not getName)
✅ Return a value (computed must always return)
✅ Prefer computed over methods for template display
❌ Don't mutate data inside computed properties
❌ Don't make async calls in computed properties
❌ Don't use computed for event handlers (use methods)
When to Use Computed vs Methods
Use Computed When:
Displaying calculated/derived data
Filtering or transforming lists
Combining multiple data properties
Need caching for performance
Use Methods When:
Handling events (clicks, submits)
Performing actions
Making API calls
Need to pass parameters
Summary
Computed properties are cached derived values
Automatically update when dependencies change
Access like data properties (no parentheses)
Must return a value
Better performance than methods for display logic
Can depend on data, props, and other computed properties

Methods
 Last updated: October 30, 2025
 
What are Methods?
Methods are functions defined in your Vue component that can be called from templates or other methods. They're used for handling events, performing actions, and executing logic.

![Methods concept diagram - IMAGE PLACEHOLDER]

Defining Methods
Methods are defined in the methods object:

export default {
  data() {
    return {
      myAge: 35
    }
  },
  methods: {
    incrementAgeBy20() {
      this.myAge = this.myAge + 20;
    }
  }
}
 Copy
Pattern 4: Conditional Logic
data() {
  return {
    userRole: 'guest'
  }
},
methods: {
  checkPermission() {
    if (this.userRole === 'admin') {
      return this.grantAccess();
    } else if (this.userRole === 'user') {
      return this.grantLimitedAccess();
    } else {
      return this.denyAccess();
    }
  },
  grantAccess() {
    console.log('Full access granted');
  },
  grantLimitedAccess() {
    console.log('Limited access granted');
  },
  denyAccess() {
    console.log('Access denied');
  }
}
 Copy
Accessing Computed Properties in Methods
data() {
  return {
    myAge: 35
  }
},
computed: {
  myAgeAfter10Years() {
    return this.myAge + 10;
  }
},
methods: {
  logAges() {
    console.log('Current:', this.myAge);
    console.log('After 10 years:', this.myAgeAfter10Years);
  }
}
 Copy
Best Practices
✅ Use descriptive method names (verbs: incrementAge, fetchUsers)
✅ Keep methods focused on a single task
✅ Use parentheses when calling methods in templates
✅ Handle errors in async methods
✅ Use methods for actions and events
❌ Don't use methods for display logic (use computed instead)
❌ Don't mutate props directly (emit events instead)
❌ Avoid complex logic in templates (move to methods)
Methods vs Computed Properties
| Use **Methods** For          | Use **Computed** For              |
|------------------------------|-----------------------------------|
| Event handlers               | Derived/calculated data           |
| Actions                      | Filtering/transforming lists      |
| API calls                    | Combining data properties         |
| Side effects                 | Display logic                     |
| Passing parameters            | Values needing caching           | 
 Copy
Summary
Methods are functions defined in the methods object
Called from templates using @event="methodName()"
Access data with this.propertyName
Can be synchronous or asynchronous
Used for actions, events, and side effects
Can call other methods and computed properties
Should be focused and have single responsibility
Sub Pages


Calling Methods from Templates
 Last updated: October 30, 2025
 
Calling Methods from Templates
Event Handling with @click
<template>
  <v-btn @click="incrementAgeBy20()">Increment 20</v-btn>
</template>
 Copy
With or Without Parentheses
Both syntaxes work, but parentheses are recommended:

<!-- ✅ Recommended: Clear that it's a function call -->
<v-btn @click="incrementAgeBy20()">Click</v-btn>

<!-- ✅ Also works: Useful when no arguments -->
<v-btn @click="incrementAgeBy20">Click</v-btn>
 Copy
When parentheses are required:

<!-- Must use parentheses when passing arguments -->
<v-btn @click="incrementBy(20)">Increment by 20</v-btn>
<v-btn @click="incrementBy(50)">Increment by 50</v-btn>
 Copy
![Method calling syntax - IMAGE PLACEHOLDER]

Methods vs Inline Expressions
❌ Inline Expressions (Not Recommended)
<template>
  <v-btn @click="myAge = myAge + 20">Increment</v-btn>
</template>
 Copy
Problems:

Hard to read
Difficult to test
Can't be reused
Mixes logic with presentation
✅ Methods (Recommended)
<template>
  <v-btn @click="incrementAgeBy20()">Increment</v-btn>
</template>

<script>
export default {
  methods: {
    incrementAgeBy20() {
      this.myAge = this.myAge + 20;
    }
  }
}
</script>
 Copy
Benefits:

Clean and readable
Reusable
Testable
Separates logic from presentation
Accessing Data in Methods
Use this.propertyName to access data properties:

export default {
  data() {
    return {
      myAge: 35,
      myName: 'John'
    }
  },
  methods: {
    incrementAgeBy20() {
      // Access data property
      this.myAge = this.myAge + 20;
      
      // Shorthand
      this.myAge += 20;
    },
    logInfo() {
      console.log(this.myName);
      console.log(this.myAge);
    }
  }
}
 Copy
Methods with Parameters
Single Parameter
methods: {
  incrementBy(amount) {
    this.myAge += amount;
  }
}
<template>
  <v-btn @click="incrementBy(10)">+10</v-btn>
  <v-btn @click="incrementBy(20)">+20</v-btn>
  <v-btn @click="incrementBy(50)">+50</v-btn>
</template>
 Copy
Multiple Parameters
methods: {
  updateUser(name, age, country) {
    this.userName = name;
    this.userAge = age;
    this.userCountry = country;
  }
}
<template>
  <v-btn @click="updateUser('Alice', 30, 'USA')">Update User</v-btn>
</template>
 Copy
![Methods with parameters - IMAGE PLACEHOLDER]

Calling Methods from Other Methods
Methods can call other methods:

methods: {
  incrementBy20() {
    this.myAge += 20;
  },
  incrementBy50() {
    this.myAge += 50;
  },
  incrementBoth() {
    this.incrementBy20();  // Call another method
    this.incrementBy50();  // Call another method
  }
}
 Copy
Calling Methods from Lifecycle Hooks
export default {
  data() {
    return {
      myAge: 35
    }
  },
  methods: {
    incrementAgeBy20() {
      this.myAge += 20;
    },
    fetchUserData() {
      // Fetch data from API
    }
  },
  created() {
    // Call methods in lifecycle hooks
    this.incrementAgeBy20();
    this.fetchUserData();
  },
  mounted() {
    this.incrementAgeBy20();
  }
}
 Copy
Common Event Handlers
Click Events
<template>
  <v-btn @click="handleClick">Click Me</v-btn>
</template>

<script>
methods: {
  handleClick() {
    console.log('Button clicked!');
  }
}
</script>
 Copy
Form Submit
<template>
  <form @submit.prevent="handleSubmit">
    <input v-model="username">
    <button type="submit">Submit</button>
  </form>
</template>

<script>
methods: {
  handleSubmit() {
    console.log('Form submitted:', this.username);
  }
}
</script>
 Copy
Input Events
<template>
  <input @input="handleInput" @keyup.enter="handleEnter">
</template>

<script>
methods: {
  handleInput(event) {
    console.log('Input value:', event.target.value);
  },
  handleEnter() {
    console.log('Enter key pressed');
  }
}
</script>
 Copy
![Common event handlers - IMAGE PLACEHOLDER]

Async Methods
Methods can be asynchronous:

methods: {
  async fetchUsers() {
    try {
      const response = await fetch('/api/users');
      this.users = await response.json();
    } catch (error) {
      console.error('Error fetching users:', error);
    }
  },
  
  async saveData() {
    this.loading = true;
    try {
      await api.save(this.data);
      this.showSuccessMessage();
    } catch (error) {
      this.showErrorMessage(error);
    } finally {
      this.loading = false;
    }
  }
}
 Copy
Common Patterns
Pattern 1: Toggle Boolean
data() {
  return {
    isVisible: false
  }
},
methods: {
  toggle() {
    this.isVisible = !this.isVisible;
  }
}
<template>
  <v-btn @click="toggle">Toggle</v-btn>
  <div v-if="isVisible">Now you see me!</div>
</template>
 Copy
Pattern 2: Form Handling
data() {
  return {
    form: {
      username: '',
      email: '',
      password: ''
    }
  }
},
methods: {
  submitForm() {
    if (this.validateForm()) {
      this.sendToServer();
    }
  },
  validateForm() {
    return this.form.username && this.form.email && this.form.password;
  },
  sendToServer() {
    // API call
  },
  resetForm() {
    this.form = {
      username: '',
      email: '',
      password: ''
    };
  }
}
 Copy
Pattern 3: Array Manipulation
data() {
  return {
    items: []
  }
},
methods: {
  addItem(item) {
    this.items.push(item);
  },
  removeItem(index) {
    this.items.splice(index, 1);
  },
  updateItem(index, newValue) {
    this.items[index] = newValue;
  },
  clearAll() {
    this.items = [];
  }
}
 Copy


Watchers
 Last updated: October 30, 2025
 
What are Watchers?
Watchers observe specific data or computed properties and execute code whenever those properties change. They're useful for performing side effects in response to data changes.

![Watchers concept diagram - IMAGE PLACEHOLDER]

Defining Watchers
Watchers are defined in the watch object with a method name that exactly matches the property you want to watch:

export default {
  data() {
    return {
      myAge: 35
    }
  },
  watch: {
    myAge() {
      console.log('myAge has changed');
    }
  }
}
 Copy
⚠️ Critical Rule: The watcher name must exactly match the property name (including case).

![Watcher naming rule - IMAGE PLACEHOLDER]

Watching Data Properties
Basic Example
export default {
  data() {
    return {
      myAge: 35
    }
  },
  watch: {
    myAge() {
      console.log('myAge has changed');
    }
  },
  methods: {
    incrementAge() {
      this.myAge += 10;  // Triggers the watcher
    }
  }
}
 Copy
Flow:

incrementAge() called
myAge changes from 35 to 45
myAge watcher executes
Console: "myAge has changed"
Watching Computed Properties
You can also watch computed properties:

export default {
  data() {
    return {
      myAge: 35
    }
  },
  computed: {
    myAgeAfter10Years() {
      return this.myAge + 10;
    }
  },
  watch: {
    myAge() {
      console.log('myAge has changed');
    },
    myAgeAfter10Years() {
      console.log('myAgeAfter10Years computed property has changed');
    }
  }
}
 Copy
Flow when myAge changes:

myAge changes (35 → 55)
myAge watcher executes → "myAge has changed"
myAgeAfter10Years recalculates (45 → 65)
myAgeAfter10Years watcher executes → "computed property has changed"
![Computed property watcher flow - IMAGE PLACEHOLDER]

Accessing New and Old Values
Watchers receive the new value and old value as parameters:

watch: {
  myAge(newValue, oldValue) {
    console.log(`Age changed from ${oldValue} to ${newValue}`);
  },
  username(newVal, oldVal) {
    console.log(`Username: "${oldVal}" → "${newVal}"`);
  }
}
 Copy
Example output:

Age changed from 35 to 55
Username: "john" → "jane"
 Copy
What Can Be Watched?
✅ Can watch:

Data properties
Computed properties
❌ Cannot watch:

Methods
Regular variables
Props (watch them in the component that owns them)
export default {
  data() {
    return {
      name: 'John',
      age: 30
    }
  },
  computed: {
    fullInfo() {
      return `${this.name} - ${this.age}`;
    }
  },
  watch: {
    name() { },        // ✅ Can watch data
    age() { },         // ✅ Can watch data
    fullInfo() { },    // ✅ Can watch computed
    
    // someMethod() { }  // ❌ Cannot watch methods
  }
}
 Copy
Complex Example: Complete Reactivity Flow
<template>
  <div>
    <p>Age: {{ myAge }}</p>
    <p>Age after 10 years: {{ myAgeAfter10Years }}</p>
    <v-btn @click="incrementAgeBy20()">Increment 20</v-btn>
  </div>
</template>

<script>
export default {
  data() {
    return {
      myAge: 35
    }
  },
  
  computed: {
    myAgeAfter10Years() {
      return this.myAge + 10;
    }
  },
  
  watch: {
    myAge() {
      console.log('1. myAge property will change now');
      console.log('2. myAge has changed');
    },
    myAgeAfter10Years() {
      console.log('3. myAgeAfter10Years computed property has changed');
    }
  },
  
  methods: {
    incrementAgeBy20() {
      console.log('0. Method called');
      this.myAge += 20;
    }
  }
}
</script>
 Copy
Execution order when button is clicked:

0. Method called
1. myAge property will change now
2. myAge has changed
3. myAgeAfter10Years computed property has changed
 Copy
![Complete reactivity flow - IMAGE PLACEHOLDER]

Deep Watching (Objects and Arrays)
Basic Object Watching (Shallow)
data() {
  return {
    user: {
      name: 'John',
      age: 30
    }
  }
},
watch: {
  user() {
    // Only triggers when entire object is replaced
    console.log('User object changed');
  }
}
 Copy
This only triggers when you do:

this.user = { name: 'Jane', age: 25 };  // ✅ Triggers
 Copy
But NOT when you do:

this.user.name = 'Jane';  // ❌ Doesn't trigger (shallow watch)
 Copy
Deep Watching
To watch nested properties, use deep: true:

watch: {
  user: {
    handler(newValue, oldValue) {
      console.log('User changed deeply');
    },
    deep: true
  }
}
 Copy
Now it triggers for:

this.user.name = 'Jane';     // ✅ Triggers
this.user.age = 25;          // ✅ Triggers
this.user = { ... };         // ✅ Triggers
 Copy
Immediate Execution
By default, watchers only run when the property changes. To run immediately on component creation:

watch: {
  myAge: {
    handler(newValue) {
      console.log('Age is:', newValue);
    },
    immediate: true  // Runs on component creation
  }
}
 Copy
Common Use Cases
1. Search/Filter Logic
data() {
  return {
    searchQuery: '',
    searchResults: []
  }
},
watch: {
  searchQuery(newQuery) {
    if (newQuery.length >= 3) {
      this.performSearch(newQuery);
    } else {
      this.searchResults = [];
    }
  }
},
methods: {
  async performSearch(query) {
    this.searchResults = await api.search(query);
  }
}
 Copy
2. API Calls on Data Change
data() {
  return {
    userId: null,
    userData: null
  }
},
watch: {
  userId(newId) {
    if (newId) {
      this.fetchUserData(newId);
    }
  }
},
methods: {
  async fetchUserData(id) {
    this.userData = await api.getUser(id);
  }
}
 Copy
3. Local Storage Sync
data() {
  return {
    preferences: {
      theme: 'light',
      language: 'en'
    }
  }
},
watch: {
  preferences: {
    handler(newPreferences) {
      localStorage.setItem('prefs', JSON.stringify(newPreferences));
    },
    deep: true
  }
}
 Copy
4. Validation
data() {
  return {
    email: '',
    emailError: ''
  }
},
watch: {
  email(newEmail) {
    if (!this.isValidEmail(newEmail)) {
      this.emailError = 'Invalid email format';
    } else {
      this.emailError = '';
    }
  }
},
methods: {
  isValidEmail(email) {
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
  }
}
 Copy
![Common watcher use cases - IMAGE PLACEHOLDER]

Watchers vs Computed Properties
| Use **Watchers** For                     | Use **Computed** For                 |
|------------------------------------------|--------------------------------------|
| Side effects (API calls, logging)        | Deriving data from other data        |
| Async operations                         | Synchronous calculations             |
| Reacting to changes                      | Transforming data for display        |
| Multiple property dependencies           | Single derived value                 |
| Complex logic with conditions            | Simple transformations               | 
 Copy
Example: When to Use What
❌ Wrong - Using watcher for derived data:

data() {
  return {
    firstName: 'John',
    lastName: 'Doe',
    fullName: ''
  }
},
watch: {
  firstName(val) {
    this.fullName = val + ' ' + this.lastName;
  },
  lastName(val) {
    this.fullName = this.firstName + ' ' + val;
  }
}
 Copy
✅ Right - Using computed:

data() {
  return {
    firstName: 'John',
    lastName: 'Doe'
  }
},
computed: {
  fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
 Copy
Best Practices
✅ Use watchers for side effects and async operations
✅ Use computed properties for derived data
✅ Match watcher names exactly to property names
✅ Use deep: true for nested object/array watching
✅ Use immediate: true when you need initial execution
❌ Don't use watchers for simple data transformations (use computed)
❌ Don't create complex chains of watchers
❌ Don't forget to handle errors in async watchers
Summary
Watchers observe data and computed properties for changes
Execute code when watched properties change
Watcher names must exactly match property names
Receive newValue and oldValue as parameters
Use for side effects, API calls, and async operations
Can watch deeply with deep: true
Can run immediately with immediate: true

Complete Example: All Concepts Together
 Last updated: October 30, 2025
 
Overview
This guide demonstrates how data properties, computed properties, methods, watchers, and lifecycle hooks work together in a real component.

![Complete component architecture - IMAGE PLACEHOLDER]

Full Component Example
<template>
  <div class="user-component">
    <!-- Display Data -->
    <h2>{{ userName }}</h2>
    <p>Current Age: {{ userAge }}</p>
    <p>Age after 10 years: {{ ageAfter10Years }}</p>
    <p>Status: {{ userStatus }}</p>
    
    <!-- Action Buttons -->
    <v-btn @click="incrementAge(10)">Add 10 Years</v-btn>
    <v-btn @click="incrementAge(20)">Add 20 Years</v-btn>
    <v-btn @click="resetAge()">Reset Age</v-btn>
    <v-btn @click="toggleStatus()">Toggle Status</v-btn>
    
    <!-- User List -->
    <div class="users-list">
      <h3>Users ({{ userCount }})</h3>
      <div v-for="user in filteredUsers" :key="user.id">
        {{ user.name }} - {{ user.age }} years old
      </div>
    </div>
    
    <!-- Search -->
    <input v-model="searchQuery" placeholder="Search users...">
  </div>
</template>

<script>
export default {
  // =====================================
  // DATA PROPERTIES
  // =====================================
  data() {
    return {
      userName: 'John Doe',
      userAge: 35,
      isActive: true,
      searchQuery: '',
      users: [
        { id: 1, name: 'Alice', age: 28 },
        { id: 2, name: 'Bob', age: 35 },
        { id: 3, name: 'Charlie', age: 42 },
        { id: 4, name: 'Diana', age: 31 }
      ],
      initialAge: 35,
      ageChangeCount: 0
    }
  },
  
  // =====================================
  // COMPUTED PROPERTIES
  // =====================================
  computed: {
    // Simple computed
    ageAfter10Years() {
      return this.userAge + 10;
    },
    
    // Conditional computed
    userStatus() {
      return this.isActive ? 'Active' : 'Inactive';
    },
    
    // Array filtering
    filteredUsers() {
      if (!this.searchQuery) {
        return this.users;
      }
      return this.users.filter(user => 
        user.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
    
    // Array derived data
    userCount() {
      return this.users.length;
    },
    
    // Multiple dependencies
    ageChangeMessage() {
      return `Age changed ${this.ageChangeCount} times from initial age of ${this.initialAge}`;
    }
  },
  
  // =====================================
  // WATCHERS
  // =====================================
  watch: {
    // Watch data property
    userAge(newAge, oldAge) {
      console.log(`Age changed: ${oldAge} → ${newAge}`);
      this.ageChangeCount++;
    },
    
    // Watch computed property
    ageAfter10Years(newValue) {
      console.log(`Future age is now: ${newValue}`);
    },
    
    // Watch with conditions
    searchQuery(newQuery) {
      console.log(`Searching for: ${newQuery}`);
      if (newQuery.length > 3) {
        console.log('Search query is long enough');
      }
    },
    
    // Deep watch for objects
    users: {
      handler(newUsers) {
        console.log('Users array changed');
        console.log(`Total users: ${newUsers.length}`);
      },
      deep: true
    }
  },
  
  // =====================================
  // METHODS
  // =====================================
  methods: {
    // Method with parameter
    incrementAge(amount) {
      this.userAge += amount;
    },
    
    // Simple method
    resetAge() {
      this.userAge = this.initialAge;
      this.ageChangeCount = 0;
    },
    
    // Toggle method
    toggleStatus() {
      this.isActive = !this.isActive;
    },
    
    // Method calling another method
    addUserAndLog(name, age) {
      this.addUser(name, age);
      this.logUsers();
    },
    
    // Array manipulation
    addUser(name, age) {
      const newId = this.users.length + 1;
      this.users.push({ id: newId, name, age });
    },
    
    // Logging method
    logUsers() {
      console.log('Current users:', this.users);
    },
    
    // Async method
    async fetchUsers() {
      console.log('Fetching users...');
      // Simulated API call
      await new Promise(resolve => setTimeout(resolve, 1000));
      this.users = [
        { id: 1, name: 'Alice', age: 28 },
        { id: 2, name: 'Bob', age: 35 }
      ];
      console.log('Users fetched!');
    }
  },
  
  // =====================================
  // LIFECYCLE HOOKS
  // =====================================
  created() {
    console.log('Component created');
    console.log(`Initial age: ${this.userAge}`);
    console.log(`Initial computed age: ${this.ageAfter10Years}`);
    
    // Can call methods in lifecycle hooks
    this.logUsers();
  },
  
  mounted() {
    console.log('Component mounted to DOM');
    console.log('Component is now visible to user');
    
    // Example: Focus on search input
    // this.$refs.searchInput.focus();
  },
  
  destroyed() {
    console.log('Component destroyed');
    console.log('Performing cleanup...');
    
    // Cleanup operations would go here
    // Clear timers, remove event listeners, etc.
  }
}
</script>
 Copy
Execution Flow Walkthrough
Scenario 1: Component Initialization
Order of execution:

created() hook runs
Console: "Component created"
Console: "Initial age: 35"
Console: "Initial computed age: 45"
logUsers() called
Console: "Current users: [...]"
mounted() hook runs
Console: "Component mounted to DOM"
Console: "Component is now visible to user"
![Component initialization flow - IMAGE PLACEHOLDER]

Scenario 2: Button Click - "Add 10 Years"
What happens when user clicks "Add 10 Years" button:

1. @click="incrementAge(10)" triggers
2. incrementAge(10) method executes
3. this.userAge changes: 35 → 45
4. userAge watcher triggers
   └─ Console: "Age changed: 35 → 45"
   └─ this.ageChangeCount increments: 0 → 1
5. ageAfter10Years computed recalculates: 45 → 55
6. ageAfter10Years watcher triggers
   └─ Console: "Future age is now: 55"
7. Template updates with new values
 Copy
![Button click execution flow - IMAGE PLACEHOLDER]

Scenario 3: Search Input Change
What happens when user types in search box:

1. v-model="searchQuery" binding activates
2. searchQuery data property updates: "" → "ali"
3. searchQuery watcher triggers
   └─ Console: "Searching for: ali"
   └─ Condition check: "ali".length > 3 is false
4. filteredUsers computed recalculates
   └─ Filters users array
   └─ Returns users matching "ali"
5. Template updates to show filtered results
 Copy
Scenario 4: Component Navigation
What happens when navigating away from component:

1. Route changes (e.g., navigate to /about)
2. destroyed() hook executes
   └─ Console: "Component destroyed"
   └─ Console: "Performing cleanup..."
3. Component removed from DOM
4. All watchers stop watching
5. All data is cleared from memory
 Copy
![Component destruction flow - IMAGE PLACEHOLDER]

Property Access Patterns Reference
In Templates (HTML)
<!-- Data properties -->
{{ userName }}
{{ userAge }}

<!-- Computed properties -->
{{ ageAfter10Years }}
{{ userStatus }}

<!-- Methods (with parentheses) -->
<v-btn @click="incrementAge(10)">Click</v-btn>

<!-- No 'this' keyword in templates -->
<!-- ❌ Wrong: {{ this.userName }} -->
<!-- ✅ Right: {{ userName }} -->
 Copy
In Script (JavaScript)
// Data properties
this.userName
this.userAge

// Computed properties
this.ageAfter10Years
this.userStatus

// Methods
this.incrementAge(10)
this.resetAge()

// Always use 'this' keyword in script
 Copy
Data Flow Diagram
User Action (Button Click)
         ↓
    Method Executes
         ↓
  Data Property Changes
         ↓
    Watcher Triggers (logs, side effects)
         ↓
  Computed Properties Recalculate
         ↓
    Computed Watchers Trigger
         ↓
    Template Updates (UI reflects changes)
 Copy
![Complete data flow diagram - IMAGE PLACEHOLDER]

Key Takeaways
1. Reactivity Chain
Data changes trigger watchers
Data changes cause computed properties to recalculate
Computed changes can trigger their own watchers
All changes update the template automatically
2. Lifecycle Integration
Use created() for initialization and API calls
Use mounted() for DOM-dependent operations
Use destroyed() for cleanup
Methods can be called from lifecycle hooks
3. Separation of Concerns
Data: Store state
Computed: Derive and transform data
Methods: Handle actions and events
Watchers: React to changes (side effects)
4. Access Patterns
Templates: No this, just property names
Script: Always use this.propertyName
Attributes: No mustache syntax {{ }}
Common Mistakes to Avoid
❌ Mistake 1: Using this in Templates
<!-- Wrong -->
<p>{{ this.userName }}</p>

<!-- Right -->
<p>{{ userName }}</p>
 Copy
❌ Mistake 2: Not Using Parentheses for Methods with Parameters
<!-- Wrong -->
<v-btn @click="incrementAge">Add</v-btn>

<!-- Right -->
<v-btn @click="incrementAge(10)">Add</v-btn>
 Copy
❌ Mistake 3: Using Watchers Instead of Computed
// Wrong - Using watcher for derived data
watch: {
  firstName() {
    this.fullName = this.firstName + ' ' + this.lastName;
  }
}

// Right - Using computed
computed: {
  fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
 Copy
❌ Mistake 4: Watcher Name Mismatch
data() {
  return {
    userAge: 35
  }
},
watch: {
  age() {  // ❌ Wrong - doesn't match 'userAge'
    // This will never execute
  }
}
 Copy
Best Practices Summary
✅ Use data for component state
✅ Use computed for derived/calculated values
✅ Use methods for actions and event handlers
✅ Use watchers for side effects when data changes
✅ Call methods from lifecycle hooks for initialization
✅ Keep components focused and single-purpose
✅ Clean up in destroyed() hook
✅ Use descriptive naming for all properties and methods
Summary
This complete example demonstrates:

How all Vue component features work together
The execution flow from user action to UI update
Proper property access patterns
Common patterns and best practices
How lifecycle hooks integrate with other features
Understanding this flow is crucial for building reactive, maintainable Vue applications.


State Management Overview
 Last updated: November 4, 2025
state
store
data
Overview
This application uses a custom Vuex store implementation for centralized state management. The store allows you to create and access variables and methods across all components within the same hierarchy, providing a powerful way to share data and functionality throughout your application.

Why Use Global State?
Global state management offers several advantages:

Single Source of Truth: All shared data lives in one place
Cross-Component Communication: Easy data sharing without prop drilling
Better Maintainability: Centralized logic is easier to debug and update
Improved Code Quality: Reduces component coupling and improves reusability
Quick Start
Creating a Global Variable
created() {
  this.$store.dispatch('setVariable', { 
    key: 'sidebar', 
    value: false 
  });
}
 Copy
Accessing a Global Variable
In Template:

{{ $store.state.variable.sidebar }}
 Copy
In Script:

// Read
const sidebarState = this.$store.state.variable.sidebar;

// Write
this.$store.state.variable.sidebar = false;
 Copy
Creating a Global Method
created() {
  this.$store.dispatch('setMethod', { 
    name: 'getData', 
    fn: this.getData
  });
}

methods: {
  getData(args,args1,...) {
    // Method implementation
  }
}
 Copy
Accessing a Global Method
const ids = await this.$store.state.method.getData("books","pens",...);
 Copy
Organization Guidelines
Component Structure
To maintain a clean and scalable codebase, organize your global state using dedicated components:

1. GlobalVariables.vue - Variable Management Component
Create a centralized component to initialize all global variables:

<script>
export default {
  name: 'GlobalVariables',
  created() {
    // UI State
    this.$store.dispatch('setVariable', { key: 'sidebar', value: false });
    this.$store.dispatch('setVariable', { key: 'theme', value: 'light' });
    this.$store.dispatch('setVariable', { key: 'isLoading', value: false });
     
    // Application Data
    this.$store.dispatch('setVariable', { key: 'books', value: [] });
    this.$store.dispatch('setVariable', { key: 'selectedBook', value: null });
  }
}
</script>
 Copy
2. GlobalMethods.vue - Method Management Component
Create a centralized component to register all global methods:

<script>
export default {
  name: 'GlobalMethods',
  created() {
    // Register all global methods 
    this.$store.dispatch('setMethod', { name: 'fetchUserData', fn: this.fetchUserData });
    this.$store.dispatch('setMethod', { name: 'validateForm', fn: this.validateForm });
  },
  methods: { 
    fetchUserData(userId) {
      // Implementation
    },
    validateForm(formData) {
      // Implementation
    }
  }
}
</script>
 Copy
3. App.vue - Root Component Setup
Import and use the management components:

<template>
  <div >
    <GlobalVariables />
    <GlobalMethods />
    <router-view />
  </div>
</template>
 
 Copy
Best Practices
Naming Conventions
Variables:

Use camelCase: isLoading, currentUser, bookList
Be descriptive: sidebar ✓ vs sb ✗
Use boolean prefixes: isActive, hasPermission, shouldRender
Methods:

Use verb prefixes: getIDBtableIds, fetchUserData, validateForm
Be specific about action: updateUserProfile ✓ vs update ✗
Variable Organization by Category
Group related variables together:

// UI State Variables
this.$store.dispatch('setVariable', { key: 'sidebarOpen', value: false });
this.$store.dispatch('setVariable', { key: 'modalVisible', value: false });
this.$store.dispatch('setVariable', { key: 'currentTheme', value: 'light' });

// User Variables
this.$store.dispatch('setVariable', { key: 'userProfile', value: null });
this.$store.dispatch('setVariable', { key: 'userPermissions', value: [] });

// Data Variables
this.$store.dispatch('setVariable', { key: 'bookCollection', value: [] });
this.$store.dispatch('setVariable', { key: 'activeFilters', value: {} });
 Copy
Method Organization by Feature
Group methods by functionality:

// Data Fetching Methods
this.$store.dispatch('setMethod', { name: 'fetchBooks', fn: this.fetchBooks });
this.$store.dispatch('setMethod', { name: 'fetchUsers', fn: this.fetchUsers });

// Validation Methods
this.$store.dispatch('setMethod', { name: 'validateEmail', fn: this.validateEmail });
this.$store.dispatch('setMethod', { name: 'validatePassword', fn: this.validatePassword });

// Utility Methods
this.$store.dispatch('setMethod', { name: 'formatDate', fn: this.formatDate });
this.$store.dispatch('setMethod', { name: 'generateId', fn: this.generateId });
 Copy
Common Patterns
Pattern 1: Loading States
// Set loading state
this.$store.state.variable.isLoading = true;

try {
  const data = await this.$store.state.method.fetchData();
  this.$store.state.variable.data = data;
} finally {
  this.$store.state.variable.isLoading = false;
}
 Copy
Pattern 2: Toggle Functions
toggleSidebar() {
  this.$store.state.variable.sidebar = !this.$store.state.variable.sidebar;
}
 Copy
Pattern 3: Computed Properties
<script>
export default {
  computed: {
    isSidebarOpen() {
      return this.$store.state.variable.sidebar;
    },
    currentUser() {
      return this.$store.state.variable.currentUser;
    }
  }
}
</script>
 Copy
Data Types Support
The store supports all ES6 JavaScript data types:

Primitives
this.$store.dispatch('setVariable', { key: 'count', value: 0 });
this.$store.dispatch('setVariable', { key: 'title', value: 'Hello' });
this.$store.dispatch('setVariable', { key: 'isActive', value: true });
 Copy
Objects
this.$store.dispatch('setVariable', { 
  key: 'user', 
  value: { id: 1, name: 'John', email: 'john@example.com' } 
});
 Copy
Arrays
this.$store.dispatch('setVariable', { 
  key: 'items', 
  value: [1, 2, 3, 4, 5] 
});
 Copy
Maps & Sets
this.$store.dispatch('setVariable', { 
  key: 'userMap', 
  value: new Map() 
});
this.$store.dispatch('setVariable', { 
  key: 'uniqueIds', 
  value: new Set() 
});
 Copy
Troubleshooting
Variable Not Updating in Template
Problem: Changes to store variables don't reflect in the template.

Solution: Ensure you're modifying the variable correctly:

// Correct
this.$store.state.variable.sidebar = false;

// Also correct for objects
this.$store.state.variable.user = { ...updatedUser };
 Copy
Method Not Found
Problem: this.$store.state.method.methodName is not a function

Solution: Verify the method is registered in GlobalMethods.vue:

created() {
  this.$store.dispatch('setMethod', { 
    name: 'methodName', 
    fn: this.methodName 
  });
}
 Copy
Variable Undefined
Problem: Cannot read property 'variableName' of undefined

Solution: Ensure GlobalVariables.vue is loaded before accessing:

Check App.vue includes <GlobalVariables />
Verify the variable is initialized in GlobalVariables.vue
Next Steps
Examples and Use Cases
Need Help? Check the examples section for detailed code samples and common use cases.

Examples and Use Cases
 Last updated: November 4, 2025
 
Example 1: Complete GlobalVariables Component
<!-- components/GlobalVariables.vue -->
<script>
export default {
  name: 'GlobalVariables',
  created() {
    // ========== UI STATE ==========
    this.$store.dispatch('setVariable', { key: 'sidebarOpen', value: false });
    this.$store.dispatch('setVariable', { key: 'mobileMenuOpen', value: false });
    this.$store.dispatch('setVariable', { key: 'currentTheme', value: 'light' });
    this.$store.dispatch('setVariable', { key: 'notificationVisible', value: false });
    this.$store.dispatch('setVariable', { key: 'isLoading', value: false });
    this.$store.dispatch('setVariable', { key: 'modalData', value: null });
    
    // ========== USER STATE ==========
    this.$store.dispatch('setVariable', { key: 'currentUser', value: null });
    this.$store.dispatch('setVariable', { key: 'isAuthenticated', value: false });
    this.$store.dispatch('setVariable', { key: 'userPermissions', value: [] });
    this.$store.dispatch('setVariable', { key: 'userPreferences', value: {} });
    
    // ========== APPLICATION DATA ==========
    this.$store.dispatch('setVariable', { key: 'books', value: [] });
    this.$store.dispatch('setVariable', { key: 'selectedBook', value: null });
    this.$store.dispatch('setVariable', { key: 'searchQuery', value: '' });
    this.$store.dispatch('setVariable', { key: 'filterOptions', value: {
      category: 'all',
      sortBy: 'title',
      orderBy: 'asc'
    }});
    
    // ========== FORM STATE ==========
    this.$store.dispatch('setVariable', { key: 'formErrors', value: {} });
    this.$store.dispatch('setVariable', { key: 'isDirty', value: false });
    this.$store.dispatch('setVariable', { key: 'isSubmitting', value: false });
    
    // ========== CACHE & SETTINGS ==========
    this.$store.dispatch('setVariable', { key: 'cachedData', value: new Map() });
    this.$store.dispatch('setVariable', { key: 'apiBaseUrl', value: 'https://api.example.com' });
    this.$store.dispatch('setVariable', { key: 'appVersion', value: '1.0.0' });
  }
}
</script>
 Copy
Example 2: Complete GlobalMethods Component
<!-- components/GlobalMethods.vue -->
<script>
export default {
  name: 'GlobalMethods',
  created() {
    // Register all global methods
    this.$store.dispatch('setMethod', { name: 'getIDBtableIds', fn: this.getIDBtableIds });
    this.$store.dispatch('setMethod', { name: 'fetchBooks', fn: this.fetchBooks });
    this.$store.dispatch('setMethod', { name: 'saveBook', fn: this.saveBook });
    this.$store.dispatch('setMethod', { name: 'deleteBook', fn: this.deleteBook });
    this.$store.dispatch('setMethod', { name: 'validateEmail', fn: this.validateEmail });
    this.$store.dispatch('setMethod', { name: 'validatePassword', fn: this.validatePassword });
    this.$store.dispatch('setMethod', { name: 'formatDate', fn: this.formatDate });
    this.$store.dispatch('setMethod', { name: 'showNotification', fn: this.showNotification });
    this.$store.dispatch('setMethod', { name: 'authenticateUser', fn: this.authenticateUser });
  },
  methods: {
    // ========== DATABASE METHODS ==========
    async getIDBtableIds(tableName) {
      try {
        // IndexedDB implementation
        const db = await this.openDatabase();
        const transaction = db.transaction([tableName], 'readonly');
        const store = transaction.objectStore(tableName);
        const request = store.getAllKeys();
        
        return new Promise((resolve, reject) => {
          request.onsuccess = () => resolve(request.result);
          request.onerror = () => reject(request.error);
        });
      } catch (error) {
        console.error('Error fetching IDB table IDs:', error);
        return [];
      }
    },
    
    // ========== BOOK MANAGEMENT ==========
    async fetchBooks() {
      try {
        this.$store.state.variable.isLoading = true;
        const response = await fetch(`${this.$store.state.variable.apiBaseUrl}/books`);
        const books = await response.json();
        this.$store.state.variable.books = books;
        return books;
      } catch (error) {
        console.error('Error fetching books:', error);
        return [];
      } finally {
        this.$store.state.variable.isLoading = false;
      }
    },
    
    async saveBook(bookData) {
      try {
        this.$store.state.variable.isSubmitting = true;
        const response = await fetch(`${this.$store.state.variable.apiBaseUrl}/books`, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(bookData)
        });
        const savedBook = await response.json();
        
        // Update store
        this.$store.state.variable.books = [...this.$store.state.variable.books, savedBook];
        this.showNotification('Book saved successfully', 'success');
        return savedBook;
      } catch (error) {
        this.showNotification('Failed to save book', 'error');
        throw error;
      } finally {
        this.$store.state.variable.isSubmitting = false;
      }
    },
    
    async deleteBook(bookId) {
      try {
        await fetch(`${this.$store.state.variable.apiBaseUrl}/books/${bookId}`, {
          method: 'DELETE'
        });
        
        // Update store
        this.$store.state.variable.books = this.$store.state.variable.books.filter(
          book => book.id !== bookId
        );
        this.showNotification('Book deleted successfully', 'success');
      } catch (error) {
        this.showNotification('Failed to delete book', 'error');
        throw error;
      }
    },
    
    // ========== VALIDATION METHODS ==========
    validateEmail(email) {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(email);
    },
    
    validatePassword(password) {
      // At least 8 characters, 1 uppercase, 1 lowercase, 1 number
      return password.length >= 8 && 
             /[A-Z]/.test(password) && 
             /[a-z]/.test(password) && 
             /[0-9]/.test(password);
    },
    
    // ========== UTILITY METHODS ==========
    formatDate(date, format = 'YYYY-MM-DD') {
      const d = new Date(date);
      const year = d.getFullYear();
      const month = String(d.getMonth() + 1).padStart(2, '0');
      const day = String(d.getDate()).padStart(2, '0');
      
      switch (format) {
        case 'YYYY-MM-DD':
          return `${year}-${month}-${day}`;
        case 'MM/DD/YYYY':
          return `${month}/${day}/${year}`;
        case 'DD/MM/YYYY':
          return `${day}/${month}/${year}`;
        default:
          return `${year}-${month}-${day}`;
      }
    },
    
    showNotification(message, type = 'info') {
      this.$store.state.variable.notificationVisible = true;
      this.$store.state.variable.modalData = { message, type };
      
      setTimeout(() => {
        this.$store.state.variable.notificationVisible = false;
      }, 3000);
    },
    
    // ========== AUTHENTICATION ==========
    async authenticateUser(credentials) {
      try {
        const response = await fetch(`${this.$store.state.variable.apiBaseUrl}/auth/login`, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(credentials)
        });
        
        const userData = await response.json();
        this.$store.state.variable.currentUser = userData;
        this.$store.state.variable.isAuthenticated = true;
        this.$store.state.variable.userPermissions = userData.permissions || [];
        
        return userData;
      } catch (error) {
        this.showNotification('Authentication failed', 'error');
        throw error;
      }
    }
  }
}
</script>
 Copy
Example 3: Using Global State in Components
Sidebar Component
<!-- components/Sidebar.vue -->
<template>
  <aside :class="{ 'open': isSidebarOpen }">
    <button @click="toggleSidebar">
      {{ isSidebarOpen ? 'Close' : 'Open' }} Menu
    </button>
    
    <nav v-if="isSidebarOpen">
      <ul>
        <li v-for="item in menuItems" :key="item.id">
          {{ item.title }}
        </li>
      </ul>
    </nav>
  </aside>
</template>

<script>
export default {
  name: 'Sidebar',
  computed: {
    isSidebarOpen() {
      return this.$store.state.variable.sidebarOpen;
    }
  },
  methods: {
    toggleSidebar() {
      this.$store.state.variable.sidebarOpen = !this.$store.state.variable.sidebarOpen;
    }
  }
}
</script>
 Copy
Book List Component
<!-- components/BookList.vue -->
<template>
  <div class="book-list">
    <div v-if="isLoading" class="loading">Loading books...</div>
    
    <div v-else>
      <input 
        v-model="searchQuery" 
        @input="updateSearch"
        placeholder="Search books..."
      />
      
      <div class="filters">
        <select v-model="filterCategory" @change="applyFilters">
          <option value="all">All Categories</option>
          <option value="fiction">Fiction</option>
          <option value="nonfiction">Non-Fiction</option>
        </select>
      </div>
      
      <div v-for="book in filteredBooks" :key="book.id" class="book-item">
        <h3>{{ book.title }}</h3>
        <p>{{ book.author }}</p>
        <button @click="selectBook(book)">View Details</button>
        <button @click="handleDeleteBook(book.id)">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BookList',
  data() {
    return {
      filterCategory: 'all'
    };
  },
  computed: {
    isLoading() {
      return this.$store.state.variable.isLoading;
    },
    books() {
      return this.$store.state.variable.books;
    },
    searchQuery: {
      get() {
        return this.$store.state.variable.searchQuery;
      },
      set(value) {
        this.$store.state.variable.searchQuery = value;
      }
    },
    filteredBooks() {
      let filtered = this.books;
      
      // Apply category filter
      if (this.filterCategory !== 'all') {
        filtered = filtered.filter(book => book.category === this.filterCategory);
      }
      
      // Apply search filter
      if (this.searchQuery) {
        const query = this.searchQuery.toLowerCase();
        filtered = filtered.filter(book => 
          book.title.toLowerCase().includes(query) ||
          book.author.toLowerCase().includes(query)
        );
      }
      
      return filtered;
    }
  },
  async created() {
    await this.$store.state.method.fetchBooks();
  },
  methods: {
    selectBook(book) {
      this.$store.state.variable.selectedBook = book;
      this.$router.push(`/books/${book.id}`);
    },
    async handleDeleteBook(bookId) {
      if (confirm('Are you sure you want to delete this book?')) {
        await this.$store.state.method.deleteBook(bookId);
      }
    },
    updateSearch() {
      // Search query is automatically updated via v-model
    },
    applyFilters() {
      this.$store.state.variable.filterOptions = {
        ...this.$store.state.variable.filterOptions,
        category: this.filterCategory
      };
    }
  }
}
</script>
 Copy
Login Form Component
<!-- components/LoginForm.vue -->
<template>
  <form @submit.prevent="handleSubmit">
    <h2>Login</h2>
    
    <div class="form-group">
      <label for="email">Email</label>
      <input 
        id="email"
        v-model="email" 
        type="email"
        :class="{ 'error': emailError }"
        @blur="validateEmailField"
      />
      <span v-if="emailError" class="error-message">{{ emailError }}</span>
    </div>
    
    <div class="form-group">
      <label for="password">Password</label>
      <input 
        id="password"
        v-model="password" 
        type="password"
        :class="{ 'error': passwordError }"
        @blur="validatePasswordField"
      />
      <span v-if="passwordError" class="error-message">{{ passwordError }}</span>
    </div>
    
    <button type="submit" :disabled="isSubmitting">
      {{ isSubmitting ? 'Logging in...' : 'Login' }}
    </button>
  </form>
</template>

<script>
export default {
  name: 'LoginForm',
  data() {
    return {
      email: '',
      password: '',
      emailError: '',
      passwordError: ''
    };
  },
  computed: {
    isSubmitting() {
      return this.$store.state.variable.isSubmitting;
    }
  },
  methods: {
    validateEmailField() {
      const isValid = this.$store.state.method.validateEmail(this.email);
      this.emailError = isValid ? '' : 'Please enter a valid email address';
      return isValid;
    },
    validatePasswordField() {
      const isValid = this.$store.state.method.validatePassword(this.password);
      this.passwordError = isValid 
        ? '' 
        : 'Password must be at least 8 characters with uppercase, lowercase, and numbers';
      return isValid;
    },
    async handleSubmit() {
      // Validate all fields
      const emailValid = this.validateEmailField();
      const passwordValid = this.validatePasswordField();
      
      if (!emailValid || !passwordValid) {
        return;
      }
      
      try {
        this.$store.state.variable.isSubmitting = true;
        
        const user = await this.$store.state.method.authenticateUser({
          email: this.email,
          password: this.password
        });
        
        this.$store.state.method.showNotification('Login successful!', 'success');
        this.$router.push('/dashboard');
      } catch (error) {
        console.error('Login failed:', error);
      } finally {
        this.$store.state.variable.isSubmitting = false;
      }
    }
  }
}
</script>
 Copy


Authentication
 Last updated: November 4, 2025
auth
login
user
Login
Syntax
this.$login({
  username: "identifier",  // Value can be username, email, or contact , but key remains username
  password: "password"
})
 Copy
Usage Examples
Login with Username:

await this.$login({
  username: "john_doe",
  password: "mySecurePass123"
});
 Copy
Login with Email:

await this.$login({
  username: "john@example.com",
  password: "mySecurePass123"
});
 Copy
Login with Contact:

await this.$login({
  username: "9876543210",
  password: "mySecurePass123"
});
 Copy
Note: The parameter key is always username, regardless of whether you're using username, email, or contact to log in.


Login Component
<template>
  <div class="login-form">
    <h2>Login</h2>
    <form @submit.prevent="handleLogin">
      <input 
        v-model="credentials.username" 
        type="text"
        placeholder="Username / Email / Contact"
        required
      />
      <input 
        v-model="credentials.password" 
        type="password"
        placeholder="Password"
        required
      />
      <button type="submit" :disabled="isLoading">
        {{ isLoading ? 'Logging in...' : 'Login' }}
      </button>
      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      credentials: { username: '', password: '' },
      isLoading: false,
      errorMessage: ''
    };
  },
  methods: {
    async handleLogin() {
      this.isLoading = true;
      this.errorMessage = '';
      
      try {
        await this.$login(this.credentials);
        this.$router.push('/dashboard');
      } catch (error) {
        this.errorMessage = error.message || 'Login failed';
      } finally {
        this.isLoading = false;
      }
    }
  }
}
</script>
 Copy
Registration
Required Fields
All users must have these mandatory fields:

Field Type Description
| Field     | Type   | Description            |
|------------|--------|------------------------|
| username   | String | Unique username        |
| email      | String | User’s email address   |
| contact    | String | User’s contact number  |
| password   | String | User’s password        |
 Copy
Registration Process
Make API call with this.$axios containing all user data
After successful registration, automatically log in the user
Registration Component
<template>
  <div class="register-form">
    <h2>Create Account</h2>
    <form @submit.prevent="handleRegister">
      <input v-model="userData.username" type="text" placeholder="Username" required />
      <input v-model="userData.email" type="email" placeholder="Email" required />
      <input v-model="userData.contact" type="tel" placeholder="Contact Number" required />
      <input v-model="userData.password" type="password" placeholder="Password" required />
      <input v-model="confirmPassword" type="password" placeholder="Confirm Password" required />
      
      <button type="submit" :disabled="isLoading">
        {{ isLoading ? 'Creating Account...' : 'Register' }}
      </button>
      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: {
        username: '',
        email: '',
        contact: '',
        password: ''
      },
      confirmPassword: '',
      isLoading: false,
      errorMessage: ''
    };
  },
  methods: {
    async handleRegister() {
      this.errorMessage = '';
      
      // Validate passwords match
      if (this.userData.password !== this.confirmPassword) {
        this.errorMessage = 'Passwords do not match';
        return;
      }
      
      this.isLoading = true;
      
      try {
        // Register user
        await this.$axios.post('/register', {f_name:'registerUser',this.userData});
        
        // Auto-login after successful registration
        await this.$login({
          username: this.userData.username,
          password: this.userData.password
        });
        
        this.$router.push('/dashboard');
      } catch (error) {
        this.errorMessage = error.response?.data?.message || 'Registration failed';
      } finally {
        this.isLoading = false;
      }
    }
  }
}
</script>
 Copy
Quick Reference
Login
// Login (works with username, email, or contact)
await this.$login({
  username: "user_identifier",
  password: "password"
});
 Copy
Register
// Step 1: Register
await this.$axios.post('/api/users/register', {
  username: "john_doe",
  email: "john@example.com",
  contact: "9876543210",
  password: "securePass123"
});

// Step 2: Auto-login
await this.$login({
  username: "john_doe",
  password: "securePass123"
});
 Copy
API Endpoint
POST /api/users/register

Request:

{
  "username": "john_doe",
  "email": "john@example.com",
  "contact": "9876543210",
  "password": "securePass123"
}
 Copy
Response:

{
  "success": true,
  "message": "User registered successfully",
  "userId": "12345"
}
 Copy
Database Schema
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  username VARCHAR(50) UNIQUE NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  contact VARCHAR(15) UNIQUE NOT NULL,
  password VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


Overview
All API calls in this application use this.$axios and must include an f_name parameter in the request body. The f_name represents the backend function that will be called to process the request.

Syntax
await this.$axios.post('/endpoint', {
  f_name: 'backendFunctionName',
  ...yourData
})
 Copy
Parameters
| Parameter | Type   | Required | Description                             |
|------------|--------|-----------|-----------------------------------------|
| f_name     | String | Yes       | Backend function name to call...        |
| data       | Any    | No        | Additional data required by the function |
 Copy
Advanced Patterns
Pattern 1: API Call with Multiple Parameters
const response = await this.$axios.post('/books/search', {
  f_name: 'searchBooks',
  query: 'javascript',
  category: 'programming',
  limit: 10,
  offset: 0,
  sortBy: 'title',
  orderBy: 'asc'
});
 Copy
Pattern 2: API Call with Array Data
await this.$axios.post('/books/bulk', {
  f_name: 'createMultipleBooks',
  books: [
    { title: 'Book 1', author: 'Author 1' },
    { title: 'Book 2', author: 'Author 2' },
    { title: 'Book 3', author: 'Author 3' }
  ]
});
 Copy
Pattern 3: API Call with Nested Objects
await this.$axios.post('/user/create', {
  f_name: 'createUserWithProfile',
  username: 'john_doe',
  email: 'john@example.com',
  profile: {
    firstName: 'John',
    lastName: 'Doe',
    age: 25,
    address: {
      street: '123 Main St',
      city: 'New York',
      zipCode: '10001'
    }
  }
});
 Copy
Pattern 4: File Upload
const formData = new FormData();
formData.append('f_name', 'uploadUserAvatar');
formData.append('userId', 123);
formData.append('avatar', fileInput.files[0]);

await this.$axios.post('/upload', formData, {
  headers: { 'Content-Type': 'multipart/form-data' }
});
 Copy
Error Handling
Basic Error Handling
try {
  const response = await this.$axios.post('/endpoint', {
    f_name: 'functionName',
    data: 'value'
  });
  
  console.log('Success:', response.data);
} catch (error) {
  console.error('Error:', error.message);
}
 Copy
Detailed Error Handling
try {
  const response = await this.$axios.post('/user/update', {
    f_name: 'updateUser',
    userId: 123,
    username: 'new_username'
  });
  
  if (response.data.success) {
    console.log('User updated successfully');
  }
} catch (error) {
  if (error.response) {
    // Server responded with error
    console.error('Server error:', error.response.data.message);
    console.error('Status code:', error.response.status);
  } else if (error.request) {
    // Request made but no response
    console.error('No response from server');
  } else {
    // Error setting up request
    console.error('Request error:', error.message);
  }
}
 Copy
Global Error Handler
// In GlobalMethods.vue
methods: {
  async apiCall(endpoint, functionName, data = {}) {
    try {
      const response = await this.$axios.post(endpoint, {
        f_name: functionName,
        ...data
      });
      return response.data;
    } catch (error) {
      // Handle error globally
      this.$store.state.method.showNotification(
        error.response?.data?.message || 'API call failed',
        'error'
      );
      throw error;
    }
  }
}

// Usage in components
const result = await this.$store.state.method.apiCall(
  '/books',
  'getAllBooks'
);
 Copy
Common API Calls Reference
User Operations
// Register
await this.$axios.post('/register', {
  f_name: 'registerUser',
  username, email, contact, password
});

// Get user by ID
await this.$axios.post('/user', {
  f_name: 'getUserById',
  userId: 123
});

// Update user
await this.$axios.post('/user/update', {
  f_name: 'updateUser',
  userId: 123,
  username: 'new_name'
});

// Delete user
await this.$axios.post('/user/delete', {
  f_name: 'deleteUser',
  userId: 123
});
 Copy
Book Operations
// Get all books
await this.$axios.post('/books', {
  f_name: 'getAllBooks'
});

// Get book by ID
await this.$axios.post('/books', {
  f_name: 'getBookById',
  bookId: 456
});

// Create book
await this.$axios.post('/books/create', {
  f_name: 'createBook',
  title: 'Book Title',
  author: 'Author Name',
  category: 'Fiction'
});

// Update book
await this.$axios.post('/books/update', {
  f_name: 'updateBook',
  bookId: 456,
  title: 'Updated Title'
});

// Delete book
await this.$axios.post('/books/delete', {
  f_name: 'deleteBook',
  bookId: 456
});

// Search books
await this.$axios.post('/books/search', {
  f_name: 'searchBooks',
  query: 'javascript',
  category: 'programming'
});

Examples
 Last updated: November 28, 2025
register
Basic Examples
Example 1: Register User
await this.$axios.post('/register', {
  f_name: 'registerUser',
  username: 'john_doe',
  email: 'john@example.com',
  contact: '9876543210',
  password: 'securePass123'
});
 Copy
Example 2: Fetch User Data
const response = await this.$axios.post('/user', {
  f_name: 'getUserById',
  userId: 123
});
 Copy
Example 3: Update Profile
await this.$axios.post('/user/update', {
  f_name: 'updateUserProfile',
  userId: 123,
  username: 'new_username',
  email: 'newemail@example.com'
});
 Copy
Example 4: Delete Record
await this.$axios.post('/user/delete', {
  f_name: 'deleteUser',
  userId: 123
});
 Copy
Complete Component Examples
User Registration
<template>
  <div>
    <form @submit.prevent="registerUser">
      <input v-model="userData.username" placeholder="Username" required />
      <input v-model="userData.email" placeholder="Email" required />
      <input v-model="userData.contact" placeholder="Contact" required />
      <input v-model="userData.password" type="password" placeholder="Password" required />
      <button type="submit">Register</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: {
        username: '',
        email: '',
        contact: '',
        password: ''
      }
    };
  },
  methods: {
    async registerUser() {
      try {
        const response = await this.$axios.post('/register', {
          f_name: 'registerUser',
          ...this.userData
        });
        
        console.log('Registration successful:', response.data);
      } catch (error) {
        console.error('Registration failed:', error);
      }
    }
  }
}
</script>
 Copy
Fetch and Display Data
<template>
  <div>
    <button @click="fetchBooks">Load Books</button>
    <div v-for="book in books" :key="book.id">
      {{ book.title }} - {{ book.author }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      books: []
    };
  },
  methods: {
    async fetchBooks() {
      try {
        const response = await this.$axios.post('/books', {
          f_name: 'getAllBooks'
        });
        
        this.books = response.data.books;
      } catch (error) {
        console.error('Failed to fetch books:', error);
      }
    }
  },
  mounted() {
    this.fetchBooks();
  }
}
</script>
 Copy
Update Data
<template>
  <div>
    <form @submit.prevent="updateBook">
      <input v-model="bookData.title" placeholder="Title" />
      <input v-model="bookData.author" placeholder="Author" />
      <button type="submit">Update Book</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bookData: {
        id: 1,
        title: '',
        author: ''
      }
    };
  },
  methods: {
    async updateBook() {
      try {
        const response = await this.$axios.post('/books/update', {
          f_name: 'updateBook',
          bookId: this.bookData.id,
          title: this.bookData.title,
          author: this.bookData.author
        });
        
        console.log('Book updated:', response.data);
      } catch (error) {
        console.error('Update failed:', error);
      }
    }
  }
}
</script>
 Copy
Delete Data
<script>
export default {
  methods: {
    async deleteBook(bookId) {
      if (confirm('Are you sure you want to delete this book?')) {
        try {
          await this.$axios.post('/books/delete', {
            f_name: 'deleteBook',
            bookId: bookId
          });
          
          console.log('Book deleted successfully');
        } catch (error) {
          console.error('Delete failed:', error);
        }
      }
    }
  }
}
</script>

Best Practices
 Last updated: November 28, 2025
 
Best Practices
1. Always Include f_name
// ✅ Correct
await this.$axios.post('/endpoint', {
  f_name: 'functionName',
  data: 'value'
});

// ❌ Wrong - missing f_name
await this.$axios.post('/endpoint', {
  data: 'value'
});
 Copy
2. Use Descriptive Function Names
// ✅ Good
f_name: 'getUserById'
f_name: 'createNewBook'
f_name: 'updateUserProfile'

// ❌ Bad
f_name: 'get'
f_name: 'create'
f_name: 'update'
 Copy
3. Spread Operator for Clean Code
// ✅ Clean
await this.$axios.post('/register', {
  f_name: 'registerUser',
  ...this.userData
});

// Also valid but more verbose
await this.$axios.post('/register', {
  f_name: 'registerUser',
  username: this.userData.username,
  email: this.userData.email,
  contact: this.userData.contact,
  password: this.userData.password
});
 Copy
4. Handle Loading States
async fetchData() {
  this.isLoading = true;
  try {
    const response = await this.$axios.post('/endpoint', {
      f_name: 'getData'
    });
    this.data = response.data;
  } catch (error) {
    console.error(error);
  } finally {
    this.isLoading = false;
  }
}
 Copy
Backend Function Mapping
The f_name parameter directly maps to backend functions:

| f_name        | Backend Function   | Description               |
|----------------|--------------------|----------------------------|
| registerUser   | registerUser()     | Create new user            |
| getUserById    | getUserById()      | Fetch user by ID           |
| getAllBooks    | getAllBooks()      | Fetch all books            |
| createBook     | createBook()       | Create new book            |
| updateBook     | updateBook()       | Update existing book       |
| deleteBook     | deleteBook()       | Delete book                |
| searchBooks    | searchBooks()      | Search books by query      |
 Copy
Response Format
Success Response
{
  "success": true,
  "message": "Operation successful",
  "data": {
    "id": 123,
    "username": "john_doe"
  }
}
 Copy
Error Response
{
  "success": false,
  "message": "Error message",
  "error": "Detailed error description"
}
 Copy


File Upload Documentation
Overview
File uploads use FormData() with files in files[] array and f_name for backend function. Files are stored in /dynamic/ folder with sanitized names.

Basic Syntax
const formData = new FormData();
formData.append('f_name', 'uploadFunction');
formData.append('files[]', fileObject);
formData.append('sanitizedFileName', sanitizedName);
formData.append('originalFileName', originalName);

await this.$axios.post('/upload', formData, {
  headers: { 'Content-Type': 'multipart/form-data' }
});
 Copy
File Name Sanitization
// Sanitize filename before upload
sanitizeFileName(originalName) {
  const timestamp = Date.now();
  const random = Math.floor(Math.random() * 1000);
  const extension = originalName.split('.').pop();
  const baseName = originalName.split('.').slice(0, -1).join('.')
    .replace(/[^a-zA-Z0-9]/g, '_');
  
  return `${baseName}_${timestamp}_${random}.${extension}`;
}
 Copy
Example:

Original: "My Lecture Video.mp4"
Sanitized: "My_Lecture_Video_1760693022_411.mp4"
 Copy
Single File Upload
<template>
  <div>
    <input type="file" @change="handleFileSelect" />
    <button @click="uploadFile">Upload</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedFile: null,
      lectureId: 123
    };
  },
  methods: {
    handleFileSelect(event) {
      this.selectedFile = event.target.files[0];
    },
    
    sanitizeFileName(originalName) {
      const timestamp = Date.now();
      const random = Math.floor(Math.random() * 1000);
      const extension = originalName.split('.').pop();
      const baseName = originalName.split('.').slice(0, -1).join('.')
        .replace(/[^a-zA-Z0-9]/g, '_');
      
      return `${baseName}_${timestamp}_${random}.${extension}`;
    },
    
    async uploadFile() {
      const originalFileName = this.selectedFile.name;
      const sanitizedFileName = this.sanitizeFileName(originalFileName);
      
      const formData = new FormData();
      formData.append('f_name', 'uploadLectureRecording');
      formData.append('files[]', this.selectedFile);
      formData.append('originalFileName', originalFileName);
      formData.append('sanitizedFileName', sanitizedFileName);
      formData.append('lecture_id', this.lectureId);
      
      try {
        const response = await this.$axios.post('/upload', formData, {
          headers: { 'Content-Type': 'multipart/form-data' }
        });
        console.log('Uploaded:', response.data);
      } catch (error) {
        console.error('Upload failed:', error);
      }
    }
  }
}
</script>
 Copy
Multiple Files Upload
methods: {
  handleFileSelect(event) {
    this.selectedFiles = Array.from(event.target.files);
  },
  
  async uploadFiles() {
    const formData = new FormData();
    formData.append('f_name', 'uploadMultipleFiles');
    formData.append('lecture_id', this.lectureId);
    
    // Append files with their names
    this.selectedFiles.forEach(file => {
      formData.append('files[]', file); 
      formData.append('sanitizedFileNames[]', this.sanitizeFileName(file.name));
    });
    
    await this.$axios.post('/upload', formData, {
      headers: { 'Content-Type': 'multipart/form-data' }
    });
  }
}
 Copy
Backend Example
internalFunction = async () => {
  const { record_id, sanitizedFileName } = req.body;
  
  if (req.files && req.files.length > 0) {
    // Update database with sanitized filename
    await dbQuery(req, 
      'UPDATE table_name SET fileName=? WHERE id=?', 
      [sanitizedFileName, record_id]
    );
    
    // Define upload directory in /dynamic/
    const uploadDir = '/dynamic/module-name/' + record_id + '/';
    
    // Remove and recreate directory
    if (fs.existsSync(req, uploadDir)) {
      fs.rmSync(req, uploadDir, { recursive: true, force: true });
    }
    fs.mkdirSync(req, uploadDir, { recursive: true });
    
    // Upload files
    await uploadFiles(req, uploadDir);
    
    res.json({ 
      success: true, 
      fileName: sanitizedFileName
    });
  }
}
 Copy
Accessing Uploaded Files
CDN URL Pattern
const fileUrl = `/api/getCdnFile/${userId}/dynamic/${path}/${sanitizedFileName}`;
 Copy
Example
// Component
computed: {
  videoUrl() {
    return `/api/getCdnFile/1000656/dynamic/live-class-lecture/${this.lectureId}/${this.sanitizedFileName}`;
  }
}
<video :src="videoUrl" controls></video>
<img :src="`/api/getCdnFile/${userId}/dynamic/live-class-lecture/${lectureId}/${thumbnailFile}`" />
 Copy
Upload with Progress
async upload() {
  const formData = new FormData();
  formData.append('f_name', 'uploadFile');
  formData.append('files[]', this.file);
  formData.append('originalFileName', this.file.name);
  formData.append('sanitizedFileName', this.sanitizeFileName(this.file.name));
  
  await this.$axios.post('/upload', formData, {
    headers: { 'Content-Type': 'multipart/form-data' },
    onUploadProgress: (progressEvent) => {
      this.uploadProgress = Math.round(
        (progressEvent.loaded * 100) / progressEvent.total
      );
    }
  });
}
 Copy
File Validation
validateFile(file) {
  // Size check (50MB)
  if (file.size > 50 * 1024 * 1024) {
    alert('File too large (max 50MB)');
    return false;
  }
  
  // Type check
  const allowedTypes = ['image/jpeg', 'image/png', 'video/mp4'];
  if (!allowedTypes.includes(file.type)) {
    alert('Invalid file type');
    return false;
  }
  
  return true;
}
 Copy
Storage Structure
/dynamic/
  └── live-class-lecture/
      └── {lecture_id}/
          ├── My_Lecture_Video_1760693022_411.mp4  (sanitized)
          └── thumbnailFile_1760693045_532.png     (sanitized)
 Copy
Quick Reference
Upload Single File
const formData = new FormData();
formData.append('f_name', 'uploadFile');
formData.append('files[]', file);
formData.append('originalFileName', file.name);
formData.append('sanitizedFileName', this.sanitizeFileName(file.name));
formData.append('id', 123);

await this.$axios.post('/upload', formData, {
  headers: { 'Content-Type': 'multipart/form-data' }
});
 Copy
Access File
const url = `/api/getCdnFile/${userId}/dynamic/${path}/${sanitizedFileName}`;
 Copy
Key Points
✅ Use FormData() for uploads
✅ files[] contains file objects
✅ Send both originalFileName and sanitizedFileName
✅ Sanitize format: baseName_timestamp_random.ext
✅ Store in /dynamic/ folder
✅ Access via /api/getCdnFile/{userId}/dynamic/{path}/{sanitizedFileName}
✅ Always include Content-Type: multipart/form-data header


WebSockets
 Last updated: November 4, 2025
websocket
realtime
events
Overview
Custom WebSocket implementation for real-time communication. Provides simple methods for joining rooms, sending events, and receiving messages.

Basic Usage
1. Join a Room
this.$ws.joinRoom('room_id');
 Copy
Connects the client to a specific room. Required before sending or receiving messages in that room.

2. Send Event
this.$ws.send({
  action: 'messageSent',
  payload: messageData,
  room: 'room_id'
});
 Copy
Broadcasts an event to all clients in the specified room. The action identifies the event type, payload contains your data, and room specifies the target room.

3. Listen for Events
this.$ws.onEvent('messageSent', (data) => {
  // Handle incoming event data
});
 Copy
Registers a listener for specific event types. Executes the callback when matching events are received from the server.

4. Leave a Room
this.$ws.leaveRoom('room_id');
 Copy
Disconnects the client from the room. Call when the user navigates away or no longer needs real-time updates.

Server-Side Events
Emit Event from Backend
emitEvent(req, {
  name: 'newNotification',
  room: `myroom-${user_id}`,
  data: { notificationDetail, status }
});
 Copy
Triggers events from the server to specific rooms. Useful for push notifications, system announcements, or remote UI control events. Allows the backend to initiate real-time updates without client requests.

Important Notes
Data Persistence: WebSocket events are transient and not stored automatically. Messages and notifications only exist in real-time transmission. To preserve history, implement separate API calls to save data to your database.

Event Flow: Events are broadcast to all room participants simultaneously. Handle sender filtering and duplicate prevention in your event listeners as needed.

Sub Pages

Grid System
Container, Row, and Column
<v-container>
  <v-row>
    <v-col cols="12" md="6">Left column</v-col>
    <v-col cols="12" md="6">Right column</v-col>
  </v-row>
</v-container>
 Copy
v-container: Centers content with responsive padding. Use fluid prop for full-width layouts.

v-row: Creates horizontal flex container for columns. Handles spacing and alignment.

v-col: Defines column width using 12-column grid. Responsive breakpoints: xs, sm, md, lg, xl.

Use Case: Page layouts, forms, card grids, responsive content sections.

Breakpoint Props
<v-col cols="12" sm="6" md="4" lg="3">
  Responsive column
</v-col>
 Copy
Columns adapt to screen sizes:

xs (< 600px): Mobile phones
sm (600-960px): Tablets portrait
md (960-1264px): Tablets landscape, small laptops
lg (1264-1904px): Desktops
xl (> 1904px): Large screens
Use Case: Mobile-first responsive designs that reorganize content based on screen size.

Spacing Utilities
Margin and Padding
<v-card class="ma-4 pa-6">Content</v-card>
<v-btn class="mt-2 mb-4 ml-auto">Button</v-btn>
 Copy
Pattern: {property}{direction}-{size}

Property: m (margin), p (padding)
Direction: t (top), b (bottom), l (left), r (right), x (horizontal), y (vertical), a (all)
Size: 0 to 16 (multiples of 4px)
Use Case: Fine-tune spacing between elements without custom CSS.

Flexbox Utilities
Alignment and Justification
<v-row align="center" justify="space-between">
  <v-col>Left</v-col>
  <v-col>Right</v-col>
</v-row>
 Copy
Align: Vertical alignment (start, center, end, baseline, stretch)

Justify: Horizontal distribution (start, center, end, space-between, space-around)

Use Case: Center content vertically/horizontally, create navbar layouts, space out elements evenly.

Application Layout
App Structure Components
<v-app>
  <v-app-bar app>Navbar</v-app-bar>
  <v-navigation-drawer app>Sidebar</v-navigation-drawer>
  <v-main>
    <v-container>Main content</v-container>
  </v-main>
  <v-footer app>Footer</v-footer>
</v-app>
 Copy
v-app: Root wrapper required for all Vuetify apps.

v-app-bar: Fixed top navigation bar. Use app prop to reserve layout space.

v-navigation-drawer: Sidebar menu. Can be permanent or toggleable.

v-main: Primary content area. Automatically adjusts for app bar and navigation drawer.

v-footer: Bottom footer section.

Use Case: Standard application shell with persistent navigation elements.

Common Layout Patterns
Centered Content
<v-container fill-height>
  <v-row align="center" justify="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>Login Form</v-card>
    </v-col>
  </v-row>
</v-container>
 Copy
Use Case: Login pages, splash screens, centered modals.

Dashboard Grid
<v-container>
  <v-row>
    <v-col v-for="card in cards" :key="card.id" cols="12" sm="6" lg="4">
      <v-card>{{ card.title }}</v-card>
    </v-col>
  </v-row>
</v-container>
 Copy
Use Case: Dashboards, product listings, image galleries.

Sidebar Layout
<v-row no-gutters>
  <v-col cols="3">
    <v-navigation-drawer permanent>Sidebar</v-navigation-drawer>
  </v-col>
  <v-col cols="9">
    <v-main>Content</v-main>
  </v-col>
</v-row>
 Copy
Use Case: Admin panels, documentation sites, file browsers.

Display Utilities
<v-card class="d-flex d-sm-none">Mobile only</v-card>
<v-btn class="hidden-md-and-down">Desktop only</v-btn>
 Copy
Display: d-{value} where value is none, inline, block, flex, etc.

Responsive Display: d-{breakpoint}-{value} or hidden-{breakpoint}-{direction}

Use Case: Show/hide elements based on screen size, create mobile-specific navigation.



