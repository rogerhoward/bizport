# Content Editing Instructions

## Overview

### Logging In
To log in to the CMS, first visit `/admin` and enter your username and password. If you're already able to view the "dashboard" (should have a couple of graphs/charts on it) at `/admin`, then you're logged in! Once you're in, change the URL to `/cms` to get to the CMS editing view.

## Writing in Markdown

The content in the CMS is stored as Markdown. This is a common open-source markup language that allows for easy-to-read text that renders with special formatting when users view a page.

http://dillinger.io/

## CMS Content Tags

The CMS

### General

The following tags can be used anywhere.

Youtube video embed: `{{ cms:partial:shared/video_embed_youtube:"https://www.youtube.com/embed/3ZtdlSmlC44" }}`

### Step Pages

```html
{{ cms:partial:shared/link_box:"https://paydirect.link2gov.com/LBCbuslicense/ItemSearch":"PAY":"Renewal Fee Online" }}
{{ cms:partial:shared/location_map:"SBDC: Downtown Long Beach Office":"309 Pine Ave, Long Beach, CA 90802" }}
{{ cms:partial:shared/contact_box_combo:"(562) 570-6211":"LBBIZ@longbeach.gov" }}
{{ cms:partial:shared/contact_box:"phone":"(562) 570-6105" }}
{{ cms:partial:shared/contact_box:"email":"test@example.com" }}

 <div class='callout'>
    NOTE:
  </div>
```

#### "Read More" Sections

To make a section of content collapse if it goes beyond a certain height (presently set at 600px), simply add the class `readmore-section` to the div wrapper for that content block.

Example:
```html
<div class='readmore-section'>
  <h2>Title of This Section</h2>
  <p>Copy for this section.</p>
</div>
```

### Contact Page

Each contact accordion section (for a particular agency, department, etc.) is created with the following code:

```html
<ul class="accordion modules" data-accordion="true" data-allow-all-closed="true">
  <li class="accordion-item modular-box" data-accordion-item="true">
    <a class="accordion-title step-group-title text-centered">
      <div class="step-group-title-text">
        <div class="text">
          <strong>Long Beach City Hall</strong>
          <div>Protects citizens through legal enforcement</div>
        </div>
        <div class="arrow"></div>
      </div>
    </a>
    <div class="accordion-content" data-tab-content="true">
      {{ cms:partial:shared/modular_box:'phone':'562-570-6555' }}
      {{ cms:partial:shared/modular_box:'hours':'7:30am-4:30pm M-F' }}
      {{ cms:partial:shared/modular_box:'map':"333 W Ocean Blvd, Long Beach, CA 90802" }}
      {{ cms:partial:shared/modular_box:'bus':"Metro Blue Line" }}
      {{ cms:partial:shared/modular_box:'bike':"Bike racks and bike share pods available." }}
      {{ cms:partial:shared/modular_box:'parking':"Parking is available at 332 West Broadway Avenue; the first 30 minutes are free, and each additional 20 minutes cost $1.25, with a maximum fee of $7.50. Metered parking is also available along Broadway and Cedar, directly in front of City Hall." }}
    </div>
  </li>
</ul>
```

Currently supported content types are `phone`, `email`, `hours`, `map`, `bus`, `bike`, `parking`. Note that content with line breaks (e.g. a list of different daily hours) is not supported with this module. If a particular section needs multi-line content, the module (`{{...}}`) can be replaced with the following HTML:

```html
<div class="contact-pane">
  <div class="contact-pane-section">
    <i class="icon icon-hours"></i> <!-- note that the class name here determines the icon -->
  </div>
  <div class="contact-pane-section">
    <!-- YOUR CUSTOM HTML HERE (e.g. list <ul> items) -->
  </div>
</div>
```