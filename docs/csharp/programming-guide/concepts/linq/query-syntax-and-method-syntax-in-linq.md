---
title: LINQ 中的查詢語法及方法語法 (C#)
description: 瞭解 LINQ 中的查詢語法和方法語法。 這包括標準查詢運算子擴充方法和 lambda 運算式。
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 46b0e44182d22158aa5fa54a0f44bae70aa8ddd9
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063038"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>LINQ 中的查詢語法及方法語法 (C#)
簡介語言整合式查詢 (LINQ) 檔中的大部分查詢，都是使用 LINQ 宣告式查詢語法來撰寫。 不過，編譯程式碼時，必須將查詢語法轉譯成 .NET Common Language Runtime (CLR) 的方法呼叫。 這些方法呼叫會叫用標準查詢運算子，而其具有 `Where`、`Select`、`GroupBy`、`Join`、`Max` 和 `Average` 這類名稱。 您可以使用方法語法來直接呼叫它們，而不是使用查詢語法。  
  
 查詢語法和方法語法的語意相同，但許多人都發現查詢語法較為簡單且更容易閱讀。 某些查詢必須以方法呼叫形式表示。 例如，您必須使用方法呼叫，來表示可擷取符合所指定條件的項目數的查詢。 您也必須針對擷取來源序列中具有最大值的項目的查詢，使用方法呼叫。 <xref:System.Linq> 命名空間中標準查詢運算子的參考文件一般會使用方法語法。 因此，即使在開始撰寫 LINQ 查詢時，也很熟悉如何在查詢和查詢運算式本身中使用方法語法。  
  
## <a name="standard-query-operator-extension-methods"></a>標準查詢運算子擴充方法  
 下列範例示範簡單「查詢運算式」** 以及撰寫為「方法查詢」** 的語意對等查詢。  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 這兩個範例的輸出完全相同。 您可以看到查詢變數的類型在兩種形式中都相同：<xref:System.Collections.Generic.IEnumerable%601>。  
  
 若要了解方法查詢，讓我們更深入進行探討。 在運算式右側，請注意，`where` 子句會立即表示為 `numbers` 物件上的執行個體方法，您應該記得有一種 `IEnumerable<int>` 的類型。 如果您熟悉泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面，則會知道它沒有 `Where` 方法。 不過，如果您在 Visual Studio IDE 中叫用 IntelliSense 完成清單，則不只會看到 `Where` 方法，還會看到許多其他方法，例如 `Select`、`SelectMany`、`Join` 和 `Orderby`。 這些都是標準查詢運算子。  
  
 ![顯示 Intellisense 中所有標準查詢運算子的螢幕擷取畫面。](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 雖然看起來就像已重新定義 <xref:System.Collections.Generic.IEnumerable%601> 來包含這些額外方法，但是實際上卻不是。 標準查詢運算子會實作為一種稱為「擴充方法」** 的新方法。 擴充方法會「擴充」現有類型，其呼叫方式就像它們是類型上的執行個體方法一樣。 標準查詢運算子可擴充 <xref:System.Collections.Generic.IEnumerable%601>，而且這是您可以撰寫 `numbers.Where(...)` 的原因。  
  
 若要開始使用 LINQ，您只需要知道擴充方法的相關資訊，就是如何使用正確的指示詞將它們帶入應用程式的範圍 `using` 。 從您應用程式的觀點來看，擴充方法和一般執行個體方法都相同。  
  
 如需擴充方法的詳細資訊，請參閱[擴充方法](../../classes-and-structs/extension-methods.md)。 如需標準查詢運算子的詳細資訊，請參閱[標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)。 某些 LINQ 提供者（例如 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ）會針對以外的其他類型實作為其標準查詢運算子和其他擴充方法 <xref:System.Collections.Generic.IEnumerable%601> 。  
  
## <a name="lambda-expressions"></a>Lambda 運算式  
 在上述範例中，請注意，條件運算式 (`num % 2 == 0`) 會傳遞為 `Where` 方法的內嵌引數︰`Where(num => num % 2 == 0).` 這個內嵌運算式稱為 Lambda 運算式。 它方便您撰寫程式碼，而這些程式碼之前必須以更難處理的形式撰寫為匿名方法、泛型委派或運算式樹狀結構。 在 C# 中，`=>` 是 Lambda 運算子，視為「到」。 運算子左側的 `num` 是對應到查詢運算式中 `num` 的輸入變數。 編譯器可以推斷 `num` 類型，因為它知道 `numbers` 是泛型 <xref:System.Collections.Generic.IEnumerable%601> 類型。 Lambda 的主體就與查詢語法或任何 C# 運算式或陳述式中的運算式相同，它可以包含方法呼叫和其他複雜邏輯。 「傳回值」就是運算式結果。  
  
 若要開始使用 LINQ，您不必廣泛使用 lambda。 不過，只能在方法語法中表示特定查詢，而其中有一部分需要 Lambda 運算式。 當您更熟悉 lambda 之後，您會發現它們在 LINQ 工具箱中是一個功能強大且靈活的工具。 如需詳細資訊，請參閱[Lambda 運算式](../../../language-reference/operators/lambda-expressions.md)。  
  
## <a name="composability-of-queries"></a>查詢的編寫性  
 在上述程式碼範例，請注意，在 `Where` 呼叫上使用點運算子來叫用 `OrderBy` 方法。 `Where` 會產生已篩選的序列，而 `Orderby` 接著會透過排序來運作於該序列。 因為查詢會傳回 `IEnumerable`，所以您可以將方法呼叫鏈結在一起，以在方法語法中撰寫它們。 當您使用查詢語法來撰寫查詢時，這是編譯器在幕後執行的作業。 因為查詢變數不會儲存查詢的結果，所以您隨時都可以修改它，或使用它作為新查詢的基礎，即使已經執行之後也是一樣。  
