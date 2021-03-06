@typedef {String} can-stache/expressions/bracket Bracket Expression
@parent can-stache/expressions

@signature `[key]`

Evaluates `key` and looks up the result in the [can-view-scope scope].

```
{{[key]}}
```

  @param {can-stache/expressions/literal|can-stache/expressions/key-lookup|can-stache/expressions/call|can-stache/expressions/helper} key A [can-stache/expressions/literal Literal], [can-stache/expressions/key-lookup KeyLookup], [can-stache/expressions/call Call], or [can-stache/expressions/helper Helper] expression to evaluate and look up the result in the [can-view-scope scope].

@signature `CALL_EXPRESSION[key]`

Evaluates `key` and looks up the result in the return value of `CALL_EXPRESSION`.

```
{{method()[key]}}
```

  @param {can-stache/expressions/call|can-stache/expressions/helper|can-stache/expressions/key-lookup} CALL_EXPRESSION A [can-stache/expressions/call Call], [can-stache/expressions/helper Helper], or [can-stache/expressions/key-lookup KeyLookup] expression that may or may not return a value.

  @param {can-stache/expressions/literal|can-stache/expressions/key-lookup|can-stache/expressions/call|can-stache/expressions/helper} key A [can-stache/expressions/literal Literal], [can-stache/expressions/key-lookup KeyLookup], [can-stache/expressions/call Call], or [can-stache/expressions/helper Helper] expression to evaluate and look up the result in the result of `CALL_EXPRESSION`.

@body

## Use

A bracket expression can be used to look up a dynamic property in the [can-view-scope scope]. This looks like:

```
Template:
	<h1>{{[key]}}</h1>

Data:
	{
		key: "name",
		name: "Kevin"
	}

Result:
	<h1>Kevin</h1>
```

This can be useful for looking up values using keys containing non-alphabetic characters:

```
Template:
	<h1>{{["person:name"]}}</h1>

Data:
	{
		"person:name": "Kevin"
	}

Result:
	<h1>Kevin</h1>
```

Bracket expressions can also be used to look up a value in the result of another expression:

```
Template:
{{getPerson()[key]}}

Data:
	{
		key: "name",
		getPerson: function() {
			return {
				name: "Kevin"
			};
		}
	}

Result:
	<h1>Kevin</h1>
```
