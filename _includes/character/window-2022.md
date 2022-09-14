{% comment -%}
This include is a template for character windows.

Fields will be only shown if fields are non-empty.
Expected delimiters: ;,:

{%- endcomment %}

{:class="interface {{ include.class }}" style="order: 20"}
> Character Info
> {:onclick="toggleAccordion(this)" .inactive}
>
> |----------+--------------------------------------|---|
> |:---------|:-------------------------------------|---|{% if include.name %}
> | Name:    | {{ character.name }}                 |   |{% endif %}{% if include.age %}
> | Age:     | {{ character.age }}                  |   |{% endif %}{% if include.species %}
> | Species: | {{ include.species | join: '/' }}    |   |{% endif %}
>
> {% if include.titles %}{:.interface}
> > Titles & Blessings
> > {:onclick="toggleAccordion(this)" .inactive}
> >
> > {% for title_string in include.titles %}{% assign title_array = title_string | split: ';' %}{% assign title_requirements = title_array[1] | split: ',' %}
> > - {{ title_array[0] }} {% if title_requirements %}({{ title_requirements | array_to_sentence_string }}){% endif %}{% endfor %}
> >
> {% endif %}
>
> {% if include.traits %}{:.interface}
> > Traits
> > {:onclick="toggleAccordion(this)" .inactive}
> >
> > {% for trait_string in include.traits %}{% assign trait_array = trait_string | split: ';' %}
> > - {{ trait[0] }}{% if trait[1] %} ({{ trait[1] }}){% endif %}{% endfor %}
> >
> {% endif %}
>
> {% if include.skills %}{:.interface}
> > Skills
> > {:onclick="toggleAccordion(this)" .inactive}
> >
> > {% for skill_string in include.skills %}{% assign skill_array = skill_string | split: ';' %}
> > {:.interface}
> > > {{ skill_array[0] }} {% if skill_array[1] != "" %}{% assign level = skill_array[1] %} <span class="float-right">Level {% include ruby number=level %}</span>{% endif %}{% if skill_array[2] != "" %}
> > > {:onclick="toggleAccordion(this)" .inactive}{% assign subskills = skill_array[2] | split: ',' %}{% endif %}
> > >
> > > {% for subskill_string in subskills %}{% assign subskill_array = subskill_string | split: ':' %}
> > > - {{ subskill_array[0] }} <span class="float-right">Level {% assign level = subskill_array[1] %}{% include ruby number=level %}</span>{% endfor %}
> > >
> > {% endfor %}
> {% endif %}
