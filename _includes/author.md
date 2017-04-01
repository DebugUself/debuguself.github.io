{% assign author = site.authors[page.author] %}

    Author: <a href="{{ author.web }}">
    <img
      class="after"
      src="http://www.gravatar.com/avatar/{{ author.gravatar }}.png"
      alt="{{ author.display_name }}"
      width="32"
      height="32"
    >
    </a>
    <b><a href="{{ author.web }}">{{ author.display_name }}</a></b>

      <i>
        ;<a href="mailto:{{ author.email }}">mail</a>
      </i>

      <i>
        ;<a href="{{ author.gittip }}">
        gittip
        </a>
      </i>

    <i>
        ;<a href="https://github.com/{{ author.github }}">github</a>
      </i>


<br/>
