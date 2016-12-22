---
title: "如何：比較字串 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "比較字串 [C#]"
  - "字串 [C#], 比較"
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：比較字串 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

比較字串時，產生的結果會說明某一個字串大於或小於另一個字串，或是兩個字串相等。  用來判斷結果的規則需視執行的是「*序數比較*」\(Ordinal Comparison\) 還是「*區分文化特性比較*」\(Culture\-Sensitive Comparison\) 而定。  針對特定工作使用正確的比較類型很重要。  
  
 在不考慮語言慣例的情況下，需要比較或排序兩個字串的值時，請使用基本序數比較。  基本序數比較 \(`System.StringComparison.Ordinal`\) 必須區分大小寫，也就是說兩個字串的字元必須完全相符："and" 不等同於 "And" 或 "AND"。  最常用的變化是 `System.StringComparison.OrdinalIgnoreCase`，亦即 "and"、"And" 和 "AND" 都視為相符。  `StringComparison.OrdinalIgnoreCase` 通常用來比較檔案名稱、路徑名稱、網路路徑，以及其值不會根據使用者電腦的地區設定而改變的任何其他字串。  如需詳細資訊，請參閱<xref:System.StringComparison?displayProperty=fullName>。  
  
 區分文化特性比較通常用來比較及排序使用者輸入的字串，因為這類字串的字元和排序慣例可能會根據使用者電腦的地區設定而改變。  即便字串包含完全相同的字元，也可能會根據目前執行緒的文化特性而有不同的排序方式。  
  
> [!NOTE]
>  比較字串時，應該使用明確指定要執行何種比較的方法，  這樣就能讓程式碼更容易維護及供人們閱讀。  請盡可能使用 <xref:System.String?displayProperty=fullName> 和 <xref:System.Array?displayProperty=fullName> 類別 \(可使用 <xref:System.StringComparison> 列舉型別 \(Enumeration\) 參數\) 之方法的多載，方便指定要執行的比較類型。  比較字串時，最好避免使用 `==` 和 `!=` 運算子。  同時，也應避免使用 <xref:System.String.CompareTo%2A?displayProperty=fullName> 執行個體 \(Instance\) 方法，因為沒有一個多載會使用 <xref:System.StringComparison>。  
  
## 範例  
 在下列範例中，會針對其值不會根據使用者電腦的地區設定而改變的字串，示範如何正確比較這些字串。  此外，還會示範 C\# 的「*字串暫留*」\(String Interning\) 功能。  當程式宣告兩個以上完全相同的字串變數時，編譯器會將它們儲存至相同位置。  只要呼叫 <xref:System.Object.ReferenceEquals%2A> 方法，就能知道兩個字串實際上是參考到記憶體中的同一個物件。  <xref:System.String.Copy%2A?displayProperty=fullName> 方法可以用來避免暫留功能，如範例中所示。  
  
 [!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]  
  
## 範例  
 在下列範例中，會示範如何透過可使用 <xref:System.StringComparison> 列舉型別的 <xref:System.String?displayProperty=fullName> 方法，以慣用方式來比較字串。  請注意，這裡不採用 <xref:System.String.CompareTo%2A?displayProperty=fullName> 執行個體方法，因為沒有一個多載會使用 <xref:System.StringComparison>。  
  
 [!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]  
  
## 範例  
 在下列範例中，會示範如何透過可使用 <xref:System.StringComparer?displayProperty=fullName> 參數的靜態 <xref:System.Array> 方法，以區分文化特性方式來排序及搜尋陣列中的字串。  
  
 [!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]  
  
 當元素或索引鍵的型別為 `string` 時，集合類別 \(例如 <xref:System.Collections.Hashtable?displayProperty=fullName>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> 和 <xref:System.Collections.Generic.List%601?displayProperty=fullName>\) 都有可使用 <xref:System.StringComparer?displayProperty=fullName> 參數的建構函式 \(Constructor\)。  一般而言，您應該盡量使用這些建構函式，並指定 `Ordinal` 或 `OrdinalIgnoreCase`。  
  
## 請參閱  
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.StringComparer?displayProperty=fullName>   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [比較字串](../Topic/Comparing%20Strings%20in%20the%20.NET%20Framework.md)   
 [全球化和當地語系化應用程式](/visual-studio/ide/globalizing-and-localizing-applications)