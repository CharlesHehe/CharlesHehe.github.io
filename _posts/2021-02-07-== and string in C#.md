# == and string in C sharp

Hi, guys. I am deploying Elasticsearch service into our E-commerce website. The cluster is steady now, therefore I managed to code DSL on application level within .net core framework. I have to commit I am a layman for C# by now. Because I use "==" to compare string value and got a scolding from my leader.
* This is what I use:

```
if (sortInfo == "createTime-desc")

```

* My leader suggestions:

```
if (string.Equals(sortInfo, "createTime-desc", StringComparison.OrdinalIgnoreCase))
{}
```

### What is the difference?

* Equals function is called on a string object, and in the other case the == operator is called on the System.Object type. string and object implement equality differently from each other (value vs. reference respectively).In the specific case of determining string equality, the industry preference is to use neither == nor string.Equals(string) most of the time. These methods determine whether two string are the same character-for-character, which is rarely the correct behavior. It is better to use string.Equals(string, StringComparison), which allows you to specify a particular type of comparison. By using the correct comparison, you can avoid a lot of potential (very hard to diagnose) bugs.[From here](https://stackoverflow.com/questions/3678792/are-string-equals-and-operator-really-same)

I seems got the key point. "==" is for reference compare or value compare or both. "string.Equals(string, StringComparison)" is better just for value comparison.
