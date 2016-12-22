---
title: "Overloaded Properties and Methods (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "properties [Visual Basic], overloading"
  - "methods [Visual Basic], overloading"
  - "shadowing"
  - "names, multiple procedures with same"
  - "procedures, mulltiples with same name"
  - "classes [Visual Basic], properties"
  - "classes [Visual Basic], methods"
  - "method overloading"
  - "Overloads keyword, overloaded members"
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Overloaded Properties and Methods (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

多載化 \(Overloading\) 是建立具有相同名稱但不同引數型別的多個程序、執行個體建構函式或類別屬性。  
  
## 多載化使用方式  
 當物件模型規定您針對在不同資料型別上作業的程序採用相似的名稱時，多載化就特別有用。  例如，可顯示數種不同資料型別的類別，可具有類似於下列範例的 `Display` 程序：  
  
 [!code-vb[VbVbalrOOP#64](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 在不使用多載化的情況下，即使程序執行相同的作業，您也必須為每個程序建立不同的名稱，如下列範例所示：  
  
 [!code-vb[VbVbalrOOP#65](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 因為多載化提供可使用的資料型別的選擇，所以能夠更容易地使用屬性或方法。  例如，下列任何一行程式碼都可呼叫先前所討論的 `Display` 方法：  
  
 [!code-vb[VbVbalrOOP#66](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 在執行階段，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會依據您指定的參數資料型別來呼叫正確的程序。  
  
## 多載化規則  
 您以加入二或多個相同名稱的屬性或方法的方式為類別建立多載成員。  除了多載衍生成員外，每個多載成員都必須具有不同的參數清單；而在多載化屬性或程序時，無法將下列項目當做差異功能使用：  
  
-   套用至成員或成員參數的修飾詞，例如 `ByVal` 或 `ByRef`。  
  
-   參數名稱  
  
-   程序的傳回型別  
  
 多載化時，您可以選擇是否使用 `Overloads` 關鍵字，但是如果任何多載成員使用了 `Overloads` 關鍵字，那麼其他所有相同名稱的多載成員也必須指定此關鍵字。  
  
 衍生類別 \(Derived Class\) 會使用具有相同參數和參數型別的成員，來多載受繼承的成員，此程序稱為「*以名稱和簽章遮蔽*」\(Shadowing by Name and Signature\)。  如果在名稱和簽章被遮蔽時使用 `Overloads` 關鍵字，將使用成員的衍生類別實作，來取代基底類別的實作，衍生類別的執行個體將可使用該成員的其他多載。  
  
 如果使用具有相同參數和參數型別的成員，來多載化繼承的成員時，則會省略 `Overloads` 關鍵字，這種多載化稱為「*以名稱遮蔽*」\(Shadowing by Name\)。  以名稱遮蔽會取代成員的繼承實作，且衍生類別的執行個體及其子系，會無法使用其他多載。  
  
 `Overloads` 和 `Shadows` 修飾詞無法用於相同名稱的屬性或方法。  
  
### 範例  
 下列範例所建立的多載方法，可接受表示金額的 `String` 或 `Decimal`，並傳回包含營業稅的字串。  
  
##### 若要使用這個範例來建立多載方法  
  
1.  開啟新專案並加入名為 `TaxClass` 的類別。  
  
2.  將下列程式碼加入至 `TaxClass` 類別。  
  
     [!code-vb[VbVbalrOOP#67](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  將下列程序加入至表單。  
  
     [!code-vb[VbVbalrOOP#68](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  將按鈕加入至表單，並從按鈕的 `Button1_Click` 事件來呼叫 `ShowTax` 程序。  
  
5.  執行專案並按一下表單上的按鈕，以測試多載 `ShowTax` 程序。  
  
 在 Run Time 時，編譯器 \(Compiler\) 會選擇符合所使用參數的適當多載函式。  當您按一下按鈕時，會先使用字串參數 `Price` 來呼叫多載方法，並顯示訊息 "Price is a String .  Tax is $5.12"。  第二次則使用 `Decimal` 值來呼叫 `TaxAmount`，顯示的訊息是 "Price is a Decimal.  Tax is $5.12"。  
  
## 請參閱  
 [Objects and Classes](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)