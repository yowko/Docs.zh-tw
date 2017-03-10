---
title: "&lt;summary&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<summary>"
  - "summary"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<summary> C# XML 標記"
  - "summary C# XML 標記"
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &lt;summary&gt; (C# 程式設計手冊)
## 語法  
  
```  
<summary>description</summary>  
```  
  
#### 參數  
 `description`  
 為物件的摘要。  
  
## 備註  
 \<summary\> 標記應用於描述型別或型別成員。  使用 [\<remarks\>](../../../csharp/programming-guide/xmldoc/remarks.md) 為型別描述加入補充資訊。  使用 [cref 屬性](../../../csharp/programming-guide/xmldoc/cref-attribute.md) \(Attribute\) 可以啟用如 [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) 的文件工具，以建立程式碼項目說明頁面的內部超連結。  
  
 \<summary\> 標記的內容會是 IntelliSense 中有關型別資訊的唯一來源，也會在[Object Browser Window](http://msdn.microsoft.com/zh-tw/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda)中顯示。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  若要依據編譯器產生的檔案建立最後的文件，您可以建立自訂工具，或者是使用 [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) 這類的工具。  
  
## 範例  
 [!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/summary_1.cs)]  
  
 前一個範例會產生下列 XML 檔案。  
  
```  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## 範例  
 下列程式碼範例示範如何建立泛型型別的 `cref` 參考。  
  
 [!code-cs[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/summary_2.cs)]  
  
 前一個範例會產生下列 XML 檔案。  
  
```  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
  
```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)