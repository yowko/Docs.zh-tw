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
ms.openlocfilehash: 2d134b8c8ef202a91b35ad8645bf63622b5e8030
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040835"
---
# <a name="anonymous-types-visual-basic"></a>匿名類型 (Visual Basic)
Visual Basic 支援匿名型別, 這可讓您建立物件, 而不需要撰寫資料類型的類別定義。 編譯器 (Compiler) 會自動幫您建立類別 (Class)。 類別沒有可用的名稱、直接繼承自<xref:System.Object>, 且包含您在宣告物件中指定的屬性。 由於未指定資料類型的名稱, 因此稱為*匿名型別*。  
  
 下列範例會宣告並建立變數`product` , 做為具有兩個屬性 (和`Price`) `Name`的匿名型別實例。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 *查詢運算式*會使用匿名型別來結合查詢所選取的資料行。 您無法事先定義結果的類型, 因為您無法預測特定查詢可能會選取的資料行。 匿名型別可讓您撰寫查詢, 依任何順序選取任意數目的資料行。 編譯器會建立符合指定屬性和指定順序的資料類型。  
  
 在下列範例中, `products`是產品物件的清單, 每個都有許多屬性。 變數`namePriceQuery`會保留查詢的定義, 當它執行時, 會傳回具有兩個屬性 (和`Price`) `Name`之匿名型別實例的集合。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 變數`nameQuantityQuery`會保留查詢的定義, 當它執行時, 會傳回具有兩個屬性 (和`OnHand`) `Name`之匿名型別實例的集合。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 如需編譯器針對匿名型別所建立之程式碼的詳細資訊, 請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
> [!CAUTION]
> 匿名型別的名稱是編譯器產生的, 而且可能會因編譯而異。 您的程式碼不應該使用或依賴匿名型別的名稱, 因為重新編譯專案時, 名稱可能會變更。  
  
## <a name="declaring-an-anonymous-type"></a>宣告匿名型別  
 匿名型別的實例宣告會使用初始化運算式清單來指定型別的屬性 (property)。 當您宣告匿名型別, 而不是其他類別專案 (例如方法或事件) 時, 您可以只指定屬性。 在下列範例中, `product1`是匿名型別的實例, 其中包含兩個屬性: `Name`和`Price`。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 如果您指定屬性做為索引鍵屬性, 您可以使用它們來比較兩個匿名型別實例是否相等。 不過, 無法變更索引鍵屬性的值。 如需詳細資訊, 請參閱本主題稍後的金鑰屬性一節。  
  
 請注意, 宣告匿名型別的實例, 就像使用物件初始化運算式宣告已命名類型的實例一樣:  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 如需指定匿名型別屬性之其他方法的詳細資訊[, 請參閱如何:在匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)宣告中推斷屬性名稱和類型。  
  
## <a name="key-properties"></a>索引鍵內容  
 索引鍵屬性與非索引鍵屬性有幾個基本的差異:  
  
- 只有索引鍵屬性的值會進行比較, 以便判斷兩個實例是否相等。  
  
- 索引鍵屬性的值是唯讀的, 而且無法變更。  
  
- 只有索引鍵屬性值會包含在編譯器為匿名型別所產生的雜湊程式碼演算法中。  
  
### <a name="equality"></a>相等  
 匿名型別的實例只有在是相同匿名型別的實例時, 才可以相等。 如果符合下列條件, 編譯器會將兩個實例視為相同類型的實例:  
  
- 它們會在同一個元件中宣告。  
  
- 其屬性具有相同的名稱、相同的推斷型別, 而且會以相同的順序宣告。 名稱比較不區分大小寫。  
  
- 每個中的相同屬性都會標示為索引鍵屬性。  
  
- 每個宣告中至少有一個屬性是索引鍵屬性。  
  
 沒有索引鍵屬性的匿名型別實例, 只等於本身。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 如果索引鍵屬性的值相等, 則相同匿名型別的兩個實例相等。 下列範例說明如何測試等號比較。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>唯讀值  
 無法變更索引鍵屬性的值。 `prod8`例如, 在上一個範例`Price` `Name`中, 和欄位是`read-only`, 但`OnHand`可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>查詢運算式中的匿名型別  
 查詢運算式不一定需要建立匿名型別。 可能的話, 它們會使用現有的類型來保存資料行資料。 當查詢從資料來源傳回完整記錄, 或從每一筆記錄中只有一個欄位時, 就會發生這種情況。 在下列程式碼範例中`customers` , 是`Customer`類別物件的集合。 類別有許多屬性, 而且您可以依任何順序在查詢結果中包含一或多個屬性。 在前兩個範例中, 不需要匿名型別, 因為查詢會選取命名類型的元素:  
  
- `custs1`包含字串的集合, 因為`cust.Name`是字串。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2`包含`Customer`物件的集合, 因為的`customers`每個專案都是`Customer`物件, 而且查詢會選取整個元素。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 不過, 適當的命名類型不一定是可用的。 您可能想要選取客戶名稱和位址的一個用途、客戶識別碼和位置, 以及第三個的客戶名稱、位址和訂單歷程記錄。 匿名型別可讓您依任何順序選取任何屬性組合, 而不需要先宣告新的命名類型來保存結果。 相反地, 編譯器會針對每個屬性編譯建立匿名型別。 下列查詢只會從中`Customer` `customers`的每個物件選取客戶的名稱和 ID 編號。 因此, 編譯器會建立只包含這兩個屬性的匿名型別。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 匿名型別中屬性的名稱和資料類型都是從的引數`Select`取得、 `cust.Name`和`cust.ID`。 查詢所建立之匿名型別中的屬性一律是索引鍵屬性。 在`custs3`下列`For Each`迴圈中執行時, 結果會是匿名型別的實例集合, 其中包含兩個索引鍵屬性: `Name`和`ID`。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 所表示`custs3`之集合中的元素是強型別, 您可以使用 IntelliSense 來流覽可用的屬性, 並驗證其型別。  
  
 如需詳細資訊, 請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>決定是否要使用匿名型別  
 將物件建立為匿名類別的實例之前, 請考慮這是否為最佳選項。 例如, 如果您想要建立暫存物件以包含相關資料, 而不需要完整類別可能包含的其他欄位和方法, 則匿名型別是不錯的解決方案。 如果您想要針對每個宣告選擇不同的屬性, 或者您想要變更屬性的順序, 則匿名型別也很方便。 不過, 如果您的專案包含多個具有相同屬性的物件 (以固定順序), 您可以使用具有類別的方法的命名類型來更輕鬆地宣告它們。 例如, 使用適當的函式, 可以更輕鬆地宣告`Product`類別的數個實例, 而不是宣告多個匿名型別的實例。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 命名類型的另一個優點是, 編譯器可以攔截不小心的屬性名稱。 在先前的範例中`firstProd2`, `secondProd2`、和`thirdProd2`是要作為相同匿名型別的實例。 不過, 如果您不小心`thirdProd2`以下列其中一種方式宣告, 其型別會與`firstProd2`和`secondProd2`的類型不同。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 更重要的是, 使用不會套用至命名類型實例的匿名型別會有一些限制。 `firstProd2`、 `secondProd2`和`thirdProd2`是相同匿名型別的實例。 不過, 共用匿名型別的名稱無法使用, 而且不能出現在您的程式碼中需要類型名稱的位置。 例如, 匿名型別不能用來定義方法簽章、宣告另一個變數或欄位, 或是在任何型別宣告中。 因此, 當您必須跨方法共用資訊時, 匿名型別就不適用。  
  
## <a name="an-anonymous-type-definition"></a>匿名型別定義  
 為了回應匿名型別的實例宣告, 編譯器會建立新的類別定義, 其中包含指定的屬性。  
  
 如果匿名型別至少包含一個索引鍵屬性, 則定義會覆寫繼承自<xref:System.Object>的<xref:System.Object.Equals%2A>三個成員<xref:System.Object.ToString%2A>:、 <xref:System.Object.GetHashCode%2A>和。 針對測試相等和判斷雜湊碼值所產生的程式碼只會考慮索引鍵屬性。 如果匿名型別不包含索引鍵屬性, <xref:System.Object.ToString%2A>則只會覆寫。 匿名型別的明確命名屬性不能與這些產生的方法衝突。 也就是說, 您不能使用`.Equals`、 `.GetHashCode`或`.ToString`來命名屬性。  
  
 具有至少一個索引鍵屬性的匿名型別定義也會<xref:System.IEquatable%601?displayProperty=nameWithType>執行介面, `T`其中是匿名型別的型別。  
  
 如需編譯器所建立之程式碼和覆寫方法之功能的詳細資訊, 請參閱[匿名型別定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
## <a name="see-also"></a>另請參閱

- [物件初始化運算式:命名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [如何：在匿名型別宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名類型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
