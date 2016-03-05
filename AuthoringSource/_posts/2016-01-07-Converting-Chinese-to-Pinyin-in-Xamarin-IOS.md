--- 
layout: post
title: "Converting Chinese to Pinyin/Quanpin in Xamarin IOS development"
author: "Ke"
comments: true
---
For an IOS app with Chinese names, the names have to be sorted via Pinyin(it's like phonetic words), or people can barely locate anyone. 

And there are lots of solutions on the internet about how to sort Chinese in Object-C, Swift or C#. However I couldn't find any on how to do it in Xamarin IOS using C#. All the C# way won't work in the Xamarin IOS app althought it compiles happily. My understanding it's that Xamarin is just a mapping(I may put it too simple here) between languages, so whatever the .Net framework is doing based on the language do not get carried over to IOS. 

Luickly I found the mapping that Xamarin specificliy created just for the sake of mapping libraries in Object-C: [Foundation.NSMutableString](https://developer.xamarin.com/api/type/Foundation.NSMutableString/) and its method: 

```cssharp
ApplyTransform(NSStringTransform, Boolean, NSRange, out NSRange) : Boolean
```
The method converts Chinese into Pinyin with tones like this "zhōng wén". In my code I created an extension to sort by, however I think creating a field in the database to hold Pinyin would be more ideal.

To note here I tried to created this as a property as part of the database model however since it's inside of a portable class library so it doesn't have the Foundation namespace so I couldn't, hence the extension.

```csharp
using Foundation;
...
		public static string GetPinyin (this string input)
		{
			var output = new NSMutableString ();
			output.SetString (new NSString (input));
			var dumy = new NSRange ();
			output.ApplyTransform (NSStringTransform.MandarinToLatin, false, new NSRange (0, output.Length), out dumy);
			return output.ToString ();
		}
```

觉得这篇尤其需要堆积一点中文来提高SEO。

基本上问题就是中文通讯录的排序，在纯 IOS 和 C# 的开发环境里这都是很普通的事情，因为 Google 里搜下一大堆的。可是在 Xamarin 里用 C# 写 IOS 就不大一样了。 Object-C 和 Swift 都不能直接用，C# 的虽然可以写出来可以编译，但到了IOS那边是失效的因为框架里的功能是完全不一样的。

所幸 Xamarin 的人真的就写了几个纯粹为了对应的类，这里要用的是这个： [Foundation.NSMutableString](https://developer.xamarin.com/api/type/Foundation.NSMutableString/)。

用了这个可以把中文全部转换成拼音并且还包括音调，不过对不住没找到怎么是不包括音调了。但是有了这个东西后，至少排序不成问题了。

我的感觉是肯定还有更好的办法，不过暂时就先这样吧。

My feeling is that this is not the best way, but for now, it works.