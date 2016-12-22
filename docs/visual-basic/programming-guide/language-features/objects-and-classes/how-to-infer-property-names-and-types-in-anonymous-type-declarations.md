---
title: "如何：在匿名類型宣告中推斷屬性名稱和類型 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "推斷屬性名稱 [Visual Basic]"
  - "匿名類型 [Visual Basic], 推斷屬性名稱和類型"
  - "推斷屬性類型 [Visual Basic]"
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 如何：在匿名類型宣告中推斷屬性名稱和類型 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

匿名類型未提供任何機制來直接指定屬性的資料類型。 所有屬性的類型都是推斷而來。 在下列範例中，透過用來初始化 `Name` 和 `Price` 類型的值，直接推斷這些類型。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 匿名類型也可以推斷其他來源的屬性名稱和類型。 以下章節提供可進行推斷的情況清單，以及不可進行推斷的狀況範例。  
  
## 成功推斷  
  
#### 匿名類型可以推斷下列來源的屬性名稱和類型：  
  
-   透過變數名稱。 匿名類型 `anonProduct` 會有兩個屬性：`productName` 和 `productPrice`。 其資料類型分別是下列原始變數：`String` 和 `Double`。  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   透過其他物件的屬性或欄位名稱。 例如，考慮使用類型為 `CarClass` 且包含 `Name` 和 `ID` 屬性的 `car` 物件。 若要利用使用 `car` 物件值初始化的 `Name` 和 `ID` 屬性來建立新的匿名類型執行個體 \(`car1`\)，您可以撰寫下列項目：  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     先前的宣告等同於定義匿名類型 `car2` 的較長程式碼行。  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   透過 XML 成員名稱。  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     針對 `anon` 產生的屬性會有一個類型 <xref:System.Collections.IEnumerable>\(Of XElement\) 的屬性 `Book`。  
  
-   透過沒有參數的函式 \(如下列範例中的 `SomeFunction`\)。  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     下列程式碼中的變數 `anon2` 是具有一個屬性 \(名稱為 `First` 的字元\) 的匿名類型。 此程式碼會顯示字母 "E" \(即函式 <xref:System.Linq.Enumerable.First%2A> 所傳回的字母\)。  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## 推斷失敗  
  
#### 在許多情況下，名稱推斷都會失敗，包括下列情況：  
  
-   推斷衍生自叫用方法、建構函式或需要引數的參數化屬性。 如果 `someFunction` 有一個或多個引數，則 `anon1` 的先前宣告會失敗。  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     指派給新的屬性名稱可解決問題。  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   推斷衍生自複雜運算式。  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     將運算式的結果指派給屬性名稱，即可解決錯誤。  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   多個屬性的推斷會產生兩個或多個同名的屬性。 推斷回先前範例中的宣告，無法將 `product.Name` 和 `car1.Name` 列為相同匿名類型的屬性。 原因是所有的推斷識別項都是 `Name`。  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     將值指派給不同的屬性名稱，即可解決問題。  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     請注意，大小寫的變更 \(大寫與小寫字母之間的變更\) 並不會讓這兩個名稱不同。  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   一個屬性的初始類型和值取決於尚未建立的另一個屬性。 例如，除非已初始化 `.LastName`，否則 `.IDName = .LastName` 在匿名類型宣告中無效。  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     在此範例中，您可以反轉屬性的宣告順序來修正問題。  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   匿名類型的屬性名稱與 <xref:System.Object> 成員的名稱相同。 例如，因為 `Equals` 是 <xref:System.Object> 的方法，所以下列宣告會失敗。  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     變更屬性名稱，即可修正問題：  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## 請參閱  
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)