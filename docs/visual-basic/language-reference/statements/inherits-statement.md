---
title: "Inherits Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Inherits"
  - "Inherits"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Inherits statement"
  - "Inherits statement, syntax"
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Inherits Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

讓目前的類別或介面繼承其他類別或介面集的屬性 \(Attribute\)、變數、屬性 \(Property\)、程序和事件。  
  
## 語法  
  
```  
Inherits basetypenames  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`basetypenames`|必要項。  衍生這個類別的類別名稱。<br /><br /> \-或\-<br /><br /> 衍生這個介面的來源介面名稱。  請使用逗號隔開多個名稱。|  
  
## 備註  
 如果使用的話，則 `Inherits` 陳述式必須是類別或介面定義中非空白且非註解的第一行。  它應該跟隨在 `Class` 或 `Interface` 陳述式之後。  
  
 只可在類別或介面中使用 `Inherits`。  這表示繼承 \(Inheritance\) 的宣告內容不可以是原始程式檔 \(Source File\)、命名空間 \(Namespace\)、結構、模組、程序或區塊。  
  
## 規則  
  
-   **類別繼承** 如果類別使用 `Inherits` 陳述式，則只可以指定一個基底類別。  
  
     類別無法繼承自在其中形成巢狀的類別。  
  
-   **介面繼承** 如果介面使用 `Inherits` 陳述式，則可以指定一個或多個基底介面。  即使兩個介面每個都定義同名的成員，也可以繼承這兩個介面。  如果這樣做，則實作程式碼必須使用名稱限定，以指定它所實作的成員。  
  
     介面無法繼承另一個具有較受限存取層級的介面。  例如，`Public` 介面無法繼承 `Friend` 介面。  
  
     介面無法繼承自內部的巢狀介面。  
  
 .NET Framework 中的類別繼承範例是 <xref:System.ArgumentException> 類別，它繼承 <xref:System.SystemException> 類別。  這會將系統例外狀況 \(Exception\) 所需的所有預先定義的屬性和程序提供給 <xref:System.ArgumentException> \(例如 <xref:System.Exception.Message%2A> 屬性和 <xref:System.Exception.ToString%2A> 方法\)。  
  
 .NET Framework 中的介面繼承範例是 <xref:System.Collections.ICollection> 介面，它繼承 <xref:System.Collections.IEnumerable> 介面。  這會讓 <xref:System.Collections.ICollection> 繼承周遊集合所需的列舉值定義。  
  
## 範例  
 下列範例會使用 `Inherits` 陳述式顯示名為 `thisClass` 的類別如何繼承名為 `anotherClass` 之基底類別的所有成員。  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## 範例  
 下列範例會顯示多個介面的繼承。  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 名為 `thisInterface` 的介面現在包含 <xref:System.IComparable>、<xref:System.IDisposable> 和 <xref:System.IFormattable> 介面中的所有定義。繼承的成員分別提供兩個物件的型別特有比較、釋放所配置的資源，以及以 `String` 表示物件的值。  實作 `thisInterface` 的類別必須實作每個基底介面的每個成員。  
  
## 請參閱  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)