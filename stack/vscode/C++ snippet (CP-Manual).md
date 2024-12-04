---
Owner: Sharafat Karim
Last edited time: 2023-09-16T10:07
---


```C++
\#include <bits/stdc++.h>
using namespace std;

// Simple template by sharafat 
typedef long long LL;
typedef pair<int, int> pii;
typedef pair<LL, LL> pll;
typedef pair<string, string> pss;
typedef vector<int> vi;
typedef vector<vi> vvi;
typedef vector<pii> vii;
typedef vector<LL> vl;
typedef vector<vl> vvl;

\#define endl '\n'

int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
\#ifndef ONLINE_JUDGE
    freopen("input.txt", "r", stdin);
    freopen("output.txt", "w", stdout);
\#endif
    // Code starts here

    Your Code Here

    // Code ends here
\#ifndef ONLINE_JUDGE
    cerr << "time taken : " << (float)clock() / CLOCKS_PER_SEC << " secs" << endl;
\#endif
    return 0;
}
```

---

The template (JSON)

```C++
{
	// Place your global snippets here. Each snippet is defined under a snippet name and has a scope, prefix, body and 
	// description. Add comma separated ids of the languages where the snippet is applicable in the scope field. If scope 
	// is left empty or omitted, the snippet gets applied to all languages. The prefix is what is 
	// used to trigger the snippet and the body will be expanded and inserted. Possible variables are: 
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. 
	// Placeholders with the same ids are connected.
	// Example:
	"Competitive programming": {
		"scope": "cpp",
		"prefix": "compete",
		"body": [
			"\#include <bits/stdc++.h>",
			"using namespace std;",
			"",
			"// Simple template by sharafat ",
			"typedef long long LL;",
			"typedef pair<int, int> pii;",
			"typedef pair<LL, LL> pll;",
			"typedef pair<string, string> pss;",
			"typedef vector<int> vi;",
			"typedef vector<vi> vvi;",
			"typedef vector<pii> vii;",
			"typedef vector<LL> vl;",
			"typedef vector<vl> vvl;",
			"",
			"\#define endl '\\n'",
			"",
			"int main()",
			"{",
			"    ios_base::sync_with_stdio(false);",
			"    cin.tie(NULL);",
			"\#ifndef ONLINE_JUDGE",
			"    freopen(\"input.txt\", \"r\", stdin);",
			"    freopen(\"output.txt\", \"w\", stdout);",
			"\#endif",
			"    // Code starts here",
			"",
			"	${0:Your Code Here}",
			"",
			"    // Code ends here",
			"\#ifndef ONLINE_JUDGE",
			"    cerr << \"time taken : \" << (float)clock() / CLOCKS_PER_SEC << \" secs\" << endl;",
			"\#endif",
			"    return 0;",
			"}",
			""
		],
		"description": "Competitive programming template"
	}
}
```

---

Refs site

> [!info] snippet generator  
> Snippet generator for Visual Studio Code, Sublime Text and Atom.  
> [https://snippet-generator.app/?description=&tabtrigger=&snippet=&mode=vscode](https://snippet-generator.app/?description=&tabtrigger=&snippet=&mode=vscode)