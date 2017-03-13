---
title: "string (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "string"
  - "string_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "字串 [C#]，參考"
  - "@ 字串常值"
  - "字串常值 [C#]"
  - "string 關鍵字 [C#]"
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# string (C# 參考)
`string` 型別表示零個或多個 Unicode 字元序列。  `string` 是 .NET Framework 中 <xref:System.String> 的別名。  
  
 雖然 `string` 是參考型別 \(Reference Type\)，但是等號比較運算子 \(`==` 和 `!=`\) 的定義目的是比較 `string` 物件 \(而不是參考\) 的值。  這讓字串相等的測試更具直覺性。  例如：  
  
```c#  
  
      string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 這會先顯示 "True" 然後再顯示 "False"，因為字串的內容相同但是 `a` 和 `b` 並未參考相同的字串執行個體。  
  
 \+ 運算子串連字串：  
  
```c#  
  
string a = "good " + "morning";  
```  
  
 這會建立包含 "good morning" 的字串物件。  
  
 字串是「*不可變動的*」\(Immutable\)，這表示字串物件建立之後，將無法變更該物件的內容 \(雖然語法看起來好像允許您變更\)。  例如，當您撰寫這段程式碼時，編譯器 \(Compiler\) 實際上會建立新的字串物件來保存新的字串序列 \(Sequence\)，而且新物件會指派至 b。  接著字串「h」就可進行記憶體回收。  
  
```c#  
  
      string b = "h";  
b += "ello";  
```  
  
 \[\] 運算子可以用來以唯讀方式存取 `string` 的個別字元：  
  
```c#  
  
      string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 字串常值是 `string` 型別而且可以寫成兩種格式，以引號括住和以 @ 括住。  以引號括住的字串常值由雙引號 \("\) 包圍起來：  
  
```c#  
"good morning"  // a string literal  
```  
  
 字串常值可以包含任何字元常值。  也包括逸出序列。  下列範例使用 `\\` 反斜線的逸出序列、`\u0066` 表示字母 f，而 `\n` 表示新的一行。  
  
```  
  
      string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  逸出程式碼 `\`u`dddd` \(其中 `dddd` 是四位數的數字\) 表示 Unicode 字元 U\+`dddd`。  八位數字的 Unicode  逸出程式碼也可以辨識：`\Udddddddd`。  
  
 逐字字串常值是以 @ 做為開頭並放在雙引號裡。  例如：  
  
```c#  
@"good morning"  // a string literal  
```  
  
 逐字字串的優點是「*不會*」處理逸出序列，這讓它很容易撰寫，例如，完整檔案名稱：  
  
```c#  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 若要在 @ 括住的字串裡包含雙引號，請重複雙引號：  
  
```c#  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 @ 符號的另一種用途是使用屬於 C\# 關鍵字之參考的 \([\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)\) 識別項。  
  
 如需 C\# 中字串的詳細資訊，請參閱[字串](../../../csharp/programming-guide/strings/index.md)。  
  
## 範例  
 [!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [使用字串的最佳作法](../Topic/Best%20Practices%20for%20Using%20Strings%20in%20the%20.NET%20Framework.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [參考類型](../../../csharp/language-reference/keywords/reference-types.md)   
 [實值類型](../../../csharp/language-reference/keywords/value-types.md)   
 [基本字串作業](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)   
 [建立新字串](../Topic/Creating%20New%20Strings%20in%20the%20.NET%20Framework.md)   
 [格式化數值結果表](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)