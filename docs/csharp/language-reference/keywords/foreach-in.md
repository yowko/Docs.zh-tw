---
title: "foreach、in (C# 參考)"
ms.date: 10/11/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5601682d53a01ff07aba7e416aa81ded4c03e4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# 參考)
`foreach` 陳述式會為陣列或物件集合中每個實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面的每個元素，重複一組內嵌陳述式。 `foreach` 陳述式可用來逐一查看集合，以取得所需的資訊，但不能用來新增或移除來源集合中的項目，以避免無法預期的副作用。 如果您必須新增或移除來源集合中的項目，請使用 [for](for.md) 迴圈。
  
 內嵌陳述式會針對陣列或集合中的每個元素繼續執行。 在完成集合中所有元素的反覆運算之後，控制權會轉移到 `foreach` 區塊之後的下一個陳述式。
  
 您可以在 `foreach` 區塊內的任何位置，使用 [break](break.md) 關鍵字跳出迴圈，或使用 [continue](continue.md) 關鍵字逐步執行到迴圈中的下一個反覆運算。

 `foreach` 迴圈也可以透過 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 陳述式結束。

 如需 `foreach` 關鍵字和程式碼範例的詳細資訊，請參閱下列主題：  

 [搭配陣列使用 foreach](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [如何：使用 foreach 存取集合類別](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a>範例
 下列程式碼顯示三個範例。

> [!TIP]
> 您可以修改範例，以試驗語法，並再試一次不同更類似於使用案例的使用方式。 請按 [執行] 以執行程式碼，然後編輯並再按 [執行]。

-   顯示整數陣列內容的一般 `foreach` 迴圈

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   執行相同動作的 [for](../../../csharp/language-reference/keywords/for.md) 迴圈

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   維護陣列中元素數目計數的 `foreach` 迴圈

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a>C# 語言規格
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱  

[C# 參考](../index.md)

[C# 程式設計指南](../../programming-guide/index.md)

[C# 關鍵字](index.md)

[反覆運算陳述式](iteration-statements.md)

[for](for.md)
