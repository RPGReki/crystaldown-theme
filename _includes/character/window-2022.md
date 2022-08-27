{% if page.termbase == "/crystaldown" %}
{% assign character = site.data.cd.characters[include.character] %}
{% elsif page.termbase == "/my-life-as-a-cat" %}
{% assign character = site.data.cat.characters[include.character] %}
{% endif %}

{:class="interface {{ include.class }}" style="order: 20"}
> Character Info
> {:onclick="toggleAccordion(this)" .inactive}
>
> |---------+--------------------------------------|
> |:--------|:-------------------------------------|{% unless include.no_name %}
> | Name:   | {{ character.name }}                 |{% endunless %}
> | Age:    | {{ character.age }}                  |
> | Species: | {{ character.species | join: '/' }} |
>
> {% unless include.no_titles %}{:.interface}
> > Titles & Blessings
> > {:onclick="toggleAccordion(this)" .inactive}
> >
> > {% for title in character.titles %}
> > - {{ title.name }} {% if title.requirements %}({{ title.requirements | array_to_sentence_string }}){% endif %}{% endfor %}
> >
> {% endunless %}
>
> {% unless include.no_traits %}{:.interface}
> > Traits
> > {:onclick="toggleAccordion(this)" .inactive}
> >
> > {% for trait in character.traits %}
> > - {{ trait.name }}{%if trait.type %} ({{trait.type}}){% endif %}{% endfor %}
> >
> {% endunless %}
>
> {% unless include.no_skills %}{:.interface}
> > Skills
> > {:onclick="toggleAccordion(this)" .inactive}
> >
> > {% for skill in character.skills %}
> > {:.interface}
> > > {{ skill.name }} {% if skill.level %} <span class="float-right">Level {% include ruby number=skill.level %}</span>{% endif %}
> > > {:onclick="toggleAccordion(this)" .inactive}
> > >
> > > {% for subskill in skill.subskills %}
> > > - {{ subskill.name }} <span class="float-right">Level {% include ruby number=subskill.level %}</span>{% endfor %}
> > >
> > {% endfor %}
> {% endunless %}
