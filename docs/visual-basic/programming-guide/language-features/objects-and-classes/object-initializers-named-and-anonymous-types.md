---
title: 物件初始設定式：具名和匿名類型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 349e4f7b4902eb18845fee7cb4d01b217849a4d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>物件初始設定式：具名和匿名類型 (Visual Basic)
物件初始設定式可讓您使用單一運算式指定的複雜物件的屬性。 它們可以用來建立匿名型別和具名類型的執行個體。  
  
## <a name="declarations"></a>宣告  
 執行個體的具名和匿名類型宣告可以看起來幾乎完全相同，但其效果不相同。 每個分類都會有能力以及其本身的限制。 下列範例示範便利的方式，來宣告和初始化具名類別的執行個體`Customer`，使用物件初始設定式清單。 請注意類別的名稱會指定關鍵字之後`New`。  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 匿名型別已沒有可用的名稱。 因此匿名類型的具現化不能包含的類別名稱。  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 需求和兩個宣告的結果都不相同。 如`namedCust`、`Customer`類別具有`Name`屬性必須存在，並宣告建立該類別的執行個體。 如`anonymousCust`，編譯器會定義新的類別具有一個屬性，一個字串稱為`Name`，並建立該類別的新執行個體。  
  
## <a name="named-types"></a>具名的類型  
 物件初始設定式會提供簡單的方式來呼叫類型的建構函式，並在單一陳述式將部分或所有屬性的值。 編譯器會叫用適當的建構函式的陳述式： 預設建構函式如果任何引數會不呈現或如果會傳送一個或多個引數的參數化建構函式。 在這之後，指定的屬性會初始化初始設定式清單中出現的順序。  
  
 初始設定式清單中的每個初始設定包含初始值指派至類別的成員。 名稱和資料類型的成員會在類別定義時決定。 在下列範例中，`Customer`類別必須存在，且必須有成員具名`Name`和`City`，可以接受的字串值。  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 或者，您也可以使用下列程式碼來取得相同的結果：  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 每個這些宣告就相當於下列的範例中，建立`Customer`使用預設建構函式物件，然後再指定初始值`Name`和`City`屬性使用`With`陳述式。  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 如果`Customer`類別包含可讓您傳送的值中的參數化建構函式`Name`，比方說，您可以也宣告和初始化`Customer`物件如下：  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 您沒有初始化所有的屬性，如下列程式碼所示。  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 不過，在初始設定清單不能空白。 未初始化的屬性會保留其預設值。  
  
### <a name="type-inference-with-named-types"></a>具名類型的類型推斷  
 您可以縮短的程式碼的宣告`cust1`結合物件初始設定式和區域類型推斷。 這可讓您省略`As`在變數宣告中的子句。 變數的資料型別會從指派所建立的物件型別推斷。 在下列範例中，類型`cust6`是`Customer`。  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>具名型別的備註  
  
-   類別成員無法初始化物件初始設定式清單中一個以上的時間。 宣告`cust7`會造成錯誤。  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   成員可以用來初始化本身或另一個欄位。 如果它已初始化以前，如下列宣告所示，存取成員`cust8`，將會使用預設值。 請記住，使用物件初始設定式的宣告處理時，會發生第一件事是適當的建構函式會叫用。 在這之後，會初始化初始設定式清單中的個別欄位。 在下列範例中，預設值為`Name`指派給`cust8`，並初始化的值指派中`cust9`。  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     下列範例會使用參數化建構函式從`cust3`和`cust4`來宣告和初始化`cust10`和`cust11`。  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   物件初始設定式可以是巢狀。 在下列範例中，`AddressClass`有兩個屬性，是類別`City`和`State`，而`Customer`類別具有`Address`的執行個體的屬性`AddressClass`。  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   在初始設定清單不能空白。  
  
-   正在初始化的執行個體不能屬於類型物件。  
  
-   正在初始化的類別成員不能共用的成員、 唯讀成員、 常數或方法呼叫。  
  
-   要初始化的類別成員無法編製索引，或限定。 下列範例會產生編譯器錯誤：  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別會使用物件初始設定式來建立您未明確定義的新類型和名稱的執行個體。 相反地，編譯器會產生根據您指定的屬性型別在物件初始設定式清單。 未指定類型的名稱，因為它指*匿名型別*。 例如，比較下列宣告與先前針對`cust6`。  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 唯一的差別語法是，未指定名稱後`New`資料類型。 不過，會發生什麼事是相當不同。 編譯器會定義新的匿名類型有兩個屬性，`Name`和`City`，並建立它的執行個體和指定的值。 類型推斷可決定類型的`Name`和`City`在範例中是字串。  
  
> [!CAUTION]
>  匿名類型的名稱由編譯器產生，而可能有所不同編譯。 您的程式碼不應該使用或依賴匿名型別的名稱。  
  
 因為無法使用型別的名稱，您無法使用`As`子句來宣告`cust13`。 必須推斷其類型。 不使用晚期繫結，這會限制使用給本機變數的匿名型別。  
  
 匿名型別提供重大支援[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。 匿名型別，在查詢中使用的相關資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)和[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
### <a name="remarks-about-anonymous-types"></a>匿名型別的備註  
  
-   一般來說，所有或大部分為匿名型別宣告中的屬性會是索引鍵屬性，由輸入關鍵字指示`Key`屬性名稱前面。  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     如需索引鍵屬性的詳細資訊，請參閱[金鑰](../../../../visual-basic/language-reference/modifiers/key.md)。  
  
-   Like 名為型別，初始設定式清單的匿名類型定義必須宣告至少一個屬性。  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   宣告匿名類型的執行個體時，編譯器會產生相符的匿名型別定義。 名稱和資料類型的屬性會從執行個體宣告中，擷取，而且會包含編譯器在定義中。 屬性不是名為，而且如具名型別，其方式是事先定義。 會推斷其類型。 您無法使用，以指定屬性的資料型別`As`子句。  
  
-   匿名類型也可以建立的名稱和其屬性的值中其他幾種方法。 例如，匿名類型屬性可能需要同時以名稱和變數，或名稱的值與另一個物件的屬性值。  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     如需匿名型別中定義屬性選項的詳細資訊，請參閱[How to： 推斷屬性名稱和匿名類型宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## <a name="see-also"></a>另請參閱  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)  
 [如何：使用物件初始設定式宣告物件](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
