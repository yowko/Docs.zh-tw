---
title: "物件初始設定式︰ 具名和匿名類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ObjectInitializer
dev_langs:
- VB
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
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
ms.openlocfilehash: d684ad4f3dd47dc7400ea401a94660af832ef866
ms.lasthandoff: 03/13/2017

---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>物件初始設定式：具名和匿名類型 (Visual Basic)
物件初始設定式可讓您使用單一運算式，指定複雜物件的屬性。 它們可以用來建立執行個體的具名型別，而匿名型別。  
  
## <a name="declarations"></a>宣告  
 具名和匿名型別的執行個體的宣告可以看起來幾乎相同，但其效果不相同。 每個類別都有能力和其本身的限制。 下列範例示範宣告和初始化具名類別的執行個體可方便`Customer`，使用物件初始設定式清單。 請注意類別的名稱會指定關鍵字之後`New`。  
  
 [!code-vb[VbVbalrObjectInit #&1;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 匿名型別已經沒有可用的名稱。 因此匿名型別的具現化不能包含類別名稱。  
  
 [!code-vb[VbVbalrObjectInit #&2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 需求和結果的兩個宣告都不相同。 如`namedCust`、`Customer`類別具有`Name`屬性必須存在，並宣告會建立該類別的執行個體。 如`anonymousCust`，編譯器會定義一個屬性，名為字串的新類別`Name`，並建立該類別的新執行個體。  
  
## <a name="named-types"></a>具名型別  
 物件初始設定式會提供簡單的方法呼叫的型別建構函式，然後設定在單一陳述式中的 部分或所有屬性的值。 編譯器會叫用適當的建構函式的陳述式︰ 預設建構函式如果不使用引數或如果會傳送一個或多個引數的參數化建構函式。 之後，會顯示在 初始設定式清單的順序會初始化所指定的屬性。  
  
 初始設定式清單中的每個初始設定包含指派初始值類別的成員。 在定義類別時，決定名稱和資料類型的成員。 在下列範例中，`Customer`類別必須存在，而且必須具有成員名稱為`Name`和`City`，可以接受的字串值。  
  
 [!code-vb[VbVbalrObjectInit #&3;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 或者，您可以使用下列程式碼取得相同的結果︰  
  
 [!code-vb[VbVbalrObjectInit #&4;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 這些宣告的每一個都是相當於下列的範例中，建立`Customer`物件使用預設建構函式，並接著指定的初始值`Name`和`City`屬性使用`With`陳述式。  
  
 [!code-vb[VbVbalrObjectInit #&5;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 如果`Customer`類別包含可讓您傳送的值中的參數化建構函式`Name`，比方說，也宣告及初始化`Customer`物件如下︰  
  
 [!code-vb[VbVbalrObjectInit #&6;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 您沒有初始化所有的屬性，如下列程式碼所示。  
  
 [!code-vb[VbVbalrObjectInit #&7;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 不過，初始設定清單不能空白。 未初始化的屬性會保留其預設值。  
  
### <a name="type-inference-with-named-types"></a>具名型別的型別推斷  
 您可以縮短的宣告的程式碼`cust1`結合物件初始設定式和區域型別推斷。 這樣您就可以省略`As`在變數宣告中的子句。 指派所建立的物件型別來推斷變數的資料型別。 在下列範例中，類型`cust6`是`Customer`。  
  
 [!code-vb[VbVbalrObjectInit #&8;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>具名型別的備註  
  
-   類別成員無法初始化物件初始設定式清單中一個以上的時間。 宣告`cust7`會導致錯誤。  
  
     [!code-vb[VbVbalrObjectInit #&9;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   成員可以用來初始化本身或其他欄位。 如果之前就已初始化，如下列宣告所示，存取成員`cust8`，將會使用預設值。 請記住，處理使用物件初始設定式的宣告時，發生第一件事，會叫用適當的建構函式。 之後，會初始化初始設定式清單中的個別欄位。 在下列範例中，預設值為`Name`指派給`cust8`，並已初始化的值會指派在`cust9`。  
  
     [!code-vb[VbVbalrObjectInit #&10;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     下列範例會使用參數化建構函式從`cust3`和`cust4`宣告並初始化`cust10`和`cust11`。  
  
     [!code-vb[VbVbalrObjectInit #&11;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   物件初始設定式可以是巢狀。 在下列範例中，`AddressClass`是類別，有兩個屬性，`City`和`State`，而`Customer`類別具有`Address`的執行個體的屬性`AddressClass`。  
  
     [!code-vb[VbVbalrObjectInit #&12;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   初始化清單不能空白。  
  
-   正在初始化的執行個體不能是型別物件。  
  
-   要初始化的類別成員不能共用的成員、 唯讀成員、 常數或方法呼叫。  
  
-   要初始化的類別成員無法編製索引，或限定。 下列範例會產生編譯器錯誤︰  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別會使用物件初始設定式來建立新您沒有明確定義的型別和名稱的執行個體。 相反地，編譯器會產生根據您指定的屬性的型別在物件初始設定式清單。 未指定型別的名稱，因為它指*匿名型別*。 例如，比較下列宣告為與前一個`cust6`。  
  
 [!code-vb[VbVbalrObjectInit #&13;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 唯一的差別在語法上是沒有指定任何名稱之後,`New`資料類型。 不過，會發生什麼事都相當不同。 編譯器會在定義新的匿名型別具有兩個屬性︰`Name`和`City`，並建立它的執行個體使用指定的值。 型別推斷的型別會決定`Name`和`City`在範例中是字串。  
  
> [!CAUTION]
>  匿名型別名稱由編譯器產生，而有所不同編譯。 您的程式碼不應該使用或依賴匿名型別的名稱。  
  
 因為沒有可用的型別名稱，您無法使用`As`子句來宣告`cust13`。 必須推斷其型別。 不使用晚期繫結，這會限制匿名型別的本機變數使用。  
  
 匿名型別提供的重要支援[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢。 匿名型別，在查詢中使用的相關資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)和[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
### <a name="remarks-about-anonymous-types"></a>匿名型別的備註  
  
-   一般來說，全部或大部分的匿名型別宣告中的屬性會是索引鍵屬性，以輸入關鍵字`Key`屬性名稱前面。  
  
     [!code-vb[VbVbalrObjectInit #&14;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     如需索引鍵屬性的詳細資訊，請參閱[金鑰](../../../../visual-basic/language-reference/modifiers/key.md)。  
  
-   例如名為型別初始設定式清單的匿名型別定義都必須宣告一個以上的屬性。  
  
     [!code-vb[VbVbalrObjectInit #&2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   匿名型別的執行個體宣告時，編譯器會產生相符的匿名型別定義。 名稱和資料類型的屬性取自於執行個體宣告和定義中，編譯器會包含。 屬性不是具名的事先定義的具名型別會是。 會推斷其型別。 您無法使用指定之屬性的資料型別`As`子句。  
  
-   匿名型別也可以建立的名稱和值的屬性其他幾種。 例如，匿名型別屬性可能需要的名稱和值的變數，或名稱，另一個物件的屬性值。  
  
     [!code-vb[VbVbalrObjectInit #&15;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     如需匿名型別中定義屬性選項的詳細資訊，請參閱[How to︰ 推斷屬性名稱和匿名型別宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [如何︰ 推斷屬性名稱和匿名型別宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [索引鍵](../../../../visual-basic/language-reference/modifiers/key.md)   
 [如何：使用物件初始設定式宣告物件](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
