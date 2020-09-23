---
title: 匿名類型
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 5ab3cf8c3c02ff35890f71ad6c7f314b51b87133
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075235"
---
# <a name="anonymous-types-visual-basic"></a>匿名類型 (Visual Basic)

Visual Basic 支援匿名型別，可讓您建立物件，而不需要撰寫資料類型的類別定義。 編譯器 (Compiler) 會自動幫您建立類別 (Class)。 類別沒有可使用的名稱，直接繼承自 <xref:System.Object> ，而且包含您在宣告物件時所指定的屬性。 因為未指定資料類型的名稱，所以稱為 *匿名型別*。  
  
 下列範例會將變數宣告 `product` 為匿名型別的實例，並將其建立為具有兩個屬性的匿名型別 `Name` `Price` 。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 *查詢運算式*使用匿名型別來合併查詢所選取的資料行。 您無法事先定義結果的類型，因為您無法預測特定查詢可能會選取的資料行。 匿名型別可讓您撰寫查詢，以任何順序選取任意數目的資料行。 編譯器會建立符合指定屬性和指定順序的資料類型。  
  
 在下列範例中， `products` 是產品物件的清單，其中每個物件都有許多屬性。 變數 `namePriceQuery` 會保存查詢的定義，當它執行時，會傳回匿名型別的實例集合，其具有兩個屬性： `Name` 和 `Price` 。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 變數 `nameQuantityQuery` 會保存查詢的定義，當它執行時，會傳回匿名型別的實例集合，其具有兩個屬性： `Name` 和 `OnHand` 。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 如需編譯器為匿名型別所建立之程式碼的詳細資訊，請參閱 [匿名型別定義](anonymous-type-definition.md)。  
  
> [!CAUTION]
> 匿名型別的名稱是編譯器產生的，而且可能會因編譯而異。 您的程式碼不應使用或依賴匿名型別的名稱，因為重新編譯專案時，名稱可能會變更。  
  
## <a name="declaring-an-anonymous-type"></a>宣告匿名型別  

 匿名型別之實例的宣告會使用初始化運算式清單來指定類型的屬性。 當您宣告匿名型別，而不是其他類別專案（例如方法或事件）時，您只能指定屬性。 在下列範例中， `product1` 是匿名型別的實例，其中包含兩個屬性： `Name` 和 `Price` 。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 如果您將屬性指定為索引鍵屬性，您可以使用它們來比較兩個匿名型別實例是否相等。 但是，索引鍵屬性的值無法變更。 如需詳細資訊，請參閱本主題稍後的「索引鍵屬性」一節。  
  
 請注意，宣告匿名型別的實例，就像使用物件初始化運算式宣告命名類型的實例一樣：  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 如需有關其他指定匿名型別屬性之方式的詳細資訊，請參閱 [如何：在匿名型別宣告中推斷屬性名稱和類型](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## <a name="key-properties"></a>索引鍵內容  

 索引鍵屬性與非索引鍵屬性有幾個基本的差異：  
  
- 系統只會比較索引鍵屬性的值，以判斷兩個實例是否相等。  
  
- 索引鍵屬性的值是唯讀的，而且無法變更。  
  
- 匿名型別的編譯器產生的雜湊程式碼演算法中只包含索引鍵屬性值。  
  
### <a name="equality"></a>等式  

 匿名型別的實例只有在它們是相同匿名型別的實例時，才能相等。 編譯器會將兩個實例視為相同型別的實例（如果它們符合下列條件）：  
  
- 它們會在相同的元件中宣告。  
  
- 它們的屬性具有相同的名稱、相同的推斷型別，而且是以相同順序宣告的。 名稱比較不區分大小寫。  
  
- 每個屬性中的相同屬性都會標示為索引鍵屬性。  
  
- 每個宣告中至少有一個屬性是索引鍵屬性。  
  
 沒有索引鍵屬性之匿名型別的實例，只等於本身。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 如果索引鍵屬性的值相等，則相同匿名型別的兩個實例會相等。 下列範例說明相等的測試方式。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>唯讀值  

 無法變更索引鍵屬性的值。 例如，在 `prod8` 上一個範例中， `Name` 和 `Price` 欄位是 `read-only` ，但 `OnHand` 可以變更。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>查詢運算式中的匿名型別  

 查詢運算式不一定需要建立匿名型別。 可能的話，它們會使用現有的類型來保存資料行資料。 當查詢從資料來源傳回完整記錄，或從每個記錄中傳回一個欄位時，就會發生這種情況。 在下列程式碼範例中， `customers` 是類別的物件集合 `Customer` 。 類別有許多屬性，您可以在查詢結果中，以任何順序包含一或多個屬性。 在前兩個範例中，不需要匿名型別，因為查詢會選取命名類型的元素：  
  
- `custs1` 包含字串的集合，因為 `cust.Name` 是字串。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2` 包含物件的集合 `Customer` ，因為的每個專案 `customers` 都是 `Customer` 物件，而且查詢會選取整個元素。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 不過，不一定可以使用適當的命名類型。 您可能會想要為一個用途（客戶識別碼和地點）選取客戶名稱和位址，並針對第三個用途選取客戶名稱、位址和訂單記錄。 匿名型別可讓您依任何順序選取任何屬性組合，而不需要先宣告新的命名類型來保存結果。 相反地，編譯器會為每個屬性編譯建立匿名型別。 下列查詢只會從中的每個物件選取客戶的名稱和 ID 號碼 `Customer` `customers` 。 因此，編譯器會建立僅包含這兩個屬性的匿名型別。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 匿名型別中屬性的名稱和資料類型都會從的引數取得 `Select` 、 `cust.Name` 和 `cust.ID` 。 由查詢所建立之匿名型別中的屬性一律是索引鍵屬性。 當 `custs3` 在下列迴圈中執行時 `For Each` ，結果會是具有兩個索引鍵屬性之匿名型別的實例集合： `Name` 和 `ID` 。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 以強型別表示之集合中的專案 `custs3` ，您可以使用 IntelliSense 來流覽可用的屬性並驗證其類型。  
  
 如需詳細資訊，請參閱 [Visual Basic 中的 LINQ 簡介](../linq/introduction-to-linq.md)。  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>決定是否要使用匿名型別  

 將物件建立為匿名類別的實例之前，請考慮這是否為最佳選項。 例如，如果您想要建立暫存物件來包含相關資料，而且您不需要完整類別可能包含的其他欄位和方法，則匿名型別是不錯的解決方案。 如果您想要針對每個宣告選取不同的屬性，或是想要變更屬性的順序，匿名型別也會很方便。 但是，如果您的專案包含多個具有相同屬性的物件（依固定順序），您可以使用具有類別的命名類型與類別的函式來更輕鬆地宣告它們。 例如，使用適當的函式，您可以更輕鬆地宣告類別的數個實例， `Product` 而不是宣告多個匿名型別的實例。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 命名類型的另一個優點是編譯器可能會攔截屬性名稱的意外出現內容。 在先前的範例中，、 `firstProd2` `secondProd2` 和的 `thirdProd2` 目的是要作為相同匿名型別的實例。 但是，如果您不小心以 `thirdProd2` 下列其中一種方式宣告，則其類型會與 `firstProd2` 和相同 `secondProd2` 。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 更重要的是，使用未套用至命名類型實例的匿名型別時，會有一些限制。 `firstProd2`、 `secondProd2` 和 `thirdProd2` 是相同匿名型別的實例。 不過，共用匿名型別的名稱無法使用，且不能出現在您的程式碼中預期的類型名稱。 例如，匿名型別無法用來定義方法簽章、宣告另一個變數或欄位，或在任何類型宣告中。 如此一來，當您必須跨方法共用資訊時，匿名型別就不適用。  
  
## <a name="an-anonymous-type-definition"></a>匿名型別定義  

 為了回應匿名型別的實例，編譯器會建立新的類別定義，其中包含指定的屬性。  
  
 如果匿名型別至少包含一個索引鍵屬性，則定義會覆寫三個繼承自的成員 <xref:System.Object> ： <xref:System.Object.Equals%2A> 、 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A> 。 針對測試相等和判斷雜湊碼值所產生的程式碼只會考慮索引鍵屬性。 如果匿名型別不包含索引鍵屬性， <xref:System.Object.ToString%2A> 則只會覆寫。 匿名型別的明確命名屬性不會與這些產生的方法產生衝突。 也就是說，您無法使用 `.Equals` 、 `.GetHashCode` 或 `.ToString` 來命名屬性。  
  
 具有至少一個索引鍵屬性的匿名型別定義也 <xref:System.IEquatable%601?displayProperty=nameWithType> 會執行介面，其中 `T` 是匿名型別的型別。  
  
 如需編譯器所建立之程式碼和覆寫方法之功能的詳細資訊，請參閱 [匿名型別定義](anonymous-type-definition.md)。  
  
## <a name="see-also"></a>另請參閱

- [物件初始設定式：具名和匿名型別](object-initializers-named-and-anonymous-types.md)
- [區域型別推斷](../variables/local-type-inference.md)
- [Visual Basic 中的 LINQ 簡介](../linq/introduction-to-linq.md)
- [如何：在匿名類型宣告中推斷屬性名稱和類型](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [匿名型別定義](anonymous-type-definition.md)
- [索引鍵](../../../language-reference/modifiers/key.md)
