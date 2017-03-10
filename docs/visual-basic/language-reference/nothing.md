---
title: "Nothing (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Nothing"
  - "vb.Nothing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Nothing keyword"
  - "Nothing keyword, syntax"
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: 31
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 31
---
# Nothing (Visual Basic)
[!INCLUDE[vs2017banner](../../visual-basic/includes/vs2017banner.md)]

代表任何資料型別的預設值。  如果是參考型別，預設值是`null`的參考。  實值型別的預設值而定是否可為 null 實值型別。  
  
> [!NOTE]
>  不可為 null 的實值型別， `Nothing` Visual Basic 在不同於`null` C\# 中。  在 Visual Basic，如果您將設定為不可為 null 實值型別的變數`Nothing`，此變數設為預設值為其宣告的型別。  在 C\#，如果您指派給不可為 null 實值型別的變數`null`，就會發生編譯時期錯誤。  
  
## 備註  
 `Nothing`表示資料型別的預設值。  預設值的變數是實值型別或參考型別而定。  
  
 變數的*實值型別*直接包含它的值。  實值型別包括所有的數字資料型別， `Boolean`， `Char`， `Date`，所有的結構，以及所有列舉型別。  變數的*參考型別*物件的執行個體的參考儲存在記憶體中。  參考型別包括類別、 陣列、 委派和字串。  如需詳細資訊，請參閱 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
 如果變數是實值鍵入的行為的`Nothing`變數是否為可為 null 的資料型別而定。  若要顯示可為 null 的實值型別，將`?`的型別名稱的修飾詞。  指派`Nothing` ，可為 null 的變數值設定為`null`。  如需詳細資訊與範例，請參閱[Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)。  
  
 如果不是可為 null 的實值型別的變數，指派`Nothing`到它將它設成預設值為其宣告的型別。  如果該型別包含變數成員，皆會設定為自己型別的預設值。  下列範例以純量型別來說明。  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/visualbasic/nothing_1.vb)]  
  
 如果變數是參考型別，指派`Nothing` ，此變數設為`null`的變數型別的參考。  此變數會設定為 \[ `null`的參考沒有任何物件相關聯。  以下範例就是示範這項作業。  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/visualbasic/nothing_2.vb)]  
  
 當檢查是否參考 \(或型別的可為 null 值\) 變數`null`，不會使用`= Nothing`或`<> Nothing`。  Always use `Is Nothing` or `IsNot Nothing`.  
  
 在 Visual Basic 中的字串，則為空字串等於`Nothing`。  因此， `"" = Nothing`為 true。  
  
 下列範例示範使用 `Is` 和 `IsNot` 運算子的比較。  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/visualbasic/nothing_3.vb)]  
  
 如果您宣告變數而未使用`As`子句，並且將其設定為`Nothing`，則該變數的類型會是`Object`.  其中一個範例是`Dim something = Nothing`。  將產生編譯時期錯誤就會發生這種情況下當`Option Strict`上和`Option Infer`已關閉。  
  
 當您指派 `Nothing` 給物件變數時，此變數即不再參考至任一個物件執行個體。  如果此變數之前已參考至某執行個體，將它設定為 `Nothing` 並不會終止該執行個體本身。  只有在記憶體回收行程 \(Garbage Collector，GC\) 偵測到沒有餘留現用參考之後，執行個體才會終止，且與它相關的記憶體和系統資源會被釋放。  
  
 `Nothing`不同於<xref:System.DBNull>物件，該物件代表未初始化的變數或不存在的資料庫資料行。  
  
## 請參閱  
 [Dim Statement](../../visual-basic/language-reference/statements/dim-statement.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Lifetime in Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Is Operator](../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)