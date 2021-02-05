# {{ name }}
{% if authors %}Authors: **{{ authors | join(', ') }}**{% endif %}

{% if compatibility %}
#### Compatibility
Versions: **{compatibility.version}**

{{ description }}

## Methods

{% for function in functions %}
### {{ function.name }}
{% if function.authors %}Authors: **{{ function.authors | join(', ') }}**{% endif %}

{{ function.description }}
{% if function.params %}
#### Parameters
name | description | units
--- | --- | ---
{% for param in function.params %}{{ param.name }} | {{ param.description }} | {{ param.units }}
{% endfor %}
{% endif %}

{% if function.throws %}
#### Throws
{% for throw in throws %}**{{ throw.type }}**: {{ throw.message }}  
{% endfor %}
{% endif %}
{% endfor %}
