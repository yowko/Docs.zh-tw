---
title: 匿名類型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 530e21e1595f9bbc3436280418287413e2a48111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-types-visual-basic"></a>匿名類型 (Visual Basic)
Visual Basic 支援可讓您建立的物件，而不需要撰寫的資料類型的類別定義的匿名型別。 編譯器 (Compiler) 會自動幫您建立類別 (Class)。 類別沒有可用的名稱，直接繼承自<xref:System.Object>，且包含您指定在宣告物件的屬性。 未指定資料類型的名稱，因為它指*匿名型別*。  
  
 下列範例會宣告並建立變數`product`做為具有兩個屬性的匿名型別的執行個體`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 A*查詢運算式*會使用匿名型別結合資料查詢選取的資料行。 由於您無法預測特定的查詢會選取的資料行，您無法事先定義的結果類型。 匿名類型可讓您撰寫依任何順序選取任意數目的資料行的查詢。 編譯器會建立比對指定的屬性和指定的順序的資料類型。  
  
 在下列範例中，`products`是一份產品物件每一個都有許多屬性。 變數`namePriceQuery`儲存傳回的查詢，當它執行時，具有兩個屬性的匿名型別的執行個體的集合定義`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 變數`nameQuantityQuery`儲存傳回的查詢，當它執行時，具有兩個屬性的匿名型別的執行個體的集合定義`Name`和`OnHand`。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 如需匿名型別為編譯器所建立的程式碼的詳細資訊，請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
> [!CAUTION]
>  匿名類型的名稱是編譯器產生，而可能有所不同編譯。 您的程式碼不應該使用或依賴匿名型別的名稱，因為重新編譯專案時，可能會變更名稱。  
  
## <a name="declaring-an-anonymous-type"></a>宣告匿名類型  
 匿名型別的執行個體的宣告會使用初始設定式清單來指定類型的屬性。 當您宣告匿名類型、 不例如方法或事件其他類別項目時，您可以指定只有屬性。 在下列範例中，`product1`是有兩個屬性的匿名類型的執行個體：`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 如果您指定屬性為索引鍵屬性時，您可以使用它們來比較兩個匿名型別執行個體相等。 不過，您無法變更索引鍵屬性的值。 請參閱本文稍後如需詳細資訊的索引鍵屬性 > 一節。  
  
 請注意，宣告匿名類型的執行個體是使用物件初始設定式宣告具名類型的執行個體：  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 如需指定匿名類型屬性的其他方式的詳細資訊，請參閱[How to： 推斷屬性名稱和匿名類型宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## <a name="key-properties"></a>索引鍵內容  
 數種基本方式，與非索引鍵屬性不同索引鍵屬性：  
  
-   只有索引鍵屬性的值會比較以判斷兩個執行個體是否相等。  
  
-   索引鍵屬性的值是唯讀而且無法變更。  
  
-   只有索引鍵屬性值包含編譯器產生的雜湊程式碼演算法，如匿名型別。  
  
### <a name="equality"></a>相等  
 匿名類型的執行個體可以有相同的匿名型別的執行個體才會相等。 編譯器會將兩個執行個體與相同類型的執行個體，若符合下列條件：  
  
-   宣告相同的組件。  
  
-   其屬性具有相同的名稱相同的推斷型別，並宣告以相同的順序。 名稱比較不區分大小寫。  
  
-   在每個相同的屬性標記為索引鍵屬性。  
  
-   每個宣告中的至少一個屬性是索引鍵內容。  
  
 匿名型別沒有索引鍵屬性的執行個體等於只有本身。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 相同匿名類型的兩個執行個體相等的索引鍵屬性的值是否相等。 下列範例說明如何測試相等。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a>唯讀的值  
 無法變更索引鍵屬性的值。 例如，在`prod8`在前一個範例中，`Name`和`Price`欄位`read-only`，但`OnHand`可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a>從查詢運算式的匿名型別  
 查詢運算式不一定需要建立匿名型別。 如果可能的話，他們會使用現有的類型來保存資料行的資料。 會發生這種情況是當查詢傳回整筆記錄，從資料來源或只有一個欄位，從每個記錄。 下列程式碼範例中，`customers`是物件的集合`Customer`類別。 類別具有許多屬性，而且您可以在查詢結果中，依任何順序包含一或多個。 在前兩個範例中，沒有匿名型別是必要的因為查詢選取的具名類型的項目：  
  
-   `custs1`包含字串的集合，因為`cust.Name`是字串。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2`包含集合`Customer`物件，因為每個項目`customers`是`Customer`查詢所選取物件，且整個項目。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 不過，適當具名型別並非永遠可用。 您可以選取 客戶名稱和一個用途、 客戶 ID 編號和另一個位置的位址和客戶名稱、 位址，以及協力廠商的訂單記錄。 匿名類型可讓您以任何順序選取屬性的任何組合，而第一個宣告新的具名的類型，以保存結果。 相反地，編譯器會建立每次編譯屬性的匿名型別。 下列查詢會選取只在客戶的名稱和 ID 編號從每個`Customer`物件存放至`customers`。 因此，編譯器會建立包含只有這兩個屬性的匿名型別。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 名稱和資料類型的匿名型別中的屬性都取自的引數`Select`，`cust.Name`和`cust.ID`。 匿名型別所建立的查詢中的屬性一定是索引鍵屬性。 當`custs3`執行下列`For Each`迴圈，結果是具有兩個屬性的匿名類型的執行個體的集合`Name`和`ID`。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 所表示的集合中的項目`custs3`強型別，並瀏覽可用的屬性，並確認其類型，您可以使用 IntelliSense。  
  
 如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>決定是否要使用匿名型別  
 當做匿名類別的執行個體建立物件之前，請考慮那是否最佳選項。 例如，如果您想要建立暫存物件來包含相關的資料，而且您不需要其他的欄位和方法，其中可能包含完整的類別，匿名型別會是很好的解決方案。 匿名類型也會很方便的如果您想要每個宣告中，選取不同的屬性，或您想要變更屬性的順序。 不過，如果您的專案包含數個物件具有相同的屬性，以固定的順序，您可以宣告它們更輕鬆地使用具名型別類別建構函式。 比方說，使用適當的建構函式，它是宣告數個執行個體的工作變得更容易`Product`類別比宣告匿名類型的數個執行個體。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 具名類型的另一個好處是，編譯器可以攔截的屬性名稱不小心輸入錯誤。 在上一個範例中， `firstProd2`， `secondProd2`，和`thirdProd2`要作為相同匿名類型的執行個體。 不過，如果您不小心將宣告`thirdProd2`中的下列方法之一，其類型會是不同的`firstProd2`和`secondProd2`。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 更重要的是，有一些限制並不適用於具名類型的執行個體的匿名型別的使用。 `firstProd2``secondProd2`，和`thirdProd2`是相同的匿名類型的執行個體。 不過，共用的匿名類型的名稱無法使用，不能出現在程式碼中預期的型別名稱的位置。 例如，匿名類型無法用來定義方法簽章，若要宣告另一個變數或欄位，或任何類型宣告中。 如此一來，匿名型別時，不適合您需要在方法之間共用資訊。  
  
## <a name="an-anonymous-type-definition"></a>匿名類型定義  
 為了回應執行個體的匿名類型宣告，編譯器會建立新的類別定義，其中包含指定的屬性。  
  
 如果匿名型別包含至少一個索引鍵屬性，定義會覆寫繼承自的三個成員<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 程式碼產生的測試相等，以及判斷雜湊碼值會考慮索引鍵的屬性。 如果匿名型別包含任何索引鍵屬性，只有<xref:System.Object.ToString%2A>會覆寫。 明確命名的匿名類型屬性不能與這些產生的方法衝突。 也就是說，您無法使用`.Equals`， `.GetHashCode`，或`.ToString`命名屬性。  
  
 匿名類型定義，至少有一個索引鍵屬性也實作<xref:System.IEquatable%601?displayProperty=nameWithType>介面，其中`T`是匿名類型的類型。  
  
 如需建立由編譯器和功能的覆寫方法的程式碼的詳細資訊，請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
## <a name="see-also"></a>另請參閱  
 [物件初始設定式：具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [匿名類型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)
