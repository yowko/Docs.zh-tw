---
title: "Object Initializers: Named and Anonymous Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ObjectInitializer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object initializers [Visual Basic]"
  - "anonymous types [Visual Basic], object initializers"
  - "initializing properties [Visual Basic]"
  - "initializers [Visual Basic]"
  - "named types [Visual Basic]"
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object Initializers: Named and Anonymous Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

物件初始設定式可以讓您使用單一運算式來指定複雜物件的屬性，  而且可以用來建立具名型別和匿名型別的執行個體 \(Instance\)。  
  
## Declarations  
 具名和匿名型別之執行個體的宣告看起來相同，但是效果不同。  每個分類都有各自的功能和限制。  下列範例顯示使用物件初始設定式清單來宣告及初始化具名類別 `Customer` 之執行個體的方便方法。  請注意，類別 \(Class\) 的名稱指定在關鍵字 `New` 後面。  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 匿名型別沒有可以使用的名稱。  因此匿名型別的執行個體化 \(Instantiation\) 無法包含類別名稱。  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 兩個宣告的需求和結果都不同。  對於 `namedCust`，具有 `Name` 屬性的 `Customer` 類別必須已經存在，並由宣告建立該類別的執行個體。  對於 `anonymousCust`，則由編譯器 \(Compiler\) 定義具有一個屬性的新類別，也就是名為 `Name` 的字串，然後再建立該類別的新執行個體。  
  
## 具名型別  
 物件初始設定式提供了一個簡單方法，可以呼叫型別的建構函式 \(Constructor\)，然後在單一陳述式中設定部分或所有屬性的值。  編譯器會叫用 \(Invoke\) 陳述式的適當建構函式：如果沒有引數則叫用預設建構函式，如果傳送了一個或多個引數則叫用參數型建構函式。  然後，指定的屬性會以初始設定式清單中出現的順序進行初始化。  
  
 初始設定式清單中的每一個初始設定，各會指派一個初始值給類別的成員。  成員的名稱和資料型別則是在定義類別時決定。  在下列範例中，必須有 `Customer` 類別，也必須有名為 `Name` 和 `City` 且接受字串值的成員。  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 或者，您也可以使用下列程式碼取得相同的結果：  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 每個宣告等同於下列範例，此範例使用預設建構函式建立 `Customer` 物件，然後使用 `With` 陳述式指定 `Name` 和 `City` 屬性的初始值。  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 如果 `Customer` 類別包含參數型建構函式，可以讓您傳送諸如 `Name` 的值，則您也可以用下列方法宣告及初始化 `Customer` 物件：  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 您不需要初始化所有屬性，如下列程式碼所示。  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 但是，初始設定清單不能是空的。  未初始化的屬性會保留其預設值。  
  
### 具名型別的型別推斷  
 您可以縮短 `cust1` 宣告的程式碼，方法是結合物件初始設定式與區域型別推斷。  這樣有助於略過變數宣告中的 `As` 子句。  變數的資料型別是根據指派作業所建立之物件的型別來推斷。  在下列範例中，`cust6` 的型別是 `Customer`。  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### 具名型別的備註  
  
-   類別成員在物件初始設定式清單中無法初始化一次以上。  `cust7` 的宣告會造成錯誤。  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   成員可以用於初始化其本身或初始化其他欄位。  如果在成員初始化之前就存取成員，如同下列 `cust8` 的宣告所示，則會使用預設值。  請記住，處理使用物件初始設定式的宣告時，發生的第一件事是叫用適當的建構函式。  接著會初始化初始設定式清單中的個別欄位。  在下列範例中，會為 `cust8` 指派 `Name` 的預設值，並在 `cust9` 中指派初始化的值。  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     下列範例使用 `cust3` 和 `cust4` 的參數型建構函式，來宣告並初始化 `cust10` 和 `cust11`。  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   物件初始設定式可以是巢狀。  在下列範例中，`AddressClass` 是具有兩個屬性 \(`City` 和 `State`\) 的類別，而 `Customer` 類別具有 `Address` 屬性，該屬性是 `AddressClass` 的執行個體。  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   初始設定清單不能是空的。  
  
-   要初始化的執行個體不能是 Object 型別。  
  
-   要初始化的類別成員不能是共用成員、唯讀成員、常數或方法呼叫。  
  
-   要初始化的類別成員不能進行索引或限定。  下列範例會產生編譯器錯誤：  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## 匿名型別  
 匿名型別會使用物件初始設定式，建立您未明確定義及命名的新型別執行個體。  並由編譯器根據您在物件初始設定式清單中指定的屬性產生型別。  因為不指定型別的名稱，所以才稱為「*匿名型別*」\(Anonymous Type\)。  例如，請比較下列宣告與先前的 `cust6` 宣告。  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 唯一的語法差異是資料型別的 `New` 後面未指定名稱。  但是，結果有相當大的差異。  編譯器會定義新的匿名型別，該型別具有兩個屬性 `Name` 和 `City`，並且以指定值建立執行個體。  型別推斷會判斷範例中 `Name` 和 `City` 的型別為字串。  
  
> [!CAUTION]
>  匿名型別的名稱是由編譯器產生，而且每次編譯時產生的名稱都不同。  您的程式碼不應該使用或固定參考匿名型別的名稱。  
  
 因為型別的名稱無法使用，所以您無法使用 `As` 子句宣告 `cust13`。  其型別必須由推斷得出。  不需使用晚期繫結 \(Late Binding\)，上述限制即會將匿名型別的使用方式限制在區域變數。  
  
 匿名型別可對 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢提供重要支援。  如需在查詢中使用匿名型別的詳細資訊，請參閱[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)和 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。  
  
### 匿名型別的備註  
  
-   通常，匿名型別宣告中的大部分或所有屬性都是索引鍵屬性，藉由在屬性名稱前輸入關鍵字 `Key` 來表示。  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     如需索引鍵屬性的詳細資訊，請參閱 [Key](../../../../visual-basic/language-reference/modifiers/key.md)。  
  
-   和具名型別相同，匿名型別定義的初始設定式清單必須宣告至少一個屬性。  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   當宣告匿名型別的執行個體時，編譯器會產生相符的匿名型別定義。  屬性的名稱和資料型別是從執行個體宣告中擷取，並由編譯器加入至定義中。  屬性不會事先命名或定義，此點與具名型別不同。  其型別則是推斷得來。  您無法使用 `As` 子句指定屬性的資料型別。  
  
-   匿名型別也可以用下列幾個其他方法建立其屬性的名稱和值。  例如，匿名型別屬性可以採用變數的名稱和值，或其他物件之屬性的名稱和值。  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     如需在匿名型別中定義屬性之選項的詳細資訊，請參閱 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。  
  
## 請參閱  
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [如何：在匿名類型宣告中推斷屬性名稱和類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)   
 [How to: Declare an Object by Using an Object Initializer](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)