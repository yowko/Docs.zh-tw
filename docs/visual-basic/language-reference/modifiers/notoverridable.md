---
title: "NotOverridable (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.NotOverridable"
  - "NotOverridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "sealed methods"
  - "NotOverridable keyword"
  - "properties [Visual Basic], redefining"
  - "elements, sealed"
  - "sealed elements"
  - "procedures, overriding"
  - "procedures, redefining"
  - "overriding"
  - "methods [Visual Basic], sealed"
  - "properties [Visual Basic], overriding"
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# NotOverridable (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定屬性 \(Property\) 或程序在衍生類別中不可覆寫。  
  
## 備註  
 `NotOverridable`修飾詞可防止屬性或方法在衍生類別中覆寫。  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)修飾詞讓衍生類別中覆寫類別中的屬性或方法。  如需詳細資訊，請參閱 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果`Overridable`或`NotOverridable`修飾詞不指定，則預設設定，取決於是否屬性或方法會覆寫基底類別的屬性或方法。  如果該屬性或方法覆寫基底類別的屬性或方法，預設值會是`Overridable`。 否則，它就是`NotOverridable`。  
  
 無法覆寫的項目有時稱為「*密封*」項目。  
  
 只有在屬性或程序宣告陳述式 \(Declaration Statement\) 中，才能使用 `NotOverridable`。  只可在覆寫另一個屬性或程序的屬性或程序上指定 `NotOverridable`，也就是說，只有在與 `Overrides` 一起使用時才可以。  
  
## 組合的修飾詞  
 您不能指定`Overridable`或`NotOverridable`的`Private`方法。  
  
 您無法在同一個宣告中同時指定 `NotOverridable` 與 `MustOverride`、`Overridable` 或 `Shared`。  
  
## 使用方式  
 `NotOverridable` 修飾詞可用於以下內容中：  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [Modifiers](../../../visual-basic/language-reference/modifiers/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)