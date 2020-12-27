taking words from <a href="http://cvsweb.openwall.com/cgi/cvsweb.cgi/Owl/packages/passwdqc/passwdqc/wordset_4k.c?rev=1.7;content-type=text%2Fplain">openwall's passwdqc's <em>wordset_4k.c</em></a> and <a href="https://github.com/mattbierner/urban-dictionary-word-list/tree/master/data">mattbierner's <em>Urban-Dictionary Word-List</em></a> (with some generic cleaning to remove some of the more rude ones...)
applying few Regular-Expression cleanups:
<pre>
^.{1,3}$               not too short
^.{6,}$                not too long
^.*[^a-z]+.*$          no lines with letters other than US-ASCII letters (A-Z) - but not using case-sensitive search/replace...
^.*(.)\1.*$            no repeating characters in 0 distance
^.*(.).\1.*$           no repeating characters in 1 distance
^.*(.)..\1.*$          no repeating characters in 2 distance
^.*(.).*\1.*$          no repeating characters in ANY distance
^[^aeiou]+$            at least one vowel in the line
^.[^aieou].*$          second letter needs to be a vowel
^.+[^aieou][^aieou]$   last-letters or one-before last-letter needs to be a vowel
</pre>

then and sort/unique using <a href="https://github.com/eladkarako/sortjs">eladkarako/sortjs</a>

it should leave short enough words,
which will be fun/rude generating passwords or random sentences which <em>(at least seems like..)</em> semi-meaningful ones.

after cleaning, sorting and such.. the file includes <code>34,843</code> lines.

the level of entropy/strength isn't high, and you'll probably find stuff such as <code>abcd</code>..
the magic happens when combining few of the words to a semi-meaningful sentence.

yes you know it, just like the one on XKCD:  -  <sub><a href="https://www.explainxkcd.com/wiki/index.php/936:_Password_Strength"><em>ExplainXKCD.com: 936: Password Strength</em></a></sub>
<a href="https://xkcd.com/936/"><img src="https://imgs.xkcd.com/comics/password_strength.png" title="To anyone who understands information theory and security and is in an infuriating argument with someone who does not (possibly involving mixed case), I sincerely apologize." alt="Password Strength"/></a>



<hr/>

<h2><code><a href="https://raw.githubusercontent.com/eladkarako/word-list/master/WORD_LIST.txt">WORD_LIST.txt</a></code> is a plain-text list (probably what you want...), <br/> while <code><a href="https://raw.githubusercontent.com/eladkarako/word-list/master/WORD_LIST.txt">WORD_LIST.js</a></code> will add the global variable <code>WORD_LIST</code> to your <code>window</code>, as an array. due to its size the file might take-a while to load up and your page might hang a bit...</h2>

you can download the entire repository using this link: https://github.com/eladkarako/word-list/archive/master.zip

<hr/>

to make the lists Windows-friendly I'm storing it as <code>"CR+LF"</code>-EOL,
but it is best to open it with Notepad2 or Notepad++.

<hr/>

Visit <a href="http://eladkarako.com/word-list/index.html">eladkarako.com/word-list</a> for 3 word password-generator.
