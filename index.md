---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "dc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc")
venue: "University of Illinois"        # brief name of host site without address (e.g., "Euphoric State University")
address: "1030 National Center for Computing Applications, "      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: "us"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1)
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/ISO_639-1)
latlng: "40.1149832,-88.2271851"       # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use http://www.latlong.net/)
humandate: "October 18-19, 2018"  # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 am - 4:30 pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2018-10-18      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2018-10-19        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Ashley Hetrick","Dena Strong","Elizabeth Wickes", "Colleen Fallaw"] # boxed, comma-separated list of instructors' names as strings
helper: []     # boxed, comma-separated list of helpers' names
email: ["training@cse.illinois.edu"]    # boxed, comma-separated list of contact email addresses for the host
collaborative_notes: "http://pad.software-carpentry.org/2018-10-18-illinois"            # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
eventbrite: "50596034100"          # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
  HEADER

  Edit the values in the block above to be appropriate for your workshop.
  If the value is not 'true', 'false', 'null', or a number, please use
  double quotation marks around the value, unless specified otherwise.
  And run 'bin/workshop_check.py' *before* committing to make sure that changes are good.
{% endcomment %}

{% comment %}
  EVENTBRITE

  This block includes the Eventbrite registration widget if
  'eventbrite' has been set in the header.  You can delete it if you
  are not using Eventbrite, or leave it in, since it will not be
  displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="248px"
  scrolling="auto">
</iframe>
{% endif %}

<h2 id="general">General Information</h2>

{% comment %}
  INTRODUCTION

  Edit the general explanatory paragraph below if you want to change
  the pitch.
{% endcomment %}
<p>This hands-on workshop teaches basic concepts, skills and tools for working more effectively with data. The workshop is for anyone who has data they want to analyze, and no prior computational experience is required.</p>
{% comment %}
  AUDIENCE

  Explain who your audience is.  (In particular, tell readers if the
  workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  LOCATION

  This block displays the address and links to maps showing directions
  if the latitude and longitude of the workshop have been set.  You
  can use http://itouchmap.com/latlong.html to find the lat/long of an
  address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
  DATE

  This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
  SPECIAL REQUIREMENTS

  Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> Participants must bring a laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges
  on. They should have a few specific software packages installed (listed
  <a href="#setup">below</a>). They are also required to abide by
  {% if page.carpentry == "swc" %}
  Software Carpentry's
  {% elsif page.carpentry == "dc" %}
  Data Carpentry's
  {% elsif page.carpentry == "lc" %}
  Library Carpentry's
  {% endif %}
  <a href="{{site.swc_site}}/conduct.html">Code of Conduct</a>.
</p>

{% comment %}
  ACCESSIBILITY

  Modify the block below if there are any barriers to accessibility or
  special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop
  accessible to everybody.
  The workshop organisers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>

<p>
  <strong>Acknowledgments</strong>:
  Local Software Carpentry and Data Carpentry workshops are made possible by the generous support of Computational Science and Engineering, Technology Services, the National Center for Supercomputing Applications, HPCBio at the Roy J. Carver Biotechnology Center with support through the Office of the Vice Chancellor for Research, the Deloitte Center for Business Analytics at the Gies College of Business, and the home units of each of our instructors.
  </p>

{% comment %}
  CONTACT EMAIL ADDRESS

  Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Please email
  {% if page.email %}
    {% for email in page.email %}
      {% if forloop.last and page.email.size > 1 %}
        or
      {% else %}
        {% unless forloop.first %}
        ,
        {% endunless %}
      {% endif %}
      <a href='mailto:{{email}}'>{{email}}</a>
    {% endfor %}
  {% else %}
    to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% comment %}
  SCHEDULE

  Show the workshop's schedule.  Edit the items and times in the table
  to match your plans.  You may also want to change 'Day 1' and 'Day
  2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Schedule</h2>

{% comment %} DO NOT EDIT SURVEY LINKS {% endcomment %}
<p><em>Surveys</em></p>
{% if page.carpentry == "swc" %} 
<p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif page.carpentry == "dc" %}
  <p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif page.carpentry == "lc" %}
<p>Ask your instructor about pre- and post-workshop Survey details.</p>
{% endif %}


{% if page.carpentry == "swc" %}
  {% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/schedule.html %}
{% endif %}

{% comment %}
  Collaborative Notes

  If you want to use an Etherpad, go to

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  where 'YYYY-MM-DD-site' is the identifier for your workshop,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}

<hr/>

{% comment %}
  SYLLABUS

  Show what topics will be covered.

  1. If your workshop is R rather than Python, remove the comment
     around that section and put a comment around the Python section.
  2. Some workshops will delete SQL.
  3. Please make sure the list of topics is synchronized with what you
     intend to teach.
  4. You may need to move the div's with class="col-md-6" around inside
     the div's with class="row" to balance the multi-column layout.

  This is one of the places where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
  SETUP
  
  Delete irrelevant sections from the setup instructions.  Each
  section is inside a 'div' without any classes to make the beginning
  and end easier to find.

  This is the other place where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to the software described below.
  In addition, you will need an up-to-date web browser and a spreadsheet program such as Microsoft Excel or LibreOffice.
</p>

<div id="shell"> {% comment %} Shell section not needed for this class {% endcomment %}
</div> {% comment %} End of 'shell' section. {% endcomment %}

<div id="python"> {% comment %}Python being taught through web interface {% endcomment %}
  <h3>Python</h3>

  <p>
    <a href="https://python.org">Python</a> is a popular language for
    research computing, and great for general-purpose programming as
    well.
  </p>

    <p>
      We will teach Python using Repl,
      a programming environment that runs in a web browser. For this to work you will need a reasonably
      up-to-date browser. The current versions of the Chrome, Safari and
      Firefox browsers are all supported (some older browsers, including Internet Explorer version 9
      and below, are not).
    </p>

</div> {% comment %} End of 'Python' section. {% endcomment %}

<div id="sql"> {% comment %} Start of 'SQLite' section. {% endcomment %}
  <h3>SQLite and SQLiteStudio</h3>

  <p>
    SQL is a specialized programming language used with databases.  We
    use a simple database manager called
    <a href="https://www.sqlite.org/">SQLite</a> in our lessons.
  </p>
 <p>
 SQLite Studio provides a graphical user interface which combines helpful visual displays and
	point and click interactions with a command line-capable interface to allow you to
	interact with a database in the manner you prefer. See <a href="https://sqlitestudio.pl/index.rvt">the SQLite Studio website</a>
	for installation instructions.
</p>

</div> {% comment %} End of 'SQLite' section. {% endcomment %}

<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    For this lesson you will need <em>OpenRefine</em> and a
    web browser. <em>Note:</em> this is a Java program that runs on your machine (not in the cloud).
    It runs inside a web browser, but no web connection is needed.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="openrefine-windows">Windows</h4>
      <p>
        Check that you have either the Firefox or the Chrome browser installed and set as your default browser.
        <strong>OpenRefine runs in your default browser.</strong>
        It will not run correctly in Internet Explorer.
      </p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a></p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by right-clicking and selecting "Extract ...". </p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by clicking <code>google-refine.exe</code> (this will launch a command prompt window, but you can ignore that - just wait for OpenRefine to open in the browser).</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-mac">Mac</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong> It may not run correctly in Safari.</p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by double-clicking it.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by dragging the icon into the Applications folder.</p>
      <p>Use <code>Ctrl-click/Open ... </code> to launch it.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-linux">Linux</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong></p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Make a directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by entering <code>./refine</code> into the terminal within the OpenRefine directory.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
  </div>
</div> {% comment %} End of 'OpenRefine' section. {% endcomment %}

