---
title: "多載屬性和方法 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names, multiple procedures with same
- procedures, mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword, overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6f379f04ca9b75161baf2bf2c33e87f05a9edf97
ms.lasthandoff: 03/13/2017

---
# <a name="overloaded-properties-and-methods-visual-basic"></a>多載屬性和方法 (Visual Basic)
多載會建立多個程序、 執行個體建構函式或具有相同名稱但不同引數型別類別中的屬性。  
  
## <a name="overloading-usage"></a>使用多載化  
 當您採用不同的資料型別上作業的程序的相同名稱的物件模型規定時，多載會特別有用。 比方說，可以顯示數個不同的資料類型的類別可能會有`Display`看起來像這樣的程序︰  
  
 [!code-vb[VbVbalrOOP #&64;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 沒有多載化，您必須建立不同的名稱，每個程序，即使它們是一樣，一步所示︰  
  
 [!code-vb[VbVbalrOOP #&65;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 多載可讓您更輕鬆地使用屬性或方法，因為它提供了可用的資料類型的選擇。 例如，多載`Display`所討論的方法之前可以呼叫任何下列程式碼行︰  
  
 [!code-vb[VbVbalrOOP #&66;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 在執行階段，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼叫正確的程序根據資料型別參數的您所指定。  
  
## <a name="overloading-rules"></a>多載規則  
 您可以新增兩個或多個屬性或方法具有相同名稱建立多載類別成員。 除了多載衍生的成員，每個多載的成員必須具有不同的參數清單和多載屬性或程序時，不做為區別功能使用下列項目︰  
  
-   修飾詞，例如`ByVal`或`ByRef`，套用到成員或成員的參數。  
  
-   參數的名稱  
  
-   程序的傳回型別  
  
 `Overloads`多載時，關鍵字是選擇性，但如果有多載成員會使用`Overloads`關鍵字，則其他所有多載的成員具有相同名稱也必須指定這個關鍵字。  
  
 在衍生的類別可以多載具有相同參數和參數型別，這道程序的繼承的成員*名稱和簽章，以遮蔽*。 如果`Overloads`關鍵字，以遮蔽名稱和簽章，衍生的類別實作的成員將用於而不是基底類別中實作及使用該成員的所有多載可供衍生類別的執行個體。  
  
 如果`Overloads`多載化繼承的成員具有相同參數和參數類型的成員時省略關鍵字，則多載會呼叫*以名稱遮蔽*。 以名稱遮蔽取代繼承的成員，實作，它會使其他所有多載無法在衍生的類別和及其子系的執行個體。  
  
 `Overloads`和`Shadows`修飾詞都不可與相同的屬性或方法。  
  
### <a name="example"></a>範例  
 下列範例會建立多載的方法可接受 `String`或`Decimal`金額和傳回包含營業稅的字串表示。  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a>若要使用此範例建立一個多載的方法  
  
1.  開啟新專案，並新增名為`TaxClass`。  
  
2.  將下列程式碼加入 `TaxClass` 類別。  
  
     [!code-vb[VbVbalrOOP #&67;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  將下列程序加入至表單。  
  
     [!code-vb[VbVbalrOOP #&68;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  將按鈕加入至您的表單，並呼叫`ShowTax`程序從`Button1_Click`按鈕的事件。  
  
5.  執行專案，然後按一下 若要測試的多載表單上的按鈕`ShowTax`程序。  
  
 在執行階段，編譯器會選擇適當的多載函式所使用的參數相符。 當您按一下按鈕時，使用第一次呼叫多載的方法`Price`參數是字串和訊息，「 價格會是一個字串。 稅率為 $5.12 」 顯示。 `TaxAmount`使用呼叫`Decimal`值第二次和訊息，「 價格是十進位。 稅率為 $5.12 」 顯示。  
  
## <a name="see-also"></a>另請參閱  
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [在 Visual Basic 中，以遮蔽](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Sub 陳述式](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [繼承基本概念](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [陰影](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
