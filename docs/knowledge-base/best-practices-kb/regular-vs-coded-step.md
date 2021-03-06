---
title: Regular vs. Coded Step
page_title: Regular vs. Coded Step
description: The benefits of recorded steps against coded and vice versa. 
position: 1
---
# Regular vs. Coded Step #

*We've noticed that a considerable number our customers' projects rely heavily on code in order to implement their test cases.*

Test Studio is designed to keep coding to a minimum. Test Studio will automatically generate for you steps that correspond to lengthy code blocks. Let's look at a simple example. Let's say you need to verify that the *alt* property of the logo on the Wikipedia main page matches the text WikipediA. This is added quickly and easily in Test Studio and a single regular step is generated. If you convert this step to code, however, it will look like this:

```C#
Pages.Wikipedia.WikipediAImage.AssertAttribute().Value("alt", ArtOfTest.Common.StringCompareType.Contains, "WikipediA");
```

Regular and coded steps visible here:

![Regular vs coded step][1]

The single line of code might seem easy to write. However the following element:

```C#
Pages.Wikipedia.WikipediAImage
```

is actually a variable that represents Find Logic generated by Test Studio. So in this case here's the code that would replace the step without using anything generated by Test Studio:

```C#
HtmlImage logo = Find.ByExpression<HtmlImage>(@"src=//upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Wikipedia_wordmark.svg/174px-Wikipedia_wordmark.svg.png");

logo.AssertAttribute().Value("alt", ArtOfTest.Common.StringCompareType.Contains, "WikipediA");
```

The first part of this code is Find Logic. This is one of the challenging aspects of of UI automation and a lot of the times you'll be unable to find a good way to identify an element. Particularly when no ID (HTML) or <a href="http://blogs.telerik.com/automated-testing-tools/posts/11-03-01/best-practices-element-identification-with-id-and-automationid" target="_blank">Automation ID</a> (Silverlight) has been implemented. Test Studio will do that for you, saving you a lot of work and improving the reliability of your test. Additionally, Test Studio allows you to control and change the Find Logic as seen <a href="/features/elements-explorer/find-element" target="_blank">here</a> and <a href="/features/project-settings/identification-logic" target="_blank">here</a>.
 
Additionally using coded step increases the chances of hitting compilation errors and other errors related to building a test project.

[1]: /img/knowledge-base/best-practices-kb/regular-vs-coded-step/fig1.png
