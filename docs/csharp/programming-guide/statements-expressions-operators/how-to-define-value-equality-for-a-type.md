---
title: "如何：定義類型的實值相等 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "Equals 方法 [C#], 覆寫"
  - "等價 [C#]"
  - "物件等價 [C#]"
  - "覆寫 Equals 方法 [C#]"
  - "實值相等 [C#]"
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：定義類型的實值相等 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

定義類別或結構時，需判斷是否有必要為型別建立實值相等 \(或等價\) 的自訂定義。  通常，當該型別的物件應加入至某種集合，或物件的主要目的是用來儲存一組欄位或屬性時，就會實作實值相等。  您可以根據對該型別中所有欄位和屬性的比較來定義實值相等，或也可以根據子集來進行定義。  不論使用哪種定義方法，對類別或結構而言，您的實作都必須遵循下列五項等價保證：  
  
1.  x.`Equals`\(x\) 會傳回 `true.` 。這稱為自反屬性。  
  
2.  x.`Equals`\(y\) 傳回  y.`Equals`\(x\) 的相同值。  這稱為對稱屬性。  
  
3.  如果 \(x.`Equals`\(y\) && y.`Equals`\(z\)\) 傳回 `true`，則 x.`Equals`\(z\) 會傳回 `true`。  這稱為可轉移屬性。  
  
4.  只要 x 和 y 所參考的物件沒有經過修改，後續叫用 x.`Equals`\(y\) 會傳回相同的值。  
  
5.  x.`Equals`\(null\) 傳回 `false`。  不過，null.Equals\(null\) 會擲回例外狀況，此項不遵守上述第二條規則。  
  
 您定義的結構已具有實值相等的預設實作，這是從 <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 方法的 <xref:System.ValueType?displayProperty=fullName> 覆寫繼承而來。  這項實作使用反映來檢查型別中所有公用和非公用的欄位及屬性。  此實作可以產生正確結果，但相較於您針對該型別特別撰寫的自訂實作卻慢得多。  
  
 對類別和結構而言，實值相等的實作細節並不一樣。  不過，類別和結構需要相同的實作相等基本步驟：  
  
1.  覆寫[虛擬](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 方法。  在大部分情況下，實作 `bool Equals( object obj )` 應呼叫型別特定的 `Equals` 方法，這是 <xref:System.IEquatable%601?displayProperty=fullName> 介面的實作  \(請參閱步驟 2\)。  
  
2.  提供型別特定的 `Equals` 方法，以便實作 <xref:System.IEquatable%601?displayProperty=fullName> 介面。  實際的等價比較是在這裡執行。  例如，您可能決定只比較型別中的一個或兩個欄位，以定義相等。  請勿從 `Equals` 擲回例外狀況。  僅適用於類別：此方法應該只檢查在類別中宣告的欄位。  方法應呼叫 `base.Equals`，檢查基底類別中的欄位   \(如果型別直接繼承自 <xref:System.Object>，則請勿採用此做法，因為 <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 的 <xref:System.Object> 實作會執行參考相等檢查\)。  
  
3.  選用但為建議動作：多載 [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) 和 [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) 運算子。  
  
4.  覆寫 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>，讓具有實值相等的兩個物件可以產生相同的雜湊程式碼。  
  
5.  選用：若要支援「大於」或「小於」的定義，請為型別實作 <xref:System.IComparable%601> 介面，並多載 [\<\=](../../../csharp/language-reference/operators/less-than-equal-operator.md) 和 [\>\=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) 運算子。  
  
 下列第一個範例顯示類別實作。  第二個範例則顯示結構實作。  
  
## 範例  
 下列範例會顯示如何在類別 \(參考型別\) 內實作實值相等。  
  
 [!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 在類別 \(參考型別\) 上，<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 方法的預設實作都是執行參考相等比較，而非實值相等檢查。  當實作器覆寫虛擬方法時，其目的是提供實值相等語意。  
  
 `==` 和 `!=` 運算子可以和類別搭配使用，不管類別有否多載它們。  不過，預設行為是執行參考相等檢查。  在類別中，如果您多載 `Equals` 方法，則也應該多載 `==` 和 `!=` 運算子，但這不是必要步驟。  
  
## 範例  
 下列範例顯示如何在結構 \(實值型別\) 內實作實值相等：  
  
 [!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 對於結構，<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 的預設實作 \(此為 <xref:System.ValueType?displayProperty=fullName> 中的受覆寫版本\) 會使用反映來比較型別中每個欄位的值，以便執行實值相等檢查。  當實作器覆寫結構中的虛擬 `Equals` 方法，其目的是要提供更有效的執行實值相等檢查方法，並可選擇根據結構之欄位或屬性的某個子集進行比較。  
  
 [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) 和 [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) 運算子不能在結構上操作，除非結構明確多載它們。  
  
## 請參閱  
 [相等比較](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)