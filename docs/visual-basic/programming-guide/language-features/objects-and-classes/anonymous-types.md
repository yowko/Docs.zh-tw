---
title: "Anonymous Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AnonymousType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], about anonymous types"
  - "anonymous types [Visual Basic]"
  - "types [Visual Basic], anonymous"
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 46
---
# Anonymous Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 支援匿名型別，這種型別可讓您不必撰寫資料型別的類別定義，即可建立物件。  編譯器 \(Compiler\) 會自動幫您建立類別 \(Class\)。  這個類別沒有可使用的名稱、會直接繼承自 <xref:System.Object>，並且包含您在宣告物件時指定的屬性。  因為不指定資料型別的名稱，所以才稱為「*匿名型別*」\(Anonymous Type\)。  
  
 下列範例會宣告並建立 `product` 變數做為匿名型別的執行個體 \(Instance\)，並具有 `Name` 和 `Price` 兩個屬性。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 「*查詢運算式*」\(Query Expression\) 會使用匿名型別來合併查詢所選取的資料行。  因為您無法預測特定查詢會選取哪些資料行，所以無法事先定義結果的型別。  匿名型別可讓您撰寫查詢，以任意順序選取任意數目的資料行。  編譯器會建立符合所指定屬性和所指定順序的資料型別。  
  
 在下列範例中，`products` 是產品物件的清單，其中每個產品物件都具有多個屬性。  `namePriceQuery` 變數包含查詢的定義，這個查詢執行時會傳回某個匿名型別 \(具有 `Name` 和 `Price` 兩個屬性\) 的執行個體集合。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 `nameQuantityQuery` 變數包含查詢的定義，這個查詢執行時會傳回某個匿名型別 \(具有 `Name` 和 `OnHand` 兩個屬性\) 的執行個體集合。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 如需編譯器針對匿名型別建立之程式碼的詳細資訊，請參閱[Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
> [!CAUTION]
>  匿名型別的名稱是由編譯器產生，而且每次編譯時產生的名稱都不同。  您的程式碼不應該使用或固定參考匿名型別的名稱，因為一旦重新編譯專案，這個名稱就會不同。  
  
## 宣告匿名型別  
 匿名型別執行個體的宣告中會使用初始設定式清單來指定該型別的屬性。  當您宣告匿名型別時，只能指定屬性，而不能指定方法或事件等其他類別項目。  在下列範例中，`product1` 即為某個匿名型別的執行個體，具有 `Name` 和 `Price` 兩個屬性。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 如果您將一些屬性指定為索引鍵屬性，可以用它們來比較兩個匿名型別執行個體是否相等。  不過，索引鍵屬性的值無法變更。  如需詳細資訊，請參閱本主題稍後的＜索引鍵屬性＞一節。  
  
 請注意，宣告匿名型別的執行個體類似於使用物件初始設定式來宣告具名型別的執行個體：  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 如需指定匿名型別屬性之其他方式的詳細資訊，請參閱 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## 主要屬性  
 索引鍵屬性與非索引鍵屬性基本上有下列不同：  
  
-   在判斷兩個執行個體是否相等時，只會比較索引鍵屬性的值。  
  
-   索引鍵屬性的值是唯讀的，無法變更。  
  
-   只有索引鍵屬性的值會納入編譯器針對匿名型別產生雜湊程式碼的演算法中。  
  
### 相等  
 匿名型別執行個體必須屬於相同的匿名型別，才有可能相等。  如果兩個執行個體符合下列條件，編譯器就會將它們視為相同型別的執行個體：  
  
-   宣告在同一個組件 \(Assembly\) 中。  
  
-   它們的屬性具有相同的名稱、相同的推斷型別和相同的宣告順序。  名稱比較不區分大小寫。  
  
-   兩個執行個體中相同的屬性會標記為索引鍵屬性。  
  
-   每個宣告中至少有一個屬性是索引鍵屬性。  
  
 沒有索引鍵屬性的匿名屬性執行個體只會與自己相等。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 同一匿名型別的兩個執行個體必須具有相同的索引鍵值，才算相等。  下列範例說明測試相等性的方法。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### 唯讀值  
 索引鍵屬性的值無法變更。  例如，在上一個範例的 `prod8` 中，`Name` 和 `Price` 欄位是 `read-only` 的，但 `OnHand` 是可以變更的。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## 查詢運算式中的匿名型別  
 使用查詢運算式時不一定需要建立匿名型別。  它們會盡量使用現有的型別來存放資料行資料。  當查詢傳回資料來源中的整筆記錄，或每筆記錄中的某個欄位時，就會發生這個情況。  在下列程式碼範例中，`customers` 是 `Customer` 類別之物件的集合。  這個類別具有許多屬性，您可以依任意順序將其中一個或多個屬性加入至查詢結果。  在前兩個範例中，查詢會選取具名型別的項目，因此不需要使用匿名型別：  
  
-   `custs1` 包含字串的集合，原因是 `cust.Name` 是一個字串。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2` 包含 `Customer` 物件的集合，原因是 `customers` 中的每個項目都是一個 `Customer` 物件，而查詢選取了整個項目。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 但是不一定總是有適當的具名型別。  您可能有時需要選取客戶姓名和地址，有時需要選取客戶 ID 編號和位置，而有時又需要選取客戶姓名、地址和訂單記錄。  匿名型別可讓您以任意順序選取任何屬性的組合，而不需先宣告新的具名型別來存放結果。  編譯器會在每次編譯屬性時自動建立匿名型別。  下列查詢只會從 `customers` 中的每個 `Customer` 選取客戶的姓名和 ID 編號。  因此，編譯器會建立只包含這兩個屬性的匿名型別。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 匿名型別中屬性的名稱和資料型別都是取自 `Select`、`cust.Name` 和 `cust.ID` 的引數。  查詢所建立之匿名型別中的屬性，一定是索引鍵屬性。  當執行下列 `For Each` 迴圈 \(Loop\) 中的 `custs3` 時，結果會產生某個匿名型別 \(具有 `Name` 和 `ID` 兩個屬性\) 之執行個體的集合。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 `custs3` 所表示之集合中的項目是強型別 \(Strongly Typed\)，您可以使用 IntelliSense 巡覽可用的屬性並確認它們的型別。  
  
 如需詳細資訊，請參閱 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
## 決定是否要使用匿名型別  
 在建立物件做為匿名類別 \(Anonymous Class\) 的執行個體之前，請先考慮這是否是最好的選擇。  例如，如果您想要建立暫存物件來存放相關資料，但是不需要完整類別所包含的其他欄位或方法，則匿名型別是不錯的選擇。  如果您想要針對每個宣告選取不同的屬性，或者想要變更屬性的順序，則匿名型別同樣也很方便。  但是，如果您的專案包含數個具有相同屬性 \(順序也固定\) 的物件，則搭配使用具名型別和類別建構函式 \(Constructor\) 來宣告這些物件，將會更容易。  例如，只要有適當的建構函式，宣告 `Product` 類別的數個執行個體會比宣告匿名型別的數個執行個體來得簡單。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 具名型別的另一項優點是編譯器可以攔截不小心設錯型別的屬性名稱。  在先前的範例中，`firstProd2`、`secondProd2` 和 `thirdProd2` 應該要是同一個匿名型別的執行個體。  不過，如果您不小心以下列方式之一宣告 `thirdProd2`，它的型別就會與 `firstProd2` 和 `secondProd2` 不同。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 更重要的是，匿名型別具有一些具名型別執行個體所沒有的使用限制。  `firstProd2`、`secondProd2` 和 `thirdProd2` 都是同一個匿名型別的執行個體。  不過，共用匿名型別的名稱無法使用，也不能用於程式碼中需要使用型別名稱的地方。  例如，匿名型別無法用來定義方法簽章、宣告另一個變數或欄位，也不能用於任何型別宣告 \(Type Declaration\) 中。  因此，當您需要讓多個方法共用資訊時，匿名型別就不適用。  
  
## 匿名型別定義  
 遇到匿名型別執行個體的宣告時，編譯器會建立新的類別定義，其中含有指定的屬性。  
  
 如果匿名型別至少包含一個索引鍵屬性，則這個定義會覆寫繼承自 <xref:System.Object> 的三個成員：<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A>。  所產生用於測試相等性和決定雜湊程式碼值的程式碼，只會將索引鍵屬性納入考慮。  如果匿名型別不包含索引鍵屬性，則只會覆寫 <xref:System.Object.ToString%2A>。  匿名型別中明確命名的屬性不能與這些產生的方法衝突。  換句話說，您不能使用 `.Equals`、`.GetHashCode` 或 `.ToString` 來命名屬性。  
  
 至少含有一個索引鍵屬性的匿名型別同時也會實作 <xref:System.IEquatable%601?displayProperty=fullName> 介面，其中 `T` 是匿名型別的類型。  
  
 如需編譯器所建立之程式碼以及遭覆寫方法之功能的詳細資訊，請參閱[Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)。  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)