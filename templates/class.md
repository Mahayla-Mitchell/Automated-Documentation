# {{ name }}
{% if authors %}Authors: **{{ authors | join(', ') }}**{% endif %}

{{ description }}

```Python
    def makeModel(Te, Tc, mf, w):
        mfcoefs = mf
        wcoefs = w
    # ------------------------------------------------------------------------
    # Setting evaporating and condensing temperatures to test models
        Tevap = Te
        Tcond = Tc
    # This code uses the AHRI.py file to calculate coefficients given experimental data
        s = SimpleCompressor(mfcoefs, wcoefs)
        s.calc_mdot(Tevap, Tcond)
        s.calc_Wdot(Tevap, Tcond)
        m = s.mdot
        w = s.Wdot
        return m,w
    
     def testAnswer():
         mfcoefs = [.3, .5, .7, .5, .9, .4, .6, .4, .3, .5]
         wcoefs = [.4, .1, .8, .6, .7, .4, .8, .9, .5, .2]
         Tevap = 30
         Tcond = 120
    
         m,w = makeModel(Tevap, Tcond, mfcoefs, wcoefs)
         assert m > 0
  ```
## Methods

{% for function in functions %}
### {{ function.name }}
{% if function.authors %}Authors: **{{ function.authors | join(', ') }}**{% endif %}

{{ function.description }}
{% if function.params %}
#### Parameters
name | description | default
--- | --- | ---
{% for param in function.params %}{{ param.name }} | {{ param.description }} | {{ param.default }}
{% endfor %}
{% endif %}

{% if function.throws %}
#### Throws
{% for throw in throws %}**{{ throw.type }}**: {{ throw.message }}  
{% endfor %}
{% endif %}
{% endfor %}
