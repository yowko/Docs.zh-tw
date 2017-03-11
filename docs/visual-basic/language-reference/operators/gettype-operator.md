---
title: "GetType Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.GetType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetType operator"
  - "GetType keyword"
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# GetType Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

傳回指定型別的 <xref:System.Type> 物件。  <xref:System.Type> 物件會提供型別的相關資訊，例如其屬性、方法和事件。  
  
## 語法  
  
```  
GetType(typename)  
```  
  
#### 參數  
  
|||  
|-|-|  
|參數|描述|  
|`typename`|您需要資訊的型別名稱。|  
  
## 備註  
 `GetType` 運算子會為指定的 `typename` 傳回 <xref:System.Type> 物件。  您可在 `typename` 中傳遞任何已定義型別的名稱。  包括下列項目：  
  
-   任何 Visual Basic 資料型別，例如 `Boolean` 或 `Date`。  
  
-   任何 .NET Framework 類別、結構、模組或介面，例如 <xref:System.ArgumentException?displayProperty=fullName> 或 <xref:System.Double?displayProperty=fullName>。  
  
-   應用程式所定義的任何類別、結構、模組或介面。  
  
-   應用程式所定義的任何陣列。  
  
-   應用程式所定義的任何委派。  
  
-   Visual Basic、.NET Framework 或應用程式所定義的任何列舉型別。  
  
 如果您想要取得物件變數的型別物件，請使用 <xref:System.Type.GetType%2A?displayProperty=fullName> 方法。  
  
 在下列情況下，`GetType` 運算子十分有用：  
  
-   必須在執行階段存取型別的中繼資料。  <xref:System.Type> 物件提供中繼資料，例如型別成員和部署資訊。  例如，您需要有此中繼資料才可透過組件進行反映。  如需詳細資訊，請參閱 <xref:System.Reflection?displayProperty=fullName>。  
  
-   想要比較兩個物件參考，以查看它們是否參考相同型別的執行個體。  如果是，則 `GetType` 會傳回該相同 <xref:System.Type> 物件的參考。  
  
## 範例  
 下列範例將說明 `GetType` 運算子的用法。  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/gettype-operator_1.vb)]  
  
## 請參閱  
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)