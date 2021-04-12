# Errata for *Practical Internet Server Configuration*

Legend:

![No](images/no.png) : original text

![Yes](images/yes.png) : corrected text

---

**Page 332* : Apache Radicale configuration.

![No](images/no.png)
<pre>RequestHeader set X-Remote-User expr=%{REMOTE_USER}</pre>

![Yes](images/yes.png)
<pre><strong>RequestHeader set X-Script-Name /</strong>
RequestHeader set X-Remote-User expr=%{REMOTE_USER}</pre>

> The reverse proxy will not function without the *X-Script-Name* header.

---

**Page 333* : Nginx Radicale configuration.

![No](images/no.png)
<pre>proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;</pre>

![Yes](images/yes.png)
<pre><strong>proxy_set_header X-Script-Name /;</strong>
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;</pre>

> The reverse proxy will not function without the *X-Script-Name* header.

---

**Page 359** : *bogofilter-mail.sh*.

![No](images/no.png)
<pre>in=`mktemp --tmpdir="${TMPDIR}" --suffix=.in`
out=${in/%in/out}</pre>

![Yes](images/yes.png)
<pre>in=`mktemp "${TMPDIR}/tmp.XXXXXXXXXX"`
out="${in}.out"</pre>

> The syntax for the *mktemp* command differs between Linux and FreeBSD. The original command only worked on Linux; the corrected version is valid for both Linux and FreeBSD.

---

**Page 363** : *bogofilter-train.sh*.

![No](images/no.png)
<pre>cat | bogofilter ${FLAG} &</pre>

![Yes](images/yes.png)
<pre>cat | bogofilter <strong>-d "${HOME}/bogofilter"</strong> ${FLAG} &</pre>

> This path should correspond to the path used in *bogo-dirs.sh* and *bogofilter-mail.sh*.
