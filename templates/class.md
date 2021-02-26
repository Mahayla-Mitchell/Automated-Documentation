# {{ name }}
{% if authors %}Authors: **{{ authors | join(', ') }}**{% endif %}

{{ description }}

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

## Methods

{% for function in functions %}
### {{ function.name }}
{% if function.authors %}Authors: **{{ function.authors | join(', ') }}**{% endif %}

{{ function.description }}

{% if function.compatibility %}
#### Compatibility
Versions: **{{ function.compatibility | join(', ') }}**{% endif %}

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

#### Working Example
{% if example %}
{{ example | join('\n')}}{% endif %}
