---
title: 匿名類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: ef48ff1bbf79be981b8b8d4148f818fe40b72353
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64632176"
---
# <a name="anonymous-types-visual-basic"></a>匿名類型 (Visual Basic)
Visual Basic 支援可讓您建立物件，而不需要撰寫的資料類型的類別定義的匿名型別。 編譯器 (Compiler) 會自動幫您建立類別 (Class)。 類別沒有可使用的名稱、 直接繼承自<xref:System.Object>，並包含您指定在宣告物件的屬性。 未指定資料類型的名稱，因為它指*匿名型別*。  
  
 下列範例會宣告並建立變數`product`有兩個屬性，匿名型別的執行個體形式`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 A*查詢運算式*會使用匿名型別結合的查詢所選取的資料行。 由於您無法預測特定的查詢可能選取的資料行，您無法事先定義的結果類型。 匿名型別可讓您撰寫的查詢，以任何順序選取任意數目的資料行。 編譯器會建立比對指定的屬性和指定的順序的資料類型。  
  
 在下列範例中，`products`是一份 product 物件，每個都有許多屬性。 變數`namePriceQuery`傳回的查詢，當它執行時，有兩個屬性，匿名型別的執行個體集合的定義會保留`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 變數`nameQuantityQuery`傳回的查詢，當它執行時，有兩個屬性，匿名型別的執行個體集合的定義會保留`Name`和`OnHand`。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 如需有關建立匿名型別，編譯器的程式碼的詳細資訊，請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
> [!CAUTION]
>  匿名類型的名稱是編譯器產生，而且可能會有所不同的編譯。 您的程式碼不應該使用或依賴匿名型別的名稱，因為重新編譯專案時，可能會變更的名稱。  
  
## <a name="declaring-an-anonymous-type"></a>宣告匿名型別  
 匿名型別的執行個體的宣告會使用初始設定式清單來指定類型的屬性。 當您宣告匿名型別，不方法或事件等其他類別項目時，您可以指定只有屬性。 在下列範例中，`product1`有兩個屬性的匿名類型的執行個體：`Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 如果您指定屬性為索引鍵屬性時，您可以使用它們來比較兩個匿名型別執行個體相等。 不過，您無法變更索引鍵屬性的值。 請參閱本章稍後如需詳細資訊的索引鍵屬性 區段。  
  
 請注意，宣告匿名類型的執行個體是使用物件初始設定式宣告的具名型別執行個體：  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 如需指定匿名型別屬性的其他方式的詳細資訊，請參閱[How to:推斷屬性名稱和匿名類型宣告中的型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## <a name="key-properties"></a>索引鍵內容  
 從非索引鍵屬性的索引鍵屬性是數個基本的方式不同：  
  
- 只有索引鍵屬性的值會比較以判斷兩個執行個體是否相等。  
  
- 索引鍵屬性的值都是唯讀的而且無法變更。  
  
- 只有索引鍵屬性值包含編譯器所產生的雜湊程式碼演算法的匿名型別。  
  
### <a name="equality"></a>相等  
 匿名型別的執行個體可以有相同的匿名型別的執行個體才相等。 編譯器會將兩個執行個體視為相同類型的執行個體如果符合下列條件：  
  
- 在相同的組件中宣告。  
  
- 其屬性具有相同名稱，也就是相同的推斷型別，並宣告順序相同。 名稱比較不區分大小寫。  
  
- 在每個相同的屬性會標示為索引鍵屬性。  
  
- 每個宣告中的至少一個屬性是索引鍵的屬性。  
  
 匿名型別沒有索引鍵屬性的執行個體等於只有本身。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 相同匿名型別的兩個執行個體相等的其索引鍵的屬性值是否相等。 下列範例說明如何測試相等。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>唯讀的值  
 無法變更索引鍵屬性的值。 例如，在`prod8`在前一個範例中，`Name`並`Price`欄位`read-only`，但`OnHand`可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>從查詢運算式的匿名型別  
 查詢運算式不一定需要建立匿名型別。 如果可能的話，它們會使用現有的型別來保存資料行的資料。 會發生這種情況是當查詢傳回整筆記錄，從資料來源或從每一筆記錄只能有一個欄位。 在下列程式碼範例中，`customers`是物件的集合`Customer`類別。 類別具有許多屬性，而且您可以在查詢結果中，依任何順序包含一或多個。 在前兩個範例中，任何匿名型別不是必要的因為查詢選取的具名類型的項目：  
  
- `custs1` 包含字串的集合，因為`cust.Name`是一個字串。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2` 包含的集合`Customer`物件，因為每個項目的`customers`是`Customer`查詢所選取物件，而整個項目。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 不過，適當的具名型別不一定可用。 您可以選取 客戶名稱和其中一個用途、 客戶識別碼和另一個位置的位址和客戶名稱、 位址，以及第三個訂單記錄。 匿名型別可讓您以任何順序選取屬性的任何組合，而不先宣告新的具名型別，用於儲存結果。 相反地，編譯器會建立匿名型別屬性的每次編譯。 下列查詢會在每個選取 「 只有客戶的名稱和 ID 編號`Customer`物件中`customers`。 因此，編譯器會建立包含只有兩個屬性的匿名型別。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 名稱和資料類型的匿名型別中的屬性會從引數`Select`，`cust.Name`和`cust.ID`。 匿名型別所建立的查詢中的屬性一律是金鑰的屬性。 當`custs3`執行下列`For Each`迴圈中，結果是兩個索引鍵屬性，使用匿名型別的執行個體的集合`Name`和`ID`。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 所表示之集合中的項目`custs3`強型別，以及您可以使用 IntelliSense 來瀏覽可用的屬性，並確認其類型。  
  
 如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>決定是否要使用匿名型別  
 您為匿名類別的執行個體建立物件之前，請考慮是否這是最佳選項。 例如，如果您想要建立暫存的物件，以包含相關的資料，而且您已經不需要的其他欄位 」 和 「 完整的類別所包含的方法，匿名型別是很好的解決方案。 匿名型別也會很方便的如果您想要每個宣告中，選取不同的屬性，或如果您想要變更屬性的順序。 不過，如果您的專案包含數個物件具有相同的屬性，依照固定順序，您可以宣告它們更輕鬆地使用具名的類型的類別建構函式。 比方說，使用適當的建構函式，它是宣告數個執行個體的工作變得更容易`Product`類別比宣告匿名類型的數個執行個體。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 具名類型的另一個優點是，編譯器可以攔截的屬性名稱不小心打錯。 在上一個範例中， `firstProd2`， `secondProd2`，和`thirdProd2`主要做為相同匿名型別的執行個體。 不過，如果您不小心將宣告`thirdProd2`中的下列方法之一，其類型應為不同的`firstProd2`和`secondProd2`。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 更重要的是，有使用限制的匿名型別不會套用至具名型別的執行個體。 `firstProd2``secondProd2`，和`thirdProd2`相同匿名類型的執行個體。 不過，共用的匿名類型的名稱未提供，並不能出現在程式碼中需要的型別名稱的地方。 比方說，匿名型別無法用來定義方法簽章，若要宣告另一個變數或欄位，或任何類型宣告中。 如此一來，匿名型別時，不適合您有多個方法中共用資訊。  
  
## <a name="an-anonymous-type-definition"></a>匿名類型定義  
 為了回應執行個體的匿名型別宣告，編譯器會建立新的類別定義，其中包含指定的屬性。  
  
 如果匿名型別包含至少一個索引鍵屬性，定義會覆寫三個成員繼承自<xref:System.Object>: <xref:System.Object.Equals%2A>， <xref:System.Object.GetHashCode%2A>，和<xref:System.Object.ToString%2A>。 程式碼所產生的測試相等，並判斷雜湊碼值會考慮索引鍵的屬性。 如果匿名型別包含任何索引鍵屬性，只有<xref:System.Object.ToString%2A>會覆寫。 明確命名的匿名型別屬性不能與這些產生的方法衝突。 也就是說，您無法使用`.Equals`， `.GetHashCode`，或`.ToString`命名屬性。  
  
 匿名類型定義，至少有一個索引鍵屬性也實作<xref:System.IEquatable%601?displayProperty=nameWithType>介面，其中`T`是匿名型別的型別。  
  
 如需編譯器和覆寫方法的功能所建立的程式碼的詳細資訊，請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
## <a name="see-also"></a>另請參閱

- [物件初始設定式：具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [如何：推斷屬性名稱和匿名類型宣告中的類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名類型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
