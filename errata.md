# Errata for *Practical Internet Server Configuration*

Legend:

![No](images/no.png) : original text

![Yes](images/yes.png) : corrected text

---

**Page 363** : *bogofilter-train.sh*.

![No](images/no.png)
<pre>cat | bogofilter ${FLAG} &</pre>

![Yes](images/yes.png)
<pre>cat | bogofilter <strong>-d "${HOME}/bogofilter"</strong> ${FLAG} &</pre>

> This path should correspond to the path used in *bogo-dirs.sh* and *bogofilter-mail.sh*.
