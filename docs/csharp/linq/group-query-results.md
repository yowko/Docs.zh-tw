---
title: 將查詢結果分組 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 將結果分組。
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 4da0aac6b406f588ea4f241c72d5700e8a63838c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403861"
---
# <a name="group-query-results"></a>將查詢結果分組

分組是 LINQ 最強大的功能之一。 下例示範如何以各種方式分組資料︰

- 根據單一屬性。

- 根據字串屬性的第一個字母。

- 根據計算的數字範圍。

- 根據布林值述詞或其他運算式。

- 根據複合索引鍵。

此外，最後兩個查詢會將其結果投射至只包含學生姓名的新匿名型別。 如需詳細資訊，請參閱 [group 子句](../language-reference/keywords/group-clause.md)。

## <a name="example"></a>範例

本主題中的所有範例都使用下列的協助程式類別和資料來源。

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a>範例

下例示範如何將項目的單一屬性用為群組索引鍵，來分組來源項目。 本例的索引鍵是 `string`，為學生的姓氏。 索引鍵也可以使用子字串。 群組作業在類型上會使用預設的相等比較子。

將下列方法貼入 `StudentClass` 類別。 將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySingleProperty()`。

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a>範例

下例示範如何在群組索引鍵使用物件屬性以外的項目分組來源項目。 本例的索引鍵是學生姓氏的第一個字母。

將下列方法貼入 `StudentClass` 類別。 將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupBySubstring()`。

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a>範例

下例示範如何將數字範圍用為群組索引鍵來分組來源項目。 查詢接著會將結果投射到只包含姓名及學生所屬百分位數範圍的匿名型別。 使用匿名型別是因為沒必要使用完整的 `Student` 物件來顯示結果。 `GetPercentile` 是根據學生平均分數計算百分位數的 Helper 函式。 方法會傳回 0 到 10 之間的整數。

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

將下列方法貼入 `StudentClass` 類別。 將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByRange()`。

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a>範例

下例示範如何使用布林比較運算式來分組來源項目。 在本例中，布林運算式會測試學生的平均測驗分數是否大於 75。 同上例，結果會投射至匿名型別，因為不需要完整的來源項目。 請注意，匿名型別中的屬性會成為 `Key` 成員上的屬性，並可在執行查詢時依名稱存取。

將下列方法貼入 `StudentClass` 類別。 將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByBoolean()`。

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a>範例

下例示範如何使用匿名型別來封裝包含多個值的索引鍵。 本例的第一個索引鍵值是學生姓氏的第一個字母。 第二個索引鍵值是布林值，指定學生第一次的考試分數是否超過 85。 您可以索引鍵中的任何屬性來排序群組。

將下列方法貼入 `StudentClass` 類別。 將 `Main` 方法中的呼叫陳述式變更為 `sc.GroupByCompositeKey()`。

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a>另請參閱

<xref:System.Linq.Enumerable.GroupBy%2A>  
<xref:System.Linq.IGrouping%602>  
[Language-Integrated Query (LINQ)](index.md)  
[group 子句](../language-reference/keywords/group-clause.md)  
[匿名類型](../programming-guide/classes-and-structs/anonymous-types.md)  
[在分組作業上執行子查詢](perform-a-subquery-on-a-grouping-operation.md)  
[建立巢狀群組](create-a-nested-group.md)  
[分組資料](../programming-guide/concepts/linq/grouping-data.md)  