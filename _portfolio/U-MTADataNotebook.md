---
title: "EDA: NYC MTA Turnstile Data"
excerpt: "A fun analysis on publicly available NYC Subway data for 2013"
header:
  teaser: /assets/images/MTA_subway.jpg
number: 1
---

## NYC MTA Turnstile Data

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="" xml:lang="">
<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes" />
  <title>31f6b40f86ae472eb4fd755e34faf706</title>
  <style>
    html {
      line-height: 1.5;
      font-family: Georgia, serif;
      font-size: 20px;
      color: #1a1a1a;
      background-color: #fdfdfd;
    }
    body {
      margin: 0 auto;
      max-width: 36em;
      padding-left: 50px;
      padding-right: 50px;
      padding-top: 50px;
      padding-bottom: 50px;
      hyphens: auto;
      word-wrap: break-word;
      text-rendering: optimizeLegibility;
      font-kerning: normal;
    }
    @media (max-width: 600px) {
      body {
        font-size: 0.9em;
        padding: 1em;
      }
    }
    @media print {
      body {
        background-color: transparent;
        color: black;
        font-size: 12pt;
      }
      p, h2, h3 {
        orphans: 3;
        widows: 3;
      }
      h2, h3, h4 {
        page-break-after: avoid;
      }
    }
    p {
      margin: 1em 0;
    }
    a {
      color: #1a1a1a;
    }
    a:visited {
      color: #1a1a1a;
    }
    img {
      max-width: 100%;
    }
    h1, h2, h3, h4, h5, h6 {
      margin-top: 1.4em;
    }
    h5, h6 {
      font-size: 1em;
      font-style: italic;
    }
    h6 {
      font-weight: normal;
    }
    ol, ul {
      padding-left: 1.7em;
      margin-top: 1em;
    }
    li > ol, li > ul {
      margin-top: 0;
    }
    blockquote {
      margin: 1em 0 1em 1.7em;
      padding-left: 1em;
      border-left: 2px solid #e6e6e6;
      color: #606060;
    }
    code {
      font-family: Menlo, Monaco, 'Lucida Console', Consolas, monospace;
      font-size: 85%;
      margin: 0;
    }
    pre {
      margin: 1em 0;
      overflow: auto;
    }
    pre code {
      padding: 0;
      overflow: visible;
    }
    .sourceCode {
     background-color: transparent;
     overflow: visible;
    }
    hr {
      background-color: #1a1a1a;
      border: none;
      height: 1px;
      margin: 1em 0;
    }
    table {
      margin: 1em 0;
      border-collapse: collapse;
      width: 100%;
      overflow-x: auto;
      display: block;
      font-variant-numeric: lining-nums tabular-nums;
    }
    table caption {
      margin-bottom: 0.75em;
    }
    tbody {
      margin-top: 0.5em;
      border-top: 1px solid #1a1a1a;
      border-bottom: 1px solid #1a1a1a;
    }
    th {
      border-top: 1px solid #1a1a1a;
      padding: 0.25em 0.5em 0.25em 0.5em;
    }
    td {
      padding: 0.125em 0.5em 0.25em 0.5em;
    }
    header {
      margin-bottom: 4em;
      text-align: center;
    }
    #TOC li {
      list-style: none;
    }
    #TOC a:not(:hover) {
      text-decoration: none;
    }
    code{white-space: pre-wrap;}
    span.smallcaps{font-variant: small-caps;}
    span.underline{text-decoration: underline;}
    div.column{display: inline-block; vertical-align: top; width: 50%;}
    div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
    ul.task-list{list-style: none;}
    pre > code.sourceCode { white-space: pre; position: relative; }
    pre > code.sourceCode > span { display: inline-block; line-height: 1.25; }
    pre > code.sourceCode > span:empty { height: 1.2em; }
    .sourceCode { overflow: visible; }
    code.sourceCode > span { color: inherit; text-decoration: inherit; }
    div.sourceCode { margin: 1em 0; }
    pre.sourceCode { margin: 0; }
    @media screen {
    div.sourceCode { overflow: auto; }
    }
    @media print {
    pre > code.sourceCode { white-space: pre-wrap; }
    pre > code.sourceCode > span { text-indent: -5em; padding-left: 5em; }
    }
    pre.numberSource code
      { counter-reset: source-line 0; }
    pre.numberSource code > span
      { position: relative; left: -4em; counter-increment: source-line; }
    pre.numberSource code > span > a:first-child::before
      { content: counter(source-line);
        position: relative; left: -1em; text-align: right; vertical-align: baseline;
        border: none; display: inline-block;
        -webkit-touch-callout: none; -webkit-user-select: none;
        -khtml-user-select: none; -moz-user-select: none;
        -ms-user-select: none; user-select: none;
        padding: 0 4px; width: 4em;
        color: #aaaaaa;
      }
    pre.numberSource { margin-left: 3em; border-left: 1px solid #aaaaaa;  padding-left: 4px; }
    div.sourceCode
      {   }
    @media screen {
    pre > code.sourceCode > span > a:first-child::before { text-decoration: underline; }
    }
    code span.al { color: #ff0000; font-weight: bold; } /* Alert */
    code span.an { color: #60a0b0; font-weight: bold; font-style: italic; } /* Annotation */
    code span.at { color: #7d9029; } /* Attribute */
    code span.bn { color: #40a070; } /* BaseN */
    code span.bu { } /* BuiltIn */
    code span.cf { color: #007020; font-weight: bold; } /* ControlFlow */
    code span.ch { color: #4070a0; } /* Char */
    code span.cn { color: #880000; } /* Constant */
    code span.co { color: #60a0b0; font-style: italic; } /* Comment */
    code span.cv { color: #60a0b0; font-weight: bold; font-style: italic; } /* CommentVar */
    code span.do { color: #ba2121; font-style: italic; } /* Documentation */
    code span.dt { color: #902000; } /* DataType */
    code span.dv { color: #40a070; } /* DecVal */
    code span.er { color: #ff0000; font-weight: bold; } /* Error */
    code span.ex { } /* Extension */
    code span.fl { color: #40a070; } /* Float */
    code span.fu { color: #06287e; } /* Function */
    code span.im { } /* Import */
    code span.in { color: #60a0b0; font-weight: bold; font-style: italic; } /* Information */
    code span.kw { color: #007020; font-weight: bold; } /* Keyword */
    code span.op { color: #666666; } /* Operator */
    code span.ot { color: #007020; } /* Other */
    code span.pp { color: #bc7a00; } /* Preprocessor */
    code span.sc { color: #4070a0; } /* SpecialChar */
    code span.ss { color: #bb6688; } /* SpecialString */
    code span.st { color: #4070a0; } /* String */
    code span.va { color: #19177c; } /* Variable */
    code span.vs { color: #4070a0; } /* VerbatimString */
    code span.wa { color: #60a0b0; font-weight: bold; font-style: italic; } /* Warning */
    .display.math{display: block; text-align: center; margin: 0.5rem auto;}
  </style>
  <!--[if lt IE 9]>
    <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv-printshiv.min.js"></script>
  <![endif]-->
</head>
<body>
<div class="cell code" data-execution_count="1">
<div class="sourceCode" id="cb1"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> pandas <span class="im">as</span> pd</span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> os</span>
<span id="cb1-3"><a href="#cb1-3" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> itertools</span>
<span id="cb1-4"><a href="#cb1-4" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> time</span>
<span id="cb1-5"><a href="#cb1-5" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> datetime</span>
<span id="cb1-6"><a href="#cb1-6" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> matplotlib.pyplot <span class="im">as</span> plt</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="2">
<div class="sourceCode" id="cb2"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb2-1"><a href="#cb2-1" aria-hidden="true" tabindex="-1"></a><span class="kw">def</span> format_old_file(filename):</span>
<span id="cb2-2"><a href="#cb2-2" aria-hidden="true" tabindex="-1"></a>    column_names <span class="op">=</span> [<span class="st">&#39;C/A&#39;</span>, <span class="st">&#39;UNIT&#39;</span>, <span class="st">&#39;SCP&#39;</span>, <span class="st">&#39;DATE&#39;</span>, <span class="st">&#39;TIME&#39;</span>,<span class="st">&#39;DESC&#39;</span>, <span class="st">&#39;ENTRIES&#39;</span>, <span class="st">&#39;EXITS&#39;</span>]</span>
<span id="cb2-3"><a href="#cb2-3" aria-hidden="true" tabindex="-1"></a>    remainders <span class="op">=</span> itertools.zip_longest(<span class="op">*</span>[<span class="bu">iter</span>(<span class="bu">range</span>(<span class="dv">3</span>, <span class="dv">43</span>))] <span class="op">*</span> <span class="dv">5</span>, fillvalue<span class="op">=</span><span class="dv">0</span>)</span>
<span id="cb2-4"><a href="#cb2-4" aria-hidden="true" tabindex="-1"></a>    column_values <span class="op">=</span> [[<span class="dv">0</span>, <span class="dv">1</span>, <span class="dv">2</span>, <span class="op">*</span>row] <span class="cf">for</span> row <span class="kw">in</span> remainders]</span>
<span id="cb2-5"><a href="#cb2-5" aria-hidden="true" tabindex="-1"></a>    frames <span class="op">=</span> [pd.read_csv(filename, header<span class="op">=</span><span class="va">None</span>, usecols<span class="op">=</span>usecols,</span>
<span id="cb2-6"><a href="#cb2-6" aria-hidden="true" tabindex="-1"></a>                              names<span class="op">=</span>column_names)</span>
<span id="cb2-7"><a href="#cb2-7" aria-hidden="true" tabindex="-1"></a>                  <span class="cf">for</span> usecols <span class="kw">in</span> column_values]</span>
<span id="cb2-8"><a href="#cb2-8" aria-hidden="true" tabindex="-1"></a>    </span>
<span id="cb2-9"><a href="#cb2-9" aria-hidden="true" tabindex="-1"></a>    df <span class="op">=</span> pd.concat(frames, axis<span class="op">=</span><span class="dv">0</span>)</span>
<span id="cb2-10"><a href="#cb2-10" aria-hidden="true" tabindex="-1"></a>    df.reset_index(drop<span class="op">=</span><span class="va">True</span>,inplace<span class="op">=</span><span class="va">True</span>)</span>
<span id="cb2-11"><a href="#cb2-11" aria-hidden="true" tabindex="-1"></a>    <span class="cf">return</span> df</span></code></pre></div>
</div>
<section id="pull-in-2013-data" class="cell markdown">
<h2>Pull in 2013 Data</h2>
<p>All txt files for the year of 2013 were downloaded from <a href="http://web.mta.info/developers/turnstile.html" class="uri">http://web.mta.info/developers/turnstile.html</a> and placed in a local directory called 'mta_data'. Data files created prior to 10/18/14 do not have one observation per row, and thus require some preprocessing and transformation (function above). Following this step, all the resulting dataframes from each weekly txt file are concatenated into one large dataframe containing all data for 2013. In all, it takes ~1 min to load in and process all the files (on my Mac at least).</p>
<p>Within the mta_data folder, a subdirectory called '2013' contains all 2013 txt files. Additionally, within the mta_data directory there are two supporting data files:</p>
<ol>
<li>Most recent MTA data file for getting answer to question 1</li>
<li>Remote-Booth-Station.xls to map stations to older data files</li>
</ol>
<p>According to the MTA website, the data contains the following fields. Data prior to 10/18/14 contain a subset of the same fields. Fields not contained in older data is marked with an asterisk.</p>
<ul>
<li>C/A = Control Area (A002)</li>
<li>UNIT = Remote Unit for a station (R051)</li>
<li>SCP = Subunit Channel Position represents an specific address for a device (02-00-00)</li>
<li>STATION* = Represents the station name the device is located at</li>
<li>LINENAME* = Represents all train lines that can be boarded at this station Normally lines are represented by one character. LINENAME 456NQR repersents train server for 4, 5, 6, N, Q, and R trains.</li>
<li>DIVISION* = Represents the Line originally the station belonged to BMT, IRT, or IND<br />
</li>
<li>DATE = Represents the date (MM-DD-YY)</li>
<li>TIME = Represents the time (hh:mm:ss) for a scheduled audit event</li>
<li>DESc = Represent the "REGULAR" scheduled audit event (Normally occurs every 4 hours) 1. Audits may occur more that 4 hours due to planning, or troubleshooting activities. 2. Additionally, there may be a "RECOVR AUD" entry: This refers to a missed audit that was recovered.</li>
<li>ENTRIES = The comulative entry register value for a device</li>
<li>EXITS = The cumulative exit register value for a device</li>
</ul>
</section>
<div class="cell code" data-execution_count="3">
<div class="sourceCode" id="cb3"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> os</span>
<span id="cb3-2"><a href="#cb3-2" aria-hidden="true" tabindex="-1"></a>data_dir <span class="op">=</span> <span class="st">&#39;../../mta_data/2013/&#39;</span></span>
<span id="cb3-3"><a href="#cb3-3" aria-hidden="true" tabindex="-1"></a>filenames <span class="op">=</span> [<span class="bu">file</span> <span class="cf">for</span> <span class="bu">file</span> <span class="kw">in</span> <span class="bu">sorted</span>(os.listdir(data_dir)) <span class="cf">if</span> <span class="st">&#39;turnstile&#39;</span> <span class="kw">in</span> <span class="bu">file</span>]</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="4">
<div class="sourceCode" id="cb4"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb4-1"><a href="#cb4-1" aria-hidden="true" tabindex="-1"></a>t <span class="op">=</span> time.time()</span>
<span id="cb4-2"><a href="#cb4-2" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> pd.concat([format_old_file(data_dir <span class="op">+</span> <span class="bu">file</span>) <span class="cf">for</span> <span class="bu">file</span> <span class="kw">in</span> filenames],axis<span class="op">=</span><span class="dv">0</span>)</span>
<span id="cb4-3"><a href="#cb4-3" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Imported data in </span><span class="sc">{</span>time<span class="sc">.</span>time() <span class="op">-</span><span class="sc">t}</span><span class="ss"> seconds&quot;</span>)</span>
<span id="cb4-4"><a href="#cb4-4" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Number of rows: </span><span class="sc">{</span><span class="bu">len</span>(df)<span class="sc">}</span><span class="ss">&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Imported data in 46.12816309928894 seconds
Number of rows: 12380824
</code></pre>
</div>
</div>
<section id="pull-in-new-data-file" class="cell markdown">
<h3>Pull in new data file</h3>
<p>We also need to pull the latest data file which contains the stations that each unit is in, which is not included in 2013 data files. This data will be merged in to get the station to turnstile mapping.</p>
</section>
<section id="cleaning-and-quality-check" class="cell markdown">
<h2>Cleaning and Quality Check</h2>
</section>
<section id="null-rows" class="cell markdown">
<h4>Null Rows</h4>
</section>
<div class="cell code" data-execution_count="5">
<div class="sourceCode" id="cb6"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb6-1"><a href="#cb6-1" aria-hidden="true" tabindex="-1"></a>na_rows <span class="op">=</span> df.isna().<span class="bu">any</span>(axis<span class="op">=</span><span class="dv">1</span>).<span class="bu">sum</span>()</span>
<span id="cb6-2"><a href="#cb6-2" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;There are </span><span class="sc">{</span>na_rows<span class="sc">}</span><span class="ss"> with na values (</span><span class="sc">{</span><span class="bu">round</span>(na_rows<span class="op">/</span><span class="bu">len</span>(df) <span class="op">*</span> <span class="dv">100</span>,<span class="dv">2</span>)<span class="sc">}</span><span class="ss"> %)&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>There are 916414 with na values (7.4 %)
</code></pre>
</div>
</div>
<div class="cell markdown">
<p>Most of the na values are likely an artifact of the initial parsing logic required for the older file format. Moreover, there is no effective or reasonable assumption that can made to fill in the missing values and, in fact, doing so incorrectly could make matters worse. With over 90% (10 million+) of the records intact, we will just drop the rows containing na values.</p>
</div>
<div class="cell code" data-execution_count="6">
<div class="sourceCode" id="cb8"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb8-1"><a href="#cb8-1" aria-hidden="true" tabindex="-1"></a>df.dropna(inplace<span class="op">=</span><span class="va">True</span>)</span></code></pre></div>
</div>
<section id="negative-entriesexits" class="cell markdown">
<h4>Negative Entries/Exits</h4>
</section>
<div class="cell code" data-execution_count="7">
<div class="sourceCode" id="cb9"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb9-1"><a href="#cb9-1" aria-hidden="true" tabindex="-1"></a>df.describe()</span></code></pre></div>
<div class="output execute_result" data-execution_count="7">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ENTRIES</th>
      <th>EXITS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1.146441e+07</td>
      <td>1.146441e+07</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.034486e+06</td>
      <td>2.971423e+06</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.292653e+07</td>
      <td>3.299601e+07</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-9.314769e+08</td>
      <td>-8.789686e+08</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.364450e+05</td>
      <td>1.932042e+05</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.982436e+06</td>
      <td>1.216322e+06</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4.972726e+06</td>
      <td>3.579545e+06</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9.168487e+08</td>
      <td>9.797130e+08</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell markdown">
<p>A quick description of the data shows that there appear to be negative values for the Entries and Exits. This doesn't make any sense given that the columns are meant to be cumulative. However, while the exact reason these values are negative is unclear (may have something to do with DOOR OPEN/DOOR CLOSE events), from a quick check of some of the records the data still seems to be accurately counting the number of exits/entries in between each reading even if the value is abnormal. Thus, we can still calculate the change and then evaluate if we still get negative values there (which we'll have to fix).</p>
</div>
<section id="dates" class="cell markdown">
<h4>Dates</h4>
<p>Combining the date and time columns into a separate datetime column will simplify analysis and reduce the number of columns. Additionally, as all analysis is being confined to 2013, we will ensure only dates in that year are represented.</p>
</section>
<div class="cell code" data-execution_count="8">
<div class="sourceCode" id="cb10"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb10-1"><a href="#cb10-1" aria-hidden="true" tabindex="-1"></a>df[<span class="st">&#39;DateTime&#39;</span>] <span class="op">=</span> pd.to_datetime(df[<span class="st">&#39;DATE&#39;</span>] <span class="op">+</span> <span class="st">&#39; &#39;</span> <span class="op">+</span> df[<span class="st">&#39;TIME&#39;</span>])</span>
<span id="cb10-2"><a href="#cb10-2" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df.drop(columns<span class="op">=</span>[<span class="st">&#39;DATE&#39;</span>,<span class="st">&#39;TIME&#39;</span>])</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="9">
<div class="sourceCode" id="cb11"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb11-1"><a href="#cb11-1" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df[(df.DateTime <span class="op">&gt;</span> <span class="st">&#39;2013-01-01 00:00:00&#39;</span>) <span class="op">&amp;</span> (df.DateTime <span class="op">&lt;</span> <span class="st">&#39;2013-12-31 23:59:59&#39;</span>)]</span></code></pre></div>
</div>
<section id="turnstile-and-entriesexits-change-columns" class="cell markdown">
<h4>TurnStile and Entries/Exits change columns</h4>
<p>We'll create a turnstile column that is the combination of the C/A, UNIT, and SCP since that uniquely identifies a turnstile within a station and will simplify the groupby statements. Additionally, we'll calculate the change in entries and exit at each reading for a turnstile, which will be needed for later analysis.</p>
</section>
<div class="cell code" data-execution_count="10">
<div class="sourceCode" id="cb12"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb12-1"><a href="#cb12-1" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df.reset_index(drop<span class="op">=</span><span class="va">True</span>)</span>
<span id="cb12-2"><a href="#cb12-2" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df.assign(TurnStile<span class="op">=</span>df[<span class="st">&#39;C/A&#39;</span>] <span class="op">+</span> <span class="st">&#39;-&#39;</span> <span class="op">+</span> df[<span class="st">&#39;UNIT&#39;</span>] <span class="op">+</span> <span class="st">&#39;-&#39;</span> <span class="op">+</span> df[<span class="st">&#39;SCP&#39;</span>])</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="11">
<div class="sourceCode" id="cb13"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb13-1"><a href="#cb13-1" aria-hidden="true" tabindex="-1"></a>df_sort <span class="op">=</span> df.sort_values([<span class="st">&#39;TurnStile&#39;</span>,<span class="st">&#39;DateTime&#39;</span>])</span>
<span id="cb13-2"><a href="#cb13-2" aria-hidden="true" tabindex="-1"></a>df[<span class="st">&#39;EntriesChange&#39;</span>] <span class="op">=</span> df_sort.groupby(<span class="st">&#39;TurnStile&#39;</span>)[<span class="st">&#39;ENTRIES&#39;</span>].transform(pd.Series.diff)</span>
<span id="cb13-3"><a href="#cb13-3" aria-hidden="true" tabindex="-1"></a>df[<span class="st">&#39;ExitsChange&#39;</span>] <span class="op">=</span> df_sort.groupby(<span class="st">&#39;TurnStile&#39;</span>)[<span class="st">&#39;EXITS&#39;</span>].transform(pd.Series.diff)</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="12">
<div class="sourceCode" id="cb14"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb14-1"><a href="#cb14-1" aria-hidden="true" tabindex="-1"></a><span class="co"># fill na values which mark the first measurement of the turnstile</span></span>
<span id="cb14-2"><a href="#cb14-2" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df.fillna({<span class="st">&#39;EntriesChange&#39;</span>:<span class="dv">0</span>, <span class="st">&#39;ExitsChange&#39;</span>:<span class="dv">0</span>})</span></code></pre></div>
</div>
<section id="quality-check-on-change-columns" class="cell markdown">
<h4>Quality Check on Change columns</h4>
<p>Doing a describe shows that there are some change values which are negative. This is doesnt make sense and we will have to amend the data.</p>
</section>
<div class="cell code" data-execution_count="13">
<div class="sourceCode" id="cb15"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb15-1"><a href="#cb15-1" aria-hidden="true" tabindex="-1"></a>df.describe()</span></code></pre></div>
<div class="output execute_result" data-execution_count="13">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ENTRIES</th>
      <th>EXITS</th>
      <th>EntriesChange</th>
      <th>ExitsChange</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1.137625e+07</td>
      <td>1.137625e+07</td>
      <td>1.137625e+07</td>
      <td>1.137625e+07</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.043418e+06</td>
      <td>2.975773e+06</td>
      <td>8.206008e+02</td>
      <td>6.460294e+02</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.300180e+07</td>
      <td>3.307180e+07</td>
      <td>9.819976e+05</td>
      <td>1.025034e+06</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-9.314769e+08</td>
      <td>-8.789650e+08</td>
      <td>-9.314769e+08</td>
      <td>-9.797130e+08</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.366480e+05</td>
      <td>1.932310e+05</td>
      <td>1.000000e+00</td>
      <td>1.000000e+00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.982904e+06</td>
      <td>1.216513e+06</td>
      <td>5.200000e+01</td>
      <td>3.700000e+01</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4.973487e+06</td>
      <td>3.579991e+06</td>
      <td>2.100000e+02</td>
      <td>1.450000e+02</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9.168487e+08</td>
      <td>9.797130e+08</td>
      <td>9.168486e+08</td>
      <td>9.719247e+08</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell code" data-execution_count="14">
<div class="sourceCode" id="cb16"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb16-1"><a href="#cb16-1" aria-hidden="true" tabindex="-1"></a>tot_rows_neg <span class="op">=</span> <span class="bu">len</span>(df.loc[(df[<span class="st">&#39;EntriesChange&#39;</span>] <span class="op">&lt;</span> <span class="dv">0</span>) <span class="op">|</span> (df[<span class="st">&#39;ExitsChange&#39;</span>] <span class="op">&lt;</span> <span class="dv">0</span>)])</span>
<span id="cb16-2"><a href="#cb16-2" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Total rows with negative change values: </span><span class="sc">{</span>tot_rows_neg<span class="sc">}</span><span class="ss">&quot;</span>)</span>
<span id="cb16-3"><a href="#cb16-3" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Percentage of negative change values rows out of total: </span><span class="sc">{</span><span class="bu">round</span>(tot_rows_neg<span class="op">/</span><span class="bu">len</span>(df)<span class="op">*</span><span class="dv">100</span>,<span class="dv">2</span>)<span class="sc">}</span><span class="ss">%&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Total rows with negative change values: 2304
Percentage of negative change values rows out of total: 0.02%
</code></pre>
</div>
</div>
<div class="cell markdown">
<p>These rows with negative values account for a whopping 0.02% of all the data. For such a small sample its not really worth it to do a deep dive and write a possibly complicated algorithm to figure out a reasonable value. We'll just drop them.</p>
<p>However, with the negative values means we have the inverse happening where there are abnormally large numbers. For an example, see the slice below. These are not as easy to identify. We could use IQR or z-score to try to clearly identify them and delete, but we also risk losing data for stations that see actual jumps because of holidays or special events. We want to capture these as best we can so we'll just set an upper limit of 10,000. If a row has more than 10,000 exits or entries in a 4 hour or less period, we'll consider that too high. For 4 hours that's a rate of ~41 people per minute for one turnstile.</p>
</div>
<div class="cell code" data-execution_count="15">
<div class="sourceCode" id="cb18"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb18-1"><a href="#cb18-1" aria-hidden="true" tabindex="-1"></a>df.loc[(df.TurnStile <span class="op">==</span> <span class="st">&#39;R644-R135-01-00-00&#39;</span>) <span class="op">&amp;</span> (df.DateTime.dt.date.astype(<span class="bu">str</span>) <span class="op">==</span> <span class="st">&#39;2013-11-26&#39;</span>)].head()</span></code></pre></div>
<div class="output execute_result" data-execution_count="15">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>C/A</th>
      <th>UNIT</th>
      <th>SCP</th>
      <th>DESC</th>
      <th>ENTRIES</th>
      <th>EXITS</th>
      <th>DateTime</th>
      <th>TurnStile</th>
      <th>EntriesChange</th>
      <th>ExitsChange</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>10334734</th>
      <td>R644</td>
      <td>R135</td>
      <td>01-00-00</td>
      <td>REGULAR</td>
      <td>4039.0</td>
      <td>1310543.0</td>
      <td>2013-11-26 08:00:00</td>
      <td>R644-R135-01-00-00</td>
      <td>0.0</td>
      <td>65.0</td>
    </tr>
    <tr>
      <th>10334735</th>
      <td>R644</td>
      <td>R135</td>
      <td>01-00-00</td>
      <td>LGF-MAN</td>
      <td>334108.0</td>
      <td>1440925.0</td>
      <td>2013-11-26 12:25:04</td>
      <td>R644-R135-01-00-00</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>10363112</th>
      <td>R644</td>
      <td>R135</td>
      <td>01-00-00</td>
      <td>RECOVR AUD</td>
      <td>334063.0</td>
      <td>1440813.0</td>
      <td>2013-11-26 08:00:00</td>
      <td>R644-R135-01-00-00</td>
      <td>330024.0</td>
      <td>130270.0</td>
    </tr>
    <tr>
      <th>10363113</th>
      <td>R644</td>
      <td>R135</td>
      <td>01-00-00</td>
      <td>LOGON</td>
      <td>334108.0</td>
      <td>1440925.0</td>
      <td>2013-11-26 12:25:15</td>
      <td>R644-R135-01-00-00</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>10389840</th>
      <td>R644</td>
      <td>R135</td>
      <td>01-00-00</td>
      <td>REGULAR</td>
      <td>4040.0</td>
      <td>1310668.0</td>
      <td>2013-11-26 12:00:00</td>
      <td>R644-R135-01-00-00</td>
      <td>-330023.0</td>
      <td>-130145.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell code" data-execution_count="16">
<div class="sourceCode" id="cb19"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb19-1"><a href="#cb19-1" aria-hidden="true" tabindex="-1"></a><span class="co"># drop negative values</span></span>
<span id="cb19-2"><a href="#cb19-2" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df[<span class="op">~</span>((df[<span class="st">&#39;EntriesChange&#39;</span>] <span class="op">&lt;</span> <span class="dv">0</span>) <span class="op">|</span> (df[<span class="st">&#39;ExitsChange&#39;</span>] <span class="op">&lt;</span> <span class="dv">0</span>))]</span>
<span id="cb19-3"><a href="#cb19-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb19-4"><a href="#cb19-4" aria-hidden="true" tabindex="-1"></a><span class="co"># drop records with values greater than 10,000</span></span>
<span id="cb19-5"><a href="#cb19-5" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df[<span class="op">~</span>((df[<span class="st">&#39;EntriesChange&#39;</span>] <span class="op">&gt;</span> <span class="dv">10000</span>) <span class="op">|</span> (df[<span class="st">&#39;ExitsChange&#39;</span>] <span class="op">&gt;</span> <span class="dv">10000</span>))]</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="17">
<div class="sourceCode" id="cb20"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb20-1"><a href="#cb20-1" aria-hidden="true" tabindex="-1"></a>df.describe()</span></code></pre></div>
<div class="output execute_result" data-execution_count="17">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ENTRIES</th>
      <th>EXITS</th>
      <th>EntriesChange</th>
      <th>ExitsChange</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1.137349e+07</td>
      <td>1.137349e+07</td>
      <td>1.137349e+07</td>
      <td>1.137349e+07</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.042996e+06</td>
      <td>2.975560e+06</td>
      <td>1.572528e+02</td>
      <td>1.234072e+02</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.299406e+07</td>
      <td>3.306292e+07</td>
      <td>2.516331e+02</td>
      <td>2.265497e+02</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-9.314769e+08</td>
      <td>-8.789650e+08</td>
      <td>0.000000e+00</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.369660e+05</td>
      <td>1.934675e+05</td>
      <td>1.000000e+00</td>
      <td>1.000000e+00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.983519e+06</td>
      <td>1.216895e+06</td>
      <td>5.200000e+01</td>
      <td>3.700000e+01</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>4.973984e+06</td>
      <td>3.580515e+06</td>
      <td>2.100000e+02</td>
      <td>1.450000e+02</td>
    </tr>
    <tr>
      <th>max</th>
      <td>9.168487e+08</td>
      <td>9.797130e+08</td>
      <td>9.890000e+03</td>
      <td>9.571000e+03</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell markdown">
<p>Much better. Now we're ready</p>
</div>
<section id="question-1-which-station-has-the-most-number-of-units" class="cell markdown">
<h2>Question 1: Which station has the most number of units?</h2>
<p>We can use the most recent data file to get the current number of units per stations. Also, 2013 data does not contain the station column.</p>
</section>
<div class="cell code" data-execution_count="18">
<div class="sourceCode" id="cb21"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb21-1"><a href="#cb21-1" aria-hidden="true" tabindex="-1"></a>new_df <span class="op">=</span> pd.read_csv(<span class="st">&#39;../../mta_data/turnstile_210612.txt&#39;</span>, engine<span class="op">=</span><span class="st">&#39;python&#39;</span>)</span>
<span id="cb21-2"><a href="#cb21-2" aria-hidden="true" tabindex="-1"></a>new_df[<span class="st">&#39;TurnStile&#39;</span>] <span class="op">=</span> new_df[<span class="st">&#39;C/A&#39;</span>] <span class="op">+</span> <span class="st">&#39;-&#39;</span> <span class="op">+</span> new_df[<span class="st">&#39;UNIT&#39;</span>] <span class="op">+</span> <span class="st">&#39;-&#39;</span> <span class="op">+</span> new_df[<span class="st">&#39;SCP&#39;</span>]</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="19">
<div class="sourceCode" id="cb22"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb22-1"><a href="#cb22-1" aria-hidden="true" tabindex="-1"></a>fig, ax <span class="op">=</span> plt.subplots(figsize<span class="op">=</span>(<span class="dv">25</span>, <span class="dv">8</span>))</span>
<span id="cb22-2"><a href="#cb22-2" aria-hidden="true" tabindex="-1"></a>largest_stations <span class="op">=</span> new_df.drop_duplicates(<span class="st">&#39;TurnStile&#39;</span>).groupby([<span class="st">&#39;STATION&#39;</span>]).size().sort_values(ascending<span class="op">=</span><span class="va">False</span>).head(<span class="dv">10</span>)</span>
<span id="cb22-3"><a href="#cb22-3" aria-hidden="true" tabindex="-1"></a>largest_stations.plot(kind<span class="op">=</span><span class="st">&#39;bar&#39;</span>,ax<span class="op">=</span>ax)</span>
<span id="cb22-4"><a href="#cb22-4" aria-hidden="true" tabindex="-1"></a>ax.<span class="bu">set</span>(title<span class="op">=</span><span class="st">&#39;Top 10 Largest Stations by Turnstile Count&#39;</span>, xlabel<span class="op">=</span><span class="st">&#39;Station&#39;</span>, ylabel<span class="op">=</span><span class="st">&#39;Number of TurnStiles&#39;</span>)</span>
<span id="cb22-5"><a href="#cb22-5" aria-hidden="true" tabindex="-1"></a>ax.legend().set_visible(<span class="va">False</span>)</span></code></pre></div>
<div class="output display_data">
<p><img src="vertopal_f3465f12660048fb84ae161b90152882/5f7158e297c862bd96a9be9ff7b786528720d905.png" /></p>
</div>
</div>
<section id="answer" class="cell markdown">
<h4>ANSWER</h4>
</section>
<div class="cell code" data-execution_count="20">
<div class="sourceCode" id="cb23"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb23-1"><a href="#cb23-1" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Answer: </span><span class="sc">{pd.</span>Series(largest_stations)[:<span class="dv">1</span>]<span class="sc">}</span><span class="ss">&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Answer: STATION
34 ST-PENN STA    102
dtype: int64
</code></pre>
</div>
</div>
<section id="34-st-penn-station-has-the-most-turnstiles-with-102" class="cell markdown">
<h5>34 ST-PENN STATION has the most turnstiles with 102</h5>
</section>
<div class="cell markdown">
<hr />
</div>
<section id="question-2-what-is-the-total-number-of-entries--exits-across-the-subway-system-for-february-1-2013" class="cell markdown">
<h2>Question 2: What is the total number of entries &amp; exits across the subway system for February 1, 2013?</h2>
</section>
<div class="cell code" data-execution_count="21">
<div class="sourceCode" id="cb25"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb25-1"><a href="#cb25-1" aria-hidden="true" tabindex="-1"></a>feb113_df <span class="op">=</span> df.loc[df.DateTime.dt.date.astype(<span class="bu">str</span>) <span class="op">==</span> <span class="st">&#39;2013-02-01&#39;</span>]</span>
<span id="cb25-2"><a href="#cb25-2" aria-hidden="true" tabindex="-1"></a>feb113_df.head()</span></code></pre></div>
<div class="output execute_result" data-execution_count="21">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>C/A</th>
      <th>UNIT</th>
      <th>SCP</th>
      <th>DESC</th>
      <th>ENTRIES</th>
      <th>EXITS</th>
      <th>DateTime</th>
      <th>TurnStile</th>
      <th>EntriesChange</th>
      <th>ExitsChange</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>753397</th>
      <td>A002</td>
      <td>R051</td>
      <td>02-00-00</td>
      <td>REGULAR</td>
      <td>3974913.0</td>
      <td>1370326.0</td>
      <td>2013-02-01 15:00:00</td>
      <td>A002-R051-02-00-00</td>
      <td>207.0</td>
      <td>32.0</td>
    </tr>
    <tr>
      <th>753403</th>
      <td>A002</td>
      <td>R051</td>
      <td>02-00-01</td>
      <td>REGULAR</td>
      <td>3792617.0</td>
      <td>821317.0</td>
      <td>2013-02-01 15:00:00</td>
      <td>A002-R051-02-00-01</td>
      <td>166.0</td>
      <td>25.0</td>
    </tr>
    <tr>
      <th>753418</th>
      <td>A002</td>
      <td>R051</td>
      <td>02-03-01</td>
      <td>REGULAR</td>
      <td>3612280.0</td>
      <td>5634445.0</td>
      <td>2013-02-01 19:00:00</td>
      <td>A002-R051-02-03-01</td>
      <td>621.0</td>
      <td>377.0</td>
    </tr>
    <tr>
      <th>753454</th>
      <td>A002</td>
      <td>R051</td>
      <td>02-03-06</td>
      <td>REGULAR</td>
      <td>4959945.0</td>
      <td>439721.0</td>
      <td>2013-02-01 07:00:00</td>
      <td>A002-R051-02-03-06</td>
      <td>46.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>753460</th>
      <td>A002</td>
      <td>R051</td>
      <td>02-05-00</td>
      <td>REGULAR</td>
      <td>907.0</td>
      <td>0.0</td>
      <td>2013-02-01 15:00:00</td>
      <td>A002-R051-02-05-00</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<section id="answer" class="cell markdown">
<h4>ANSWER</h4>
</section>
<div class="cell code" data-execution_count="22">
<div class="sourceCode" id="cb26"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb26-1"><a href="#cb26-1" aria-hidden="true" tabindex="-1"></a>tot_entries <span class="op">=</span> feb113_df.EntriesChange.<span class="bu">sum</span>()</span>
<span id="cb26-2"><a href="#cb26-2" aria-hidden="true" tabindex="-1"></a>tot_exits <span class="op">=</span> feb113_df.ExitsChange.<span class="bu">sum</span>()</span>
<span id="cb26-3"><a href="#cb26-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb26-4"><a href="#cb26-4" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Total number of entries across the whole subway system on February 1, 2013: </span><span class="sc">{</span>tot_entries<span class="sc">}</span><span class="ss">&quot;</span>)</span>
<span id="cb26-5"><a href="#cb26-5" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Total number of exits across the whole subway system on February 1, 2013: </span><span class="sc">{</span>tot_exits<span class="sc">}</span><span class="ss">&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Total number of entries across the whole subway system on February 1, 2013: 5818588.0
Total number of exits across the whole subway system on February 1, 2013: 4516096.0
</code></pre>
</div>
</div>
<div class="cell markdown">
<p>On February 1st 2013, 5.81 million people entered the subway and only 4.51 million came out. Terrifying. Although that makes sense because a lot of people will actually use the emergency exits on their way out, which wouldn't get counted. That's about 20%. Interesting</p>
</div>
<div class="cell markdown">
<hr />
</div>
<section id="question-3-what-station-was-the-busiest-on-february-1-2013-what-turnstile-was-the-busiest-on-that-date" class="cell markdown">
<h2>Question 3: What station was the busiest on February 1, 2013? What turnstile was the busiest on that date?</h2>
</section>
<div class="cell markdown">
<p>To answer this we first have to map the stations to their turnstiles since Feb 2013 data does not contain the station field. MTA provides a Remote-Booth-Station.xls file to help with this. I downloaded it into my home directory and read it in to merge with the Feb 2013 data.</p>
<p>Note: Some booths and/or units do not have records in the excel file. Possibly they were removed in the years gone by.</p>
</div>
<div class="cell code" data-execution_count="24">
<div class="sourceCode" id="cb28"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb28-1"><a href="#cb28-1" aria-hidden="true" tabindex="-1"></a>stat_map <span class="op">=</span> pd.read_excel(<span class="st">&#39;../../mta_data/Remote-Booth-Station.xls&#39;</span>)</span>
<span id="cb28-2"><a href="#cb28-2" aria-hidden="true" tabindex="-1"></a>feb113_df <span class="op">=</span> feb113_df.merge(stat_map, left_on<span class="op">=</span>[<span class="st">&quot;C/A&quot;</span>,<span class="st">&quot;UNIT&quot;</span>],right_on<span class="op">=</span>[<span class="st">&quot;Booth&quot;</span>,<span class="st">&quot;Remote&quot;</span>],how<span class="op">=</span><span class="st">&#39;left&#39;</span>)</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="28">
<div class="sourceCode" id="cb29"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb29-1"><a href="#cb29-1" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;</span><span class="sc">{</span>feb113_df<span class="sc">.</span>isna()<span class="sc">.</span><span class="bu">any</span>(axis<span class="op">=</span><span class="dv">1</span>)<span class="sc">.</span><span class="bu">sum</span>()<span class="sc">}</span><span class="ss"> turnstile do not have mapped stations available (</span><span class="sc">{</span>feb113_df<span class="sc">.</span>isna()<span class="sc">.</span><span class="bu">any</span>(axis<span class="op">=</span><span class="dv">1</span>)<span class="sc">.</span><span class="bu">sum</span>()<span class="op">/</span><span class="bu">len</span>(feb113_df)<span class="op">*</span><span class="dv">100</span><span class="sc">}</span><span class="ss">%)&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>558 turnstile do not have mapped stations available (1.8250204415372036%)
</code></pre>
</div>
</div>
<section id="answer" class="cell markdown">
<h4>ANSWER</h4>
</section>
<div class="cell code" data-execution_count="29">
<div class="sourceCode" id="cb31"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb31-1"><a href="#cb31-1" aria-hidden="true" tabindex="-1"></a>busiest_stations <span class="op">=</span> pd.DataFrame((feb113_df.groupby(<span class="st">&#39;Station&#39;</span>)[<span class="st">&#39;EntriesChange&#39;</span>].<span class="bu">sum</span>() <span class="op">+</span> </span>
<span id="cb31-2"><a href="#cb31-2" aria-hidden="true" tabindex="-1"></a>              feb113_df.groupby(<span class="st">&#39;Station&#39;</span>)[<span class="st">&#39;ExitsChange&#39;</span>].<span class="bu">sum</span>()</span>
<span id="cb31-3"><a href="#cb31-3" aria-hidden="true" tabindex="-1"></a>             ), columns<span class="op">=</span>[<span class="st">&#39;Entries+Exits&#39;</span>]</span>
<span id="cb31-4"><a href="#cb31-4" aria-hidden="true" tabindex="-1"></a>            ).sort_values(by<span class="op">=</span><span class="st">&quot;Entries+Exits&quot;</span>,ascending<span class="op">=</span><span class="va">False</span>).head()</span>
<span id="cb31-5"><a href="#cb31-5" aria-hidden="true" tabindex="-1"></a>busiest_stations</span></code></pre></div>
<div class="output execute_result" data-execution_count="29">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Entries+Exits</th>
    </tr>
    <tr>
      <th>Station</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>34 ST-PENN STA</th>
      <td>348286.0</td>
    </tr>
    <tr>
      <th>42 ST-GRD CNTRL</th>
      <td>327422.0</td>
    </tr>
    <tr>
      <th>34 ST-HERALD SQ</th>
      <td>222322.0</td>
    </tr>
    <tr>
      <th>86 ST</th>
      <td>208671.0</td>
    </tr>
    <tr>
      <th>14 ST-UNION SQ</th>
      <td>208269.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell code" data-execution_count="30">
<div class="sourceCode" id="cb32"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb32-1"><a href="#cb32-1" aria-hidden="true" tabindex="-1"></a>busiest_turnstiles <span class="op">=</span> pd.DataFrame(</span>
<span id="cb32-2"><a href="#cb32-2" aria-hidden="true" tabindex="-1"></a>    (feb113_df.groupby(<span class="st">&#39;TurnStile&#39;</span>)[<span class="st">&#39;EntriesChange&#39;</span>].<span class="bu">sum</span>() <span class="op">+</span> </span>
<span id="cb32-3"><a href="#cb32-3" aria-hidden="true" tabindex="-1"></a>     feb113_df.groupby(<span class="st">&#39;TurnStile&#39;</span>)[<span class="st">&#39;ExitsChange&#39;</span>].<span class="bu">sum</span>()</span>
<span id="cb32-4"><a href="#cb32-4" aria-hidden="true" tabindex="-1"></a>    ), columns<span class="op">=</span>[<span class="st">&#39;Entries+Exits&#39;</span>]).sort_values(by<span class="op">=</span><span class="st">&quot;Entries+Exits&quot;</span>,ascending<span class="op">=</span><span class="va">False</span>).head()</span>
<span id="cb32-5"><a href="#cb32-5" aria-hidden="true" tabindex="-1"></a>busiest_turnstiles</span></code></pre></div>
<div class="output execute_result" data-execution_count="30">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Entries+Exits</th>
    </tr>
    <tr>
      <th>TurnStile</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>R240-R047-00-00-00</th>
      <td>13529.0</td>
    </tr>
    <tr>
      <th>N601-R319-00-00-00</th>
      <td>13066.0</td>
    </tr>
    <tr>
      <th>N063A-R011-00-00-00</th>
      <td>12188.0</td>
    </tr>
    <tr>
      <th>R221-R170-01-00-00</th>
      <td>12060.0</td>
    </tr>
    <tr>
      <th>R249-R179-01-00-09</th>
      <td>11692.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell code" data-execution_count="31">
<div class="sourceCode" id="cb33"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb33-1"><a href="#cb33-1" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Busiest Station: </span><span class="sc">{</span>busiest_stations<span class="sc">.</span>iloc[<span class="dv">0</span>]<span class="sc">.</span>name<span class="sc">}</span><span class="ss">&quot;</span>) </span>
<span id="cb33-2"><a href="#cb33-2" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Total Entries + Exits on Feb 1st 2013: </span><span class="sc">{</span><span class="bu">int</span>(busiest_stations.iloc[<span class="dv">0</span>][<span class="st">&#39;Entries+Exits&#39;</span>])<span class="sc">}</span><span class="ss">&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Busiest Station: 34 ST-PENN STA
Total Entries + Exits on Feb 1st 2013: 348286
</code></pre>
</div>
</div>
<div class="cell code" data-execution_count="33">
<div class="sourceCode" id="cb35"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb35-1"><a href="#cb35-1" aria-hidden="true" tabindex="-1"></a><span class="co"># station that the busiest turnstile is located in</span></span>
<span id="cb35-2"><a href="#cb35-2" aria-hidden="true" tabindex="-1"></a>tstile_station <span class="op">=</span> feb113_df.loc[feb113_df.TurnStile <span class="op">==</span> busiest_turnstiles.iloc[<span class="dv">0</span>].name][<span class="st">&#39;Station&#39;</span>].iloc[<span class="dv">0</span>]</span>
<span id="cb35-3"><a href="#cb35-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb35-4"><a href="#cb35-4" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Busiest Turnstile: </span><span class="sc">{</span>busiest_turnstiles<span class="sc">.</span>iloc[<span class="dv">0</span>]<span class="sc">.</span>name<span class="sc">}</span><span class="ss">&quot;</span>)</span>
<span id="cb35-5"><a href="#cb35-5" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Located in Station: </span><span class="sc">{</span>tstile_station<span class="sc">}</span><span class="ss">&quot;</span>)</span>
<span id="cb35-6"><a href="#cb35-6" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot;Total Entries + Exits on Feb 1st 2013: </span><span class="sc">{</span><span class="bu">int</span>(busiest_turnstiles.iloc[<span class="dv">0</span>][<span class="st">&#39;Entries+Exits&#39;</span>])<span class="sc">}</span><span class="ss">&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Busiest Turnstile: R240-R047-00-00-00
Located in Station: 42 ST-GRD CNTRL
Total Entries + Exits on Feb 1st 2013: 13529
</code></pre>
</div>
</div>
<div class="cell markdown">
<hr />
</div>
<section id="question-4-what-stations-have-seen-the-most-usage-growthdecline-in-2013" class="cell markdown">
<h2>Question 4: What stations have seen the most usage growth/decline in 2013?</h2>
</section>
<div class="cell markdown">
<p>To avoid the risk of periodicity or anomalies on certain dates by check the percent change from the first to last date, we can take the average quarterly business for each station and then compare the Q1 to Q4 traffic to see how its changed.</p>
</div>
<div class="cell code" data-execution_count="34">
<div class="sourceCode" id="cb37"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb37-1"><a href="#cb37-1" aria-hidden="true" tabindex="-1"></a><span class="co"># merge in station mapping to get the station for each turnstile</span></span>
<span id="cb37-2"><a href="#cb37-2" aria-hidden="true" tabindex="-1"></a>df <span class="op">=</span> df.merge(stat_map, left_on<span class="op">=</span>[<span class="st">&quot;C/A&quot;</span>,<span class="st">&quot;UNIT&quot;</span>],right_on<span class="op">=</span>[<span class="st">&quot;Booth&quot;</span>,<span class="st">&quot;Remote&quot;</span>],how<span class="op">=</span><span class="st">&#39;left&#39;</span>)</span>
<span id="cb37-3"><a href="#cb37-3" aria-hidden="true" tabindex="-1"></a>df[<span class="st">&#39;Entries+Exits&#39;</span>] <span class="op">=</span> df[<span class="st">&#39;EntriesChange&#39;</span>] <span class="op">+</span> df[<span class="st">&#39;ExitsChange&#39;</span>]</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="35">
<div class="sourceCode" id="cb38"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb38-1"><a href="#cb38-1" aria-hidden="true" tabindex="-1"></a><span class="co"># calculate Q1 and Q4 mean traffic for each station</span></span>
<span id="cb38-2"><a href="#cb38-2" aria-hidden="true" tabindex="-1"></a>q1 <span class="op">=</span> df.loc[df[<span class="st">&#39;DateTime&#39;</span>].dt.month.isin([<span class="dv">1</span>,<span class="dv">2</span>,<span class="dv">3</span>])].groupby([<span class="st">&#39;Station&#39;</span>])[<span class="st">&#39;Entries+Exits&#39;</span>].mean().to_frame(<span class="st">&#39;Q1Mean&#39;</span>)</span>
<span id="cb38-3"><a href="#cb38-3" aria-hidden="true" tabindex="-1"></a>q4 <span class="op">=</span> df.loc[df[<span class="st">&#39;DateTime&#39;</span>].dt.month.isin([<span class="dv">10</span>,<span class="dv">11</span>,<span class="dv">12</span>])].groupby([<span class="st">&#39;Station&#39;</span>])[<span class="st">&#39;Entries+Exits&#39;</span>].mean().to_frame(<span class="st">&#39;Q4Mean&#39;</span>)</span>
<span id="cb38-4"><a href="#cb38-4" aria-hidden="true" tabindex="-1"></a>q_df <span class="op">=</span> q1.join(q4)</span>
<span id="cb38-5"><a href="#cb38-5" aria-hidden="true" tabindex="-1"></a>q_df[<span class="st">&#39;PercentChange&#39;</span>] <span class="op">=</span> <span class="bu">round</span>(((q_df[<span class="st">&#39;Q4Mean&#39;</span>] <span class="op">-</span> q_df[<span class="st">&#39;Q1Mean&#39;</span>])<span class="op">/</span>q_df[<span class="st">&#39;Q1Mean&#39;</span>])<span class="op">*</span><span class="dv">100</span>,<span class="dv">3</span>)</span></code></pre></div>
</div>
<section id="stations-with-largest-growth-in-2013" class="cell markdown">
<h4>Stations with largest growth in 2013</h4>
</section>
<div class="cell code" data-execution_count="36">
<div class="sourceCode" id="cb39"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb39-1"><a href="#cb39-1" aria-hidden="true" tabindex="-1"></a>q_df.sort_values(<span class="st">&#39;PercentChange&#39;</span>, ascending<span class="op">=</span><span class="va">False</span>).head(<span class="dv">3</span>)</span></code></pre></div>
<div class="output execute_result" data-execution_count="36">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Q1Mean</th>
      <th>Q4Mean</th>
      <th>PercentChange</th>
    </tr>
    <tr>
      <th>Station</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>BEACH 90 ST</th>
      <td>0.050420</td>
      <td>43.670715</td>
      <td>86513.585</td>
    </tr>
    <tr>
      <th>AQUEDUCT TRACK</th>
      <td>0.370667</td>
      <td>42.954366</td>
      <td>11488.408</td>
    </tr>
    <tr>
      <th>BEACH 44 ST</th>
      <td>1.610232</td>
      <td>29.146561</td>
      <td>1710.084</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell code" data-execution_count="37">
<div class="sourceCode" id="cb40"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb40-1"><a href="#cb40-1" aria-hidden="true" tabindex="-1"></a>aqueduct_df <span class="op">=</span> df.loc[df.Station <span class="op">==</span> <span class="st">&#39;AQUEDUCT TRACK&#39;</span>].groupby(df[<span class="st">&#39;DateTime&#39;</span>].dt.month).agg({<span class="st">&#39;Entries+Exits&#39;</span>:<span class="st">&#39;mean&#39;</span>}).rename(columns<span class="op">=</span>{<span class="st">&quot;Entries+Exits&quot;</span>:<span class="st">&quot;Aqueduct Track&quot;</span>})</span>
<span id="cb40-2"><a href="#cb40-2" aria-hidden="true" tabindex="-1"></a>beach44_df <span class="op">=</span>  df.loc[df.Station <span class="op">==</span> <span class="st">&#39;BEACH 44 ST&#39;</span>].groupby(df[<span class="st">&#39;DateTime&#39;</span>].dt.month).agg({<span class="st">&#39;Entries+Exits&#39;</span>:<span class="st">&#39;mean&#39;</span>}).rename(columns<span class="op">=</span>{<span class="st">&quot;Entries+Exits&quot;</span>:<span class="st">&quot;Beach 44 ST&quot;</span>})</span>
<span id="cb40-3"><a href="#cb40-3" aria-hidden="true" tabindex="-1"></a>beach90_df <span class="op">=</span>  df.loc[df.Station <span class="op">==</span> <span class="st">&#39;BEACH 90 ST&#39;</span>].groupby(df[<span class="st">&#39;DateTime&#39;</span>].dt.month).agg({<span class="st">&#39;Entries+Exits&#39;</span>:<span class="st">&#39;mean&#39;</span>}).rename(columns<span class="op">=</span>{<span class="st">&quot;Entries+Exits&quot;</span>:<span class="st">&quot;Beach 90 ST&quot;</span>})</span>
<span id="cb40-4"><a href="#cb40-4" aria-hidden="true" tabindex="-1"></a>beach44_df.join(beach90_df).join(aqueduct_df).fillna(<span class="dv">0</span>).plot(kind<span class="op">=</span><span class="st">&#39;line&#39;</span>)</span></code></pre></div>
<div class="output execute_result" data-execution_count="37">
<pre><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7ffbc967e250&gt;</code></pre>
</div>
<div class="output display_data">
<p><img src="vertopal_f3465f12660048fb84ae161b90152882/4f52294e2c3c65f00ed912917ec550bbad8464a3.png" /></p>
</div>
</div>
<section id="stations-with-largest-decline-in-2013" class="cell markdown">
<h4>Stations with largest decline in 2013</h4>
</section>
<div class="cell code" data-execution_count="38">
<div class="sourceCode" id="cb42"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb42-1"><a href="#cb42-1" aria-hidden="true" tabindex="-1"></a>q_df.sort_values(<span class="st">&#39;PercentChange&#39;</span>).head(<span class="dv">3</span>)</span></code></pre></div>
<div class="output execute_result" data-execution_count="38">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Q1Mean</th>
      <th>Q4Mean</th>
      <th>PercentChange</th>
    </tr>
    <tr>
      <th>Station</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>HOWARD BCH-JFK</th>
      <td>118.424049</td>
      <td>49.343952</td>
      <td>-58.333</td>
    </tr>
    <tr>
      <th>WHITEHALL ST</th>
      <td>217.121889</td>
      <td>90.847422</td>
      <td>-58.158</td>
    </tr>
    <tr>
      <th>DYCKMAN ST</th>
      <td>511.564791</td>
      <td>230.912285</td>
      <td>-54.862</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell code" data-execution_count="39">
<div class="sourceCode" id="cb43"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb43-1"><a href="#cb43-1" aria-hidden="true" tabindex="-1"></a>howard_df <span class="op">=</span> df.loc[df.Station <span class="op">==</span> <span class="st">&#39;HOWARD BCH-JFK&#39;</span>].groupby(df[<span class="st">&#39;DateTime&#39;</span>].dt.month).agg({<span class="st">&#39;Entries+Exits&#39;</span>:<span class="st">&#39;mean&#39;</span>}).rename(columns<span class="op">=</span>{<span class="st">&quot;Entries+Exits&quot;</span>:<span class="st">&quot;Howard Beach JFK&quot;</span>})</span>
<span id="cb43-2"><a href="#cb43-2" aria-hidden="true" tabindex="-1"></a>whitehall_df <span class="op">=</span>  df.loc[df.Station <span class="op">==</span> <span class="st">&#39;WHITEHALL ST&#39;</span>].groupby(df[<span class="st">&#39;DateTime&#39;</span>].dt.month).agg({<span class="st">&#39;Entries+Exits&#39;</span>:<span class="st">&#39;mean&#39;</span>}).rename(columns<span class="op">=</span>{<span class="st">&quot;Entries+Exits&quot;</span>:<span class="st">&quot;Whitehall St&quot;</span>})</span>
<span id="cb43-3"><a href="#cb43-3" aria-hidden="true" tabindex="-1"></a>dyckman_df <span class="op">=</span>  df.loc[df.Station <span class="op">==</span> <span class="st">&#39;DYCKMAN ST&#39;</span>].groupby(df[<span class="st">&#39;DateTime&#39;</span>].dt.month).agg({<span class="st">&#39;Entries+Exits&#39;</span>:<span class="st">&#39;mean&#39;</span>}).rename(columns<span class="op">=</span>{<span class="st">&quot;Entries+Exits&quot;</span>:<span class="st">&quot;Dyckman St&quot;</span>})</span>
<span id="cb43-4"><a href="#cb43-4" aria-hidden="true" tabindex="-1"></a>howard_df.join(whitehall_df).join(dyckman_df).fillna(<span class="dv">0</span>).plot(kind<span class="op">=</span><span class="st">&#39;line&#39;</span>)</span></code></pre></div>
<div class="output execute_result" data-execution_count="39">
<pre><code>&lt;matplotlib.axes._subplots.AxesSubplot at 0x7ffbc8a365d0&gt;</code></pre>
</div>
<div class="output display_data">
<p><img src="vertopal_f3465f12660048fb84ae161b90152882/94297163d97f2be1a5800aa518d6375e84c456ed.png" /></p>
</div>
</div>
<section id="answer" class="cell markdown">
<h3>ANSWER</h3>
<h4 id="stations-with-largest-growth">Stations with largest growth</h4>
<ul>
<li>Beach 90 St: +86,513%</li>
<li>Aqueduct Track: +11,488%</li>
<li>Beach 44 St: +1710%</li>
</ul>
<p>Fun Fact: A quick google search shows that the Beach St stations were actually entirely or partially closed due to damage from Hurricane Sandy. They opened back up in May 2013, which corresponds to the sharp increase in overall traffic in month 5. Alternatively, Aqueduct track was close from 2011-2013 to rebuild it for better access to the Resorts World Casino, opening back up in August 2013.</p>
<h4 id="stations-with-largest-decline">Stations with largest decline</h4>
<ul>
<li>Howard Beach JFK: -58.3%</li>
<li>Whitehall St: -58.1%</li>
<li>Dyckman St: -54.8%</li>
</ul>
<p>Fun Fact: Again, Hurricane Sandy comes into play. Because of numerous closings of other subway stations that were damaged by the hurricane, Howard Beach JFK served as the alternative route while these stations were rebuilt. As a result, Howard Beach JFK had very high ridership numbers early in the year, but as the closed stations re-opened the traffic fell back to normal levels. On the other hand, Whitehall St and Dyckman St experienced decline in traffic because they went under rehabilitation work in the later part of 2013.</p>
</section>
<div class="cell markdown">
<hr />
</div>
<section id="question-5-what-dates-are-the-least-busy-could-you-identify-days-on-which-stations-were-not-operating-at-full-capacity-or-closed-entirely" class="cell markdown">
<h2>Question 5: What dates are the least busy? Could you identify days on which stations were not operating at full capacity or closed entirely?</h2>
</section>
<section id="least-busy-days" class="cell markdown">
<h4>Least Busy Days</h4>
</section>
<div class="cell code" data-execution_count="40">
<div class="sourceCode" id="cb45"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb45-1"><a href="#cb45-1" aria-hidden="true" tabindex="-1"></a>df[<span class="st">&#39;DATE&#39;</span>] <span class="op">=</span> df[<span class="st">&#39;DateTime&#39;</span>].dt.date</span>
<span id="cb45-2"><a href="#cb45-2" aria-hidden="true" tabindex="-1"></a>least_busy_days <span class="op">=</span> pd.DataFrame(df.groupby(<span class="st">&#39;DATE&#39;</span>)[<span class="st">&#39;Entries+Exits&#39;</span>].<span class="bu">sum</span>().sort_values().head(<span class="dv">3</span>)).reset_index()</span>
<span id="cb45-3"><a href="#cb45-3" aria-hidden="true" tabindex="-1"></a>least_busy_days[<span class="st">&#39;DOW&#39;</span>] <span class="op">=</span> pd.to_datetime(least_busy_days[<span class="st">&#39;DATE&#39;</span>]).dt.day_name()</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="41">
<div class="sourceCode" id="cb46"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb46-1"><a href="#cb46-1" aria-hidden="true" tabindex="-1"></a>least_busy_days</span></code></pre></div>
<div class="output execute_result" data-execution_count="41">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>DATE</th>
      <th>Entries+Exits</th>
      <th>DOW</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2013-12-25</td>
      <td>3452962.0</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2013-01-01</td>
      <td>3557056.0</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2013-11-28</td>
      <td>4281943.0</td>
      <td>Thursday</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell markdown">
<p>Not too surprising that the least traveled days happen to be the biggest holidays of the year with Christmas, New Years, and Thanksgiving taking the first, second, and third place, respectively.</p>
</div>
<section id="closed-stations" class="cell markdown">
<h4>Closed Stations</h4>
<p>Closed stations would have no entries or exits at any turnstile for the day.</p>
<p>In other words: Completely Closed = total ridership for the day is zero</p>
</section>
<div class="cell code" data-execution_count="42">
<div class="sourceCode" id="cb47"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb47-1"><a href="#cb47-1" aria-hidden="true" tabindex="-1"></a>closed_stations <span class="op">=</span> df.groupby([<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;DATE&#39;</span>])[<span class="st">&#39;Entries+Exits&#39;</span>].<span class="bu">sum</span>().to_frame(<span class="st">&#39;DailyTraffic&#39;</span>).query(<span class="st">&quot;DailyTraffic == 0&quot;</span>)</span>
<span id="cb47-2"><a href="#cb47-2" aria-hidden="true" tabindex="-1"></a>closed_stations <span class="op">=</span> closed_stations.reset_index().groupby(<span class="st">&#39;DATE&#39;</span>).agg(<span class="kw">lambda</span> x: x.tolist())</span>
<span id="cb47-3"><a href="#cb47-3" aria-hidden="true" tabindex="-1"></a>closed_stations[<span class="st">&#39;NumberOfStationsClosed&#39;</span>] <span class="op">=</span> closed_stations[<span class="st">&#39;Station&#39;</span>].<span class="bu">apply</span>(<span class="kw">lambda</span> x: <span class="bu">len</span>(x))</span>
<span id="cb47-4"><a href="#cb47-4" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot; Number of days which have a station closed: </span><span class="sc">{</span><span class="bu">len</span>(closed_stations)<span class="sc">}</span><span class="ss">&quot;</span>)</span>
<span id="cb47-5"><a href="#cb47-5" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="ss">f&quot; Number of stations closed for the day throughout 2013: </span><span class="sc">{</span>closed_stations<span class="sc">.</span>NumberOfStationsClosed<span class="sc">.</span><span class="bu">sum</span>()<span class="sc">}</span><span class="ss">&quot;</span>)</span></code></pre></div>
<div class="output stream stdout">
<pre><code> Number of days which have a station closed: 152
 Number of stations closed for the day throughout 2013: 213
</code></pre>
</div>
</div>
<div class="cell code" data-execution_count="43">
<div class="sourceCode" id="cb49"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb49-1"><a href="#cb49-1" aria-hidden="true" tabindex="-1"></a>closed_stations.sort_values(<span class="st">&#39;NumberOfStationsClosed&#39;</span>, ascending<span class="op">=</span><span class="va">False</span>).drop(columns<span class="op">=</span>[<span class="st">&#39;DailyTraffic&#39;</span>]).head()</span></code></pre></div>
<div class="output execute_result" data-execution_count="43">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Station</th>
      <th>NumberOfStationsClosed</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-05-18</th>
      <td>[BEACH 105 ST, BEACH 90 ST, BEACH 98 ST, ORCHA...</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2013-05-19</th>
      <td>[BEACH 105 ST, BEACH 44 ST, BEACH 98 ST, ORCHA...</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2013-04-07</th>
      <td>[190 ST, AQUEDUCT TRACK, CRESCENT ST, FOREST P...</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2013-03-31</th>
      <td>[AQUEDUCT TRACK, BEACH 90 ST, CLEVELAND ST, CR...</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2013-01-06</th>
      <td>[14TH STREET, 9TH STREET, KINGSTON AVE, TWENTY...</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<div class="cell markdown">
<p>5 stations were closed on May 18th which was the highest amount for the year</p>
</div>
<section id="partial-capacity" class="cell markdown">
<h4>Partial Capacity</h4>
<p>Stations not operating at full capacity would have no entries or exits for only a portion of the turnstiles for the day.</p>
<p>Partial = some turnstile are zero</p>
</section>
<div class="cell code" data-execution_count="44">
<div class="sourceCode" id="cb50"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb50-1"><a href="#cb50-1" aria-hidden="true" tabindex="-1"></a>closed_turnstiles <span class="op">=</span> df.groupby([<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;TurnStile&#39;</span>,<span class="st">&#39;DATE&#39;</span>])[<span class="st">&#39;Entries+Exits&#39;</span>].<span class="bu">sum</span>().to_frame(<span class="st">&#39;DailyTSTraffic&#39;</span>).query(<span class="st">&quot;DailyTSTraffic == 0&quot;</span>)</span>
<span id="cb50-2"><a href="#cb50-2" aria-hidden="true" tabindex="-1"></a>num_closed_ts <span class="op">=</span> closed_turnstiles.reset_index().groupby([<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;DATE&#39;</span>]).count().drop(columns<span class="op">=</span>[<span class="st">&quot;TurnStile&quot;</span>]).rename(columns<span class="op">=</span>{<span class="st">&#39;DailyTSTraffic&#39;</span>:<span class="st">&#39;NumberClosed&#39;</span>})</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="46">
<div class="sourceCode" id="cb51"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb51-1"><a href="#cb51-1" aria-hidden="true" tabindex="-1"></a>partial_operating <span class="op">=</span> df[[<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;TurnStile&#39;</span>,<span class="st">&#39;DateTime&#39;</span>,<span class="st">&#39;DATE&#39;</span>]].merge(num_closed_ts.reset_index(), on<span class="op">=</span>[<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;DATE&#39;</span>], how<span class="op">=</span><span class="st">&#39;left&#39;</span>)</span>
<span id="cb51-2"><a href="#cb51-2" aria-hidden="true" tabindex="-1"></a>partial_operating <span class="op">=</span> partial_operating.query(<span class="st">&quot;NumberClosed &gt; 0&quot;</span>)</span>
<span id="cb51-3"><a href="#cb51-3" aria-hidden="true" tabindex="-1"></a>station_turnstiles <span class="op">=</span> partial_operating.drop_duplicates(subset<span class="op">=</span>[<span class="st">&#39;TurnStile&#39;</span>,<span class="st">&#39;DATE&#39;</span>]).groupby([<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;DATE&#39;</span>]).size().to_frame(<span class="st">&#39;TotalTurnStiles&#39;</span>)</span>
<span id="cb51-4"><a href="#cb51-4" aria-hidden="true" tabindex="-1"></a>partial_operating <span class="op">=</span> partial_operating.merge(station_turnstiles, on<span class="op">=</span>[<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;DATE&#39;</span>], how<span class="op">=</span><span class="st">&#39;left&#39;</span>)[[<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;DATE&#39;</span>,<span class="st">&#39;NumberClosed&#39;</span>,<span class="st">&#39;TotalTurnStiles&#39;</span>]]</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="47">
<div class="sourceCode" id="cb52"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb52-1"><a href="#cb52-1" aria-hidden="true" tabindex="-1"></a>partial_operating[<span class="st">&#39;OperatingCapacity&#39;</span>] <span class="op">=</span> <span class="bu">round</span>(<span class="dv">100</span><span class="op">*</span>(</span>
<span id="cb52-2"><a href="#cb52-2" aria-hidden="true" tabindex="-1"></a>    (partial_operating[<span class="st">&#39;TotalTurnStiles&#39;</span>] <span class="op">-</span> partial_operating[<span class="st">&#39;NumberClosed&#39;</span>])<span class="op">/</span>partial_operating[<span class="st">&#39;TotalTurnStiles&#39;</span>]),<span class="dv">2</span>)</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="48">
<div class="sourceCode" id="cb53"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb53-1"><a href="#cb53-1" aria-hidden="true" tabindex="-1"></a>partial_operating <span class="op">=</span> partial_operating.drop_duplicates(subset<span class="op">=</span>[<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;DATE&#39;</span>]).reset_index().groupby(<span class="st">&#39;DATE&#39;</span>).agg(<span class="kw">lambda</span> x: x.tolist())</span>
<span id="cb53-2"><a href="#cb53-2" aria-hidden="true" tabindex="-1"></a>partial_operating[<span class="st">&#39;NumberOfPartialOperatingStations&#39;</span>] <span class="op">=</span> partial_operating[<span class="st">&#39;Station&#39;</span>].<span class="bu">apply</span>(<span class="kw">lambda</span> x: <span class="bu">len</span>(x))</span>
<span id="cb53-3"><a href="#cb53-3" aria-hidden="true" tabindex="-1"></a>partial_operating[[<span class="st">&#39;Station&#39;</span>,<span class="st">&#39;OperatingCapacity&#39;</span>,<span class="st">&#39;NumberOfPartialOperatingStations&#39;</span>]].sort_values(<span class="st">&#39;NumberOfPartialOperatingStations&#39;</span>,ascending<span class="op">=</span><span class="va">False</span>).head()</span></code></pre></div>
<div class="output execute_result" data-execution_count="48">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Station</th>
      <th>OperatingCapacity</th>
      <th>NumberOfPartialOperatingStations</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-08-18</th>
      <td>[LEXINGTON AVE, 5 AVE-59 ST, 49 ST-7 AVE, 34 S...</td>
      <td>[80.0, 85.71, 90.91, 96.3, 94.74, 85.71, 44.44...</td>
      <td>171</td>
    </tr>
    <tr>
      <th>2013-11-17</th>
      <td>[LEXINGTON AVE, 5 AVE-59 ST, 49 ST-7 AVE, 34 S...</td>
      <td>[80.0, 92.86, 90.91, 96.3, 97.37, 82.14, 33.33...</td>
      <td>170</td>
    </tr>
    <tr>
      <th>2013-10-20</th>
      <td>[LEXINGTON AVE, 5 AVE-59 ST, 49 ST-7 AVE, 42 S...</td>
      <td>[80.0, 85.71, 95.45, 96.0, 98.15, 97.37, 87.5,...</td>
      <td>168</td>
    </tr>
    <tr>
      <th>2013-10-06</th>
      <td>[LEXINGTON AVE, 5 AVE-59 ST, 49 ST-7 AVE, 42 S...</td>
      <td>[90.0, 92.86, 90.91, 96.0, 98.15, 83.93, 66.67...</td>
      <td>166</td>
    </tr>
    <tr>
      <th>2013-11-03</th>
      <td>[LEXINGTON AVE, 5 AVE-59 ST, 49 ST-7 AVE, 34 S...</td>
      <td>[80.0, 92.86, 90.91, 98.15, 87.5, 66.67, 17.65...</td>
      <td>161</td>
    </tr>
  </tbody>
</table>
</div>
</div>
</div>
<section id="answer" class="cell markdown">
<h3>ANSWER</h3>
<h4 id="least-busy-dates">Least Busy Dates</h4>
<p>Not too surprising that the biggest holidays are the least busy days</p>
<ul>
<li>Christmas (2013-12-25)</li>
<li>New Years (2013-01-01)</li>
<li>Thanksgiving (2013-11-28)</li>
</ul>
<h4 id="completely-closed-and-partially-closed-stations">Completely closed and partially closed stations</h4>
<p>Refer to the above data frames to see the list of stations that are either completely or partially closed on certain dates.</p>
</section>
<section id="bonus-what-hour-is-the-busiest-for-station-canal-st-in-q1-2013" class="cell markdown">
<h2>Bonus: What hour is the busiest for station CANAL ST in Q1 2013?</h2>
</section>
<div class="cell code" data-execution_count="49">
<div class="sourceCode" id="cb54"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb54-1"><a href="#cb54-1" aria-hidden="true" tabindex="-1"></a><span class="co"># filter data down to CANAL ST in Q1</span></span>
<span id="cb54-2"><a href="#cb54-2" aria-hidden="true" tabindex="-1"></a>canalq12013 <span class="op">=</span> df.loc[(df[<span class="st">&#39;Station&#39;</span>] <span class="op">==</span> <span class="st">&#39;CANAL ST&#39;</span>) <span class="op">&amp;</span> (df[<span class="st">&#39;DateTime&#39;</span>].dt.month.isin([<span class="dv">1</span>,<span class="dv">2</span>,<span class="dv">3</span>]))]</span></code></pre></div>
</div>
<div class="cell code" data-execution_count="50">
<div class="sourceCode" id="cb55"><pre class="sourceCode python"><code class="sourceCode python"><span id="cb55-1"><a href="#cb55-1" aria-hidden="true" tabindex="-1"></a><span class="co"># resample data to get hourly frequency, using linear interpolation to fill in hour numbers</span></span>
<span id="cb55-2"><a href="#cb55-2" aria-hidden="true" tabindex="-1"></a>canalq12013 <span class="op">=</span> canalq12013.groupby([<span class="st">&#39;TurnStile&#39;</span>]).resample(<span class="st">&#39;60T&#39;</span>, on<span class="op">=</span><span class="st">&#39;DateTime&#39;</span>).mean().reset_index()</span>
<span id="cb55-3"><a href="#cb55-3" aria-hidden="true" tabindex="-1"></a>canalq12013[<span class="st">&#39;Hour&#39;</span>] <span class="op">=</span> canalq12013[<span class="st">&#39;DateTime&#39;</span>].dt.hour</span>
<span id="cb55-4"><a href="#cb55-4" aria-hidden="true" tabindex="-1"></a>canalq12013.interpolate(method<span class="op">=</span><span class="st">&#39;linear&#39;</span>).reset_index().groupby(<span class="st">&#39;Hour&#39;</span>).mean().sort_values(<span class="st">&#39;Entries+Exits&#39;</span>, ascending<span class="op">=</span><span class="va">False</span>)[<span class="st">&#39;Entries+Exits&#39;</span>].head()</span></code></pre></div>
<div class="output execute_result" data-execution_count="50">
<pre><code>Hour
20    627.749974
19    626.143669
18    588.330532
17    551.228967
21    540.642590
Name: Entries+Exits, dtype: float64</code></pre>
</div>
</div>
<section id="answer" class="cell markdown">
<h3>ANSWER</h3>
<p>The busiest hour for CANAL ST in Q1 2013 is hour 20 (8pm), followed closely by hour 19 and 18. So, it looks like 5-9pm sees the highest traffic. Makes sense for rush hour</p>
</section>
</body>
</html>
