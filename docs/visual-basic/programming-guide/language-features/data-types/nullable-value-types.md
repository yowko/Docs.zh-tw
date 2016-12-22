---
title: "Nullable Value Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Nullable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nullable types [Visual Basic]"
  - "? [Visual Basic]"
  - "types [Visual Basic], nullable"
  - "nullable types"
  - "data types [Visual Basic], nullable"
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nullable Value Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

有時會在特定情況下使用不具有已定義值的實值型別。  例如，資料庫中的欄位可能需要在已指派有意義值與未指派值之間加以區別。  實值型別可擴充為接受一般值或 null 值。  這類擴充稱為「*可為 Null 的型別*」\(Nullable Type\)。  
  
 每個可為 Null 的型別是從泛型 <xref:System.Nullable%601> 結構建構而來。  請考慮會追蹤工作相關活動的資料庫。  下列範例會建構可為 Null 的 `Boolean` 型別，並宣告該型別的變數。  您可以用下列三種方法撰寫宣告：  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 變數 `ridesBusToWork` 可存放 `True` 值、`False` 值或根本沒有值。  初始預設值是「根本沒有值」，在這個情況下，表示尚未取得這個人的資訊。  相較之下，`False` 表示已取得資訊，且那個人未搭乘公車上班。  
  
 您可以宣告具有可為 Null 之型別的變數和屬性 \(Property\)，而且可以宣告具有可為 Null 之型別的元素陣列。  也可以將具有可為 Null 型別的程序宣告為參數，並從 `Function` 程序傳回可為 Null 的型別。  
  
 但無法在參考型別 \(Reference Type\) 上建構可為 Null 的型別 \(例如陣列、`String` 或類別 \(Class\)\)。  基礎型別必須是實值型別。  如需詳細資訊，請參閱 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)。  
  
## 使用可為 Null 型別的變數  
 可為 Null 型別的最重要成員是它的 <xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 屬性。  如果是可為 Null 型別的變數，則 <xref:System.Nullable%601.HasValue%2A> 會告知您變數是否包含已定義值。  如果 <xref:System.Nullable%601.HasValue%2A> 為 `True`，則可以從 <xref:System.Nullable%601.Value%2A> 中讀取值。  請注意，<xref:System.Nullable%601.HasValue%2A> 和 <xref:System.Nullable%601.Value%2A> 都是 `ReadOnly` 屬性。  
  
### 預設值  
 宣告具有可為 Null 型別的變數時，<xref:System.Nullable%601.HasValue%2A> 屬性的預設值為 `False`。  這表示變數依預設沒有已定義值，而非基礎實值型別的預設值。  在下列範例中，即使 `Integer` 型別的預設值為 0，變數 `numberOfChildren` 一開始也不會有已定義值。  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 null 值可用於指出未定義或未知的值。  如果 `numberOfChildren` 已宣告成 `Integer`，則沒有值可指出目前無法使用該資訊。  
  
### 儲存值  
 您可以用一般的方式，將值儲存於可為 Null 型別的變數或屬性中。  下列範例會將值指派給先前範例中所宣告的變數 `numberOfChildren`。  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 如果可為 Null 型別的變數或屬性包含已定義值，您可以讓它還原成未指派值的初始狀態。  將變數或屬性設定成 `Nothing`，即可達到此目的 \(如下列範例所示\)。  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  雖然您可以將 `Nothing` 指派給可為 Null 型別的變數，但是無法使用等號對 `Nothing` 進行任何測試。  使用等號的比較 `someVar = Nothing` 一律會評估為 `Nothing`。  您可以測試變數的 <xref:System.Nullable%601.HasValue%2A> 屬性是否為 `False`，或使用 `Is` 或 `IsNot` 運算子進行測試。  
  
### 擷取值  
 如果要擷取可為 Null 型別之變數的值，則應先測試 <xref:System.Nullable%601.HasValue%2A> 屬性，以確認它具有值。  如果您嘗試在 <xref:System.Nullable%601.HasValue%2A> 為 `False` 時讀取值，則 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會擲回 <xref:System.InvalidOperationException> 例外狀況 \(Exception\)。  下列範例會顯示讀取先前範例之變數 `numberOfChildren` 的建議方式。  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## 比較可為 Null 的型別  
 當可為 Null 的 `Boolean` 變數用於 Boolean 運算式時，結果可以是 `True`、`False` 或 `Nothing`。  下列是 `And` 和 `Or` 的事實資料表。  因為 `b1` 和 `b2` 現在有 3 個可能值，所以共有 9 個組合要評估。  
  
|b1|b2|b1 和 b2|b1 或 b2|  
|--------|--------|-------------|-------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 當布林值變數或運算式的值為 `Nothing` 時，代表它不是 `true` 也不是 `false`。  參考下列範例：  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 在這個範例中，`b1 And b2` 評估為 `Nothing`。  因此會在每個 `If` 陳述式 \(Statement\) 中執行 `Else` 子句，輸出如下：  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` 和 `OrElse` 使用「最少運算」\(Short\-Circuit\) 評估，必須在第一個運算元評估為 `Nothing` 時評估第二個運算元。  
  
## 傳用  
 如果算術、比較、移位或型別運算的其中一個或兩個運算元可為 Null，則該運算的結果也可為 Null。  如果兩個運算元都有非 `Nothing` 的值，則運算會在運算元的基礎值上執行，如同它們都不是可為 Null 的型別。  在下列範例中，變數 `compare1` 和 `sum1` 是隱含型別的。  如果您將滑鼠指標停留在上面，就會看到編譯器推斷兩者都是可為 Null 的型別。  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 如果其中一個或兩個運算元具有 `Nothing` 值，結果會是 `Nothing`。  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## 搭配使用可為 Null 的型別與資料  
 資料庫是使用可為 Null 之型別的其中一個最重要位置。  並非所有資料庫物件目前都支援可為 Null 的型別，而設計工具產生的資料表配接器則會支援該型別。  請參閱 [TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)中的＜TableAdapter 支援可為 Null 的型別＞。  
  
## 請參閱  
 <xref:System.InvalidOperationException>   
 <xref:System.Nullable%601.HasValue%2A>   
 [用可為 Null 的類型](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)   
 [資料類型](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)   
 [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)