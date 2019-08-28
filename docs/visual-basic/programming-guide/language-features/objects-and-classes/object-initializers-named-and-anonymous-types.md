---
title: 物件初始設定式：命名和匿名型別 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: e1f461cc98fb104f78a6c83a207cff7f4eda9227
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046456"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>物件初始設定式：命名和匿名型別 (Visual Basic)
物件初始化運算式可讓您使用單一運算式來指定複雜物件的屬性。 它們可以用來建立命名類型和匿名型別的實例。  
  
## <a name="declarations"></a>宣告  
 已命名和匿名型別的實例宣告看起來幾乎完全相同, 但其效果並不相同。 每個類別都有自己的能力和限制。 下列範例顯示使用物件初始化運算式清單來宣告和初始化命名類別`Customer`之實例的便利方式。 請注意, 類別的名稱是在關鍵字`New`之後指定。  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 匿名型別沒有可用的名稱。 因此, 匿名型別的具現化不能包含類別名稱。  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 這兩個宣告的需求和結果不同。 若`namedCust`為,具有`Name`屬性的類別必須已經存在,而且宣告會建立該類別的實例。`Customer` 針對`anonymousCust`, 編譯器會定義具有一個屬性的新類別、名`Name`為的字串, 並建立該類別的新實例。  
  
## <a name="named-types"></a>命名類型  
 物件初始化運算式提供簡單的方法來呼叫類型的函式, 然後在單一語句中設定部分或所有屬性的值。 編譯器會針對語句叫用適當的函式: 如果沒有提供任何引數, 則為無參數的函式, 或如果傳送了一或多個引數, 則為參數化的函數 之後, 指定的屬性會依照它們在初始化運算式清單中的顯示順序來初始化。  
  
 初始化運算式清單中的每個初始設定都包含將初始值指派給類別的成員。 定義類別時, 會決定成員的名稱和資料類型。 在下列範例中, `Customer`類別必須存在, 而且必須具有名為`Name`且`City`可接受字串值的成員。  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 或者, 您可以使用下列程式碼來取得相同的結果:  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 這些宣告中的每一個都相當於下列範例, 其會`Customer`使用無參數的函式來建立物件, 然後使用`With`來指定`Name`和`City`屬性的初始值句.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 例如, 如果`Name` `Customer`類別包含參數化的函式, 可讓您傳送的值, 您也可以透過下列方式來宣告和初始化物件: `Customer`  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 您不需要初始化所有屬性, 如下列程式碼所示。  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 不過, 初始化清單不可以是空的。 未初始化的屬性會保留其預設值。  
  
### <a name="type-inference-with-named-types"></a>具有命名類型的類型推斷  
 您可以藉`cust1`由結合物件初始化運算式和區欄位型別推斷, 縮短宣告的程式碼。 這可讓您省略變數`As`宣告中的子句。 變數的資料類型是從指派所建立的物件類型推斷而來。 在下列範例中, 的類型`cust6`是。 `Customer`  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>命名類型的相關備註  
  
- 類別成員在物件初始化運算式清單中無法初始化一次以上。 的宣告會造成錯誤。 `cust7`  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- 成員可以用來初始化本身或其他欄位。 如果成員在初始化之前被存取 (如的下列`cust8`宣告所示), 則會使用預設值。 請記住, 當處理使用物件初始化運算式的宣告時, 第一件事就是叫用適當的函式。 之後, 初始化運算式清單中的個別欄位便會進行初始化。 在下列範例中, `Name`會為`cust8`指派的預設值, 並在中`cust9`指派初始化的值。  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     下列範例會`cust3`從和`cust4`使用參數化的函式, 以宣告`cust11`和初始化`cust10`和。  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- 物件初始化運算式可以嵌套。 在下列範例中, `AddressClass`是具有兩個屬性 ( `City`和`State`) 的類別, 而`Customer`類別具有`Address`屬於實例的`AddressClass`屬性。  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- 初始化清單不可以是空的。  
  
- 要初始化的實例不可以是 Object 類型。  
  
- 要初始化的類別成員不能是共用成員、唯讀成員、常數或方法呼叫。  
  
- 無法為已初始化的類別成員編制索引或限定。 下列範例會引發編譯器錯誤:  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別會使用物件初始化運算式, 來建立您未明確定義和命名的新類型實例。 相反地, 編譯器會根據您在物件初始化運算式清單中指定的屬性來產生型別。 因為未指定類型的名稱, 所以稱為*匿名型別*。 例如, 比較的下列宣告與先前`cust6`的宣告。  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 唯一的不同之處在于, 在資料類型之後`New`未指定任何名稱。 不過, 這種情況會有很大的差異。 編譯器會定義具有兩個屬性 ( `Name`和`City`) 的新匿名型別, 並使用指定的值建立它的實例。 型別推斷會將範例`Name`中`City`的和類型判斷為字串。  
  
> [!CAUTION]
> 匿名型別的名稱是由編譯器所產生, 而且可能會因編譯而異。 您的程式碼不應該使用或依賴匿名型別的名稱。  
  
 因為類型的名稱無法使用, 所以您不能使用`As`子句`cust13`來宣告。 必須推斷其型別。 如果沒有使用晚期繫結, 這會限制使用匿名型別來做為本機變數。  
  
 匿名型別提供查詢的[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]關鍵支援。 如需在查詢中使用匿名型別的詳細資訊, 請參閱[匿名](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)型別和 Visual Basic 中的[LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
### <a name="remarks-about-anonymous-types"></a>匿名型別的相關備註  
  
- 一般來說, 匿名型別宣告中的所有或大部分屬性都是索引鍵屬性, 這是藉由在屬性名稱`Key`前面輸入關鍵字來表示。  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     如需索引鍵屬性的詳細資訊, 請參閱索引[鍵](../../../../visual-basic/language-reference/modifiers/key.md)。  
  
- 就像命名類型, 匿名型別定義的初始化運算式清單必須宣告至少一個屬性。  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- 宣告匿名型別的實例時, 編譯器會產生相符的匿名型別定義。 屬性的名稱和資料類型取自實例宣告, 並由編譯器在定義中包含。 屬性不會事先命名並定義, 就像是針對已命名的型別一樣。 系統會推斷其類型。 您不能使用`As`子句來指定屬性的資料類型。  
  
- 匿名型別也可以用數種其他方式來建立其屬性的名稱和值。 例如, 匿名型別屬性可以同時接受變數的名稱和值, 或是另一個物件之屬性的名稱和值。  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     如需有關在匿名型別中定義屬性之選項的詳細[資訊, 請參閱如何:在匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)宣告中推斷屬性名稱和類型。  
  
## <a name="see-also"></a>另請參閱

- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [如何：在匿名型別宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
- [如何：使用物件初始化運算式宣告物件](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
