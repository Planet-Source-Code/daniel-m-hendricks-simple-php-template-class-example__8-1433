<div align="center">

## Simple PHP Template Class Example


</div>

### Description

The purpose of this tutorial is to show you how to implement a simple class to handle page templates.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Daniel M\. Hendricks](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/daniel-m-hendricks.md)
**Level**          |Beginner
**User Rating**    |4.4 (79 globes from 18 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__8-3.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/daniel-m-hendricks-simple-php-template-class-example__8-1433/archive/master.zip)





### Source Code


<br /><h3>Simple PHP Template Class</h3>
<p><font size="2">The purpose of this tutorial is to show you how to implement a
simple class to handle page templates.&nbsp; It can be extended in any way you
wish.</font></p>
<p><b><font size="2">The Class (template.class.php)</font></b></p>
<p><code>&lt;?<br>
class Template {<br>
&nbsp;&nbsp; public $template;<br>
&nbsp;&nbsp; function load($filepath) {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $this-&gt;template = file_get_contents($filepath);<br>
&nbsp;&nbsp; }<br>
&nbsp;&nbsp; function replace($var, $content) {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $this->template = str_replace("#$var#", $content, $this->template);<br>
&nbsp;&nbsp; }<br>
&nbsp;&nbsp; function publish() {<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		eval(&quot;?&gt;&quot;.$this-&gt;template.&quot;&lt;?&quot;);<br>
&nbsp;&nbsp; }<br>
}<br>
?&gt;</code></p>
<p><b><font size="2">The Template File (design.html)</font></b></p>
<p><font size="2">This file will contain the design of your web site and the
blank fields that will be merged with content data.</font></p>
<p><font size="2">&lt;html&gt;<br>
&lt;head&gt;<br>
&lt;title&gt;#title#&lt;/title&gt;<br>
&lt;/head&gt;<br>
&lt;body&gt;<br>
&lt;h3&gt;Hello #name#!&lt;/h3&gt;<br>
&lt;p&gt;The time is: #datetime#&lt;/p&gt;<br>
&lt;? echo &quot;&lt;p&gt;Embedded PHP works too!&lt;/p&gt;&quot;; ?&gt;<br>
&lt;/body&gt;<br>
&lt;/html&gt;</font></p>
<p><b><font size="2">Usage (index.php)</font></b></p>
<p><font size="2">Now we will create a script that load the template and use the
class to merge the data.</font></p>
<p><code>&lt;?<br>
include &quot;template.class.php&quot;;</code></p>
<p><code>$template = new Template;<br>
$template-&gt;load(&quot;design.html&quot;);<br>
$template-&gt;replace(&quot;title&quot;, &quot;My Template Class&quot;);<br>
$template-&gt;replace(&quot;name&quot;, &quot;William&quot;);<br>
$template-&gt;replace(&quot;datetime&quot;, <span class="default">date</span><span class="keyword">(</span><span class="string">&quot;m/d/y&quot;</span><span class="keyword">)</span>);<br>
$template->publish();<br>
?></code></p>
<p><font size="2">When you run the above script, index.php, it will output the
following:</font></p>
<p><font size="2">&nbsp;&lt;html&gt;<br>
&lt;head&gt;<br>
&lt;title&gt;My Template Class&lt;/title&gt;<br>
&lt;/head&gt;<br>
&lt;body&gt;<br>
&lt;h3&gt;Hello William!&lt;/h3&gt;<br>
&lt;p&gt;The time is: 03/10/04&lt;/p&gt;<br>
&lt;p&gt;Embedded PHP works too!&lt;/p&gt;<br>
&lt;/body&gt;<br>
&lt;/html&gt;</font></p>
<p><font size="2">This code, as you can see, is very simple.&nbsp; It supports
embedding PHP into the original template file (design.html).&nbsp; You could
easily extend it to pull data from a database such as MySQL.</font></p>

