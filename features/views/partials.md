# Partials

### Location <a id="location"></a>

The view partial files are located in the `app/views/partials` directory.

### Convention <a id="convention"></a>

Despite views, partials and layouts having separate directories, it may sometimes get confusing having to deal with all three when working on your application.

Following Rails convention, file names for partials should ideally begin with an underscore.

### Typical example pattern <a id="typical-example-pattern"></a>

Suppose we have a portfolio website where projects are displayed on the `projects` page.

The `projects` page will be loaded with a layout, and so is not a full view itself. One typical approach would be:

{% code-tabs %}
{% code-tabs-item title="app/views/projects.erb" %}
```markup
<p>Here is a selection of a few projects that I have either:</p>
<ul>
    <li>Created myself</li>
    <li>Been an essential part of the development team</li>
</ul>
​
<div id="projects">
    <% @projects.each do |project| %>
    <div class="project">
        <h2><%= project[:title] %></h2>
        <p><%= project[:description] %></p>
        <%= link_to "Repository link", project[:link] %>
        <ul>
        <% project[:languages].each do |lang| %>
            <li><span><%= lang %></span></li>
        <% end %>
        </ul>
    </div>
    <% end %>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

But ideally view files should be clean, easy to read and most importantly, isolated from the logic.

Typically logic should be restricted to controllers, models and helpers \(as well as partials where appropriate\).

To clean this view file up, we will need a new partial containing all of the `erb` code necessary for displaying projects \(Simply copying the `ruby` code part from the above view file\).

{% code-tabs %}
{% code-tabs-item title="app/views/partials/\_projects.erb" %}
```markup
<div id="projects">
    <% @projects.each do |project| %>
    <div class="project">
        <h2><%= project[:title] %></h2>
        <p><%= project[:description] %></p>
        <%= link_to "Repository link", project[:link] %>
        <ul>
        <% project[:languages].each do |lang| %>
            <li><span><%= lang %></span></li>
        <% end %>
        </ul>
    </div>
    <% end %>
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

We can then clean up our `projects.erb` file by calling the `partial` function \(which is already defined in Eucalypt\) in the view:

{% code-tabs %}
{% code-tabs-item title="app/views/projects.erb" %}
```markup
<p>Here is a selection of a few projects that I have either:</p>
<ul>
    <li>Created myself</li>
    <li>Been an essential part of the development team</li>
</ul>
​
<%= partial 'partials/_projects' %>
<!-- Or alternatively -->
<%= partial '_projects' %>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

If you have variables that need to be used in the partial, simply pass them as keyword arguments in the `partial` function:

```markup
<%= partial '_projects', count: 10, top_lang: 'Ruby' %>
<!-- Or alternatively -->
<%= partial '_projects', {count: 10, top_lang: 'Ruby'} %>
```

The variables `count` and `top_lang` will then be usable in the partial's ERB file. They are treated as local variables, so just access them by their name.

