---
title: "XML 文件註解 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.xml"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, XML 程式碼註解"
  - "C# 原始程式碼檔"
  - "註解 [C#], XML"
  - "文件註解 [C#]"
  - "XML [C#], 程式碼註解"
  - "XML 文件註解 [C#]"
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# XML 文件註解 (C# 程式設計手冊)
在 Visual C\# 中，您可以加入程式碼的文件，加入的方法是在原始程式碼中，於註解所參考程式碼區塊之前的特殊註解欄位 \(以三個斜線表示\) 中加入 XML 項目，例如：  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 當您使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 選項編譯時，編譯器將會搜尋原始程式碼中的所有 XML 標記，然後建立 XML 文件檔。  若要依據編譯器產生的檔案建立最後的文件，您可以建立自訂工具，或者是使用 [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) 這類工具。  
  
 若要參考 XML 項目，例如，您的函式處理要在 XML 文件註解中描述的特定 XML 項目，您可以使用標準引號機制 \(`<` 和 `>`\)。若要參考程式碼參考 \(`cref`\) 項目中的泛型識別項，您可以使用逸出字元 \(例如 `cref="List<T>"`\) 或大括號 \(`cref="List{T}"`\)。視為特殊案例的情形是，編譯器將大括號剖析為角括號，如此在參考泛型識別項時，文件註解撰寫起來就變得不那麼複雜。  
  
> [!NOTE]
>  XML 文件註解並不是中繼資料，這些註解不會包含在編譯的組件內，因此不能透過反映存取。  
  
## 本章節內容  
  
-   [建議的文件註解標記](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [處理 XML 檔案](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [文件標記的分隔符號](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [如何：使用 XML 文件功能](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## 相關章節  
 如需詳細資訊，請參閱：  
  
-   [\/doc \(處理文件註解\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)