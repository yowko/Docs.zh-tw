---
title: "dynamic (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "dynamic_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "動態 [C#]"
  - "dynamic 關鍵字 [C#]"
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# dynamic (C# 參考)
`dynamic` 型別可讓它發生所在的作業略過編譯時期型別檢查。  這些作業會改在執行階段解析。  `dynamic` 型別可簡化對 COM API \(例如 Office 自動化 API\)、動態 API \(例如 IronPython 程式庫\) 及 HTML 文件物件模型 \(DOM\) 的存取。  
  
 在大多數情況下，型別 `dynamic` 的行為就像 `object` 型別一樣。  不過，包含 `dynamic` 型別之運算式的作業沒有解析，或是由編譯器進行型別檢查。  編譯器將作業的相關資訊封裝在一起，而且可在之後使用該資訊來評估執行階段的作業。  做為程序的一部分，`dynamic` 型別的變數都會編譯為 `object` 型別的變數。  因此，類型 `dynamic` 只存在於編譯時間，而不存在於執行階段。  
  
 下列範例會對比類型為 `dynamic` 的變數與類型為 `object` 的變數。  若要在編譯時期確認每個變數的型別，將滑鼠指標停在 `WriteLine` 陳述式中 的 `dyn` 或  `obj` 上方。  IntelliSense 會針對 `dyn` 顯示 \[**動態**\]，並針對 `obj` 顯示\[**物件**\]。  
  
 [!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/csharp/dynamic_1.cs)]  
  
 `WriteLine` 陳述式會顯示 `dyn` 和 `obj` 的執行階段型別。  在此時，兩者都具有相同的型別，也就是整數。  產生以下輸出：  
  
 `System.Int32`  
  
 `System.Int32`  
  
 若要查看 `dyn` 和 `obj` 在編譯時期的差異，請在前一個範例的宣告和 `WriteLine` 陳述式之間加入下列兩行。  
  
```c#  
dyn = dyn + 3;  
obj = obj + 3;  
  
```  
  
 對於嘗試加入的整數和運算式 `obj + 3` 中的物件，會有編譯器錯誤的報告。  然而，沒有 `dyn + 3` 的錯誤報告。  由於 `dyn` 的類型是 `dynamic`，因此編譯時期不會檢查包含 `dyn` 的運算式。  
  
## 內容  
 `dynamic` 關鍵字可以直接出現，或是做為建構之型別的元件，在下列狀況出現：  
  
-   在宣告中，做為屬性、欄位、索引子、參數、傳回值、本機變數或型別條件約束的型別。  下列類別定義在數個不同的宣告中使用 `dynamic`。  
  
     [!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/csharp/dynamic_2.cs)]  
  
-   在明確的型別轉換中，做為轉換的目標型別  
  
     [!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/csharp/dynamic_3.cs)]  
  
-   在將型別當做值的任何內容中，例如在 `is` 運算子的右邊，或是 `as` 運算子，或是做為 `typeof` 的引數以當做建構之型別的一部分。  例如，`dynamic` 可在下列運算式中使用。  
  
     [!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/csharp/dynamic_4.cs)]  
  
## 範例  
 下列範例會在數個宣告中使用 `dynamic`。  `Main` 方法也會以執行階段型別檢查來對比編譯時期型別檢查。  
  
 [!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/csharp/dynamic_5.cs)]  
  
 如需詳細資訊與範例，請參閱[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)。  
  
## 請參閱  
 <xref:System.Dynamic.ExpandoObject?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [如何：使用 as 和 is 運算子進行安全轉型](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)   
 [逐步解說：建立和使用動態物件](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)