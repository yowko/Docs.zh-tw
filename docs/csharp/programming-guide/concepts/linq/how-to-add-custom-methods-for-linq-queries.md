---
title: '如何新增 LINQ 查詢的自訂方法 (c # ) '
description: '瞭解如何 <T> 在 c # 中將擴充方法加入至 IEnumerable 介面，以擴充 LINQ 查詢的語法。'
ms.date: 08/26/2020
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 768882fce40a2fc6e018f24c8928341e7c65bc4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122421"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>如何新增 LINQ 查詢的自訂方法 (c # ) 

您可以藉由將擴充方法加入至介面，來擴充您用於 LINQ 查詢的方法集合 <xref:System.Collections.Generic.IEnumerable%601> 。 例如，除了標準平均或最大作業之外，您還可以建立自訂匯總方法來計算值序列中的單一值。 您也會建立一個方法，以做為自訂篩選或一系列值的特定資料轉換，並傳回新的序列。 這類方法的範例包括 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A>。

當您延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面時，可將自訂方法套用至任何可列舉的集合。 如需詳細資訊，請參閱[擴充方法](../../classes-and-structs/extension-methods.md)。

## <a name="adding-an-aggregate-method"></a>新增匯總方法

彙總方法會計算一組值的單一值。 LINQ 提供數種彙總方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。 您可將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，建立自己的彙總方法。

下列程式碼範例示範如何建立呼叫 `Median` 的擴充方法，來計算一系列類型為 `double` 的中位數。

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="LinqExtensionClass":::

您可以使用從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他彙總方法同樣的方式，為任何可列舉集合呼叫此擴充方法。

下列程式碼範例示範如何使用 `Median` 方法處理 `double` 類型的陣列。

:::code language="csharp" source="./snippets/Program.cs" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>多載彙總方法以接受各種類型

您可以多載自己的彙總方法，讓它接受各種類型的序列。 標準方法是為每種類型建立多載。 另一種方法是建立採用泛型型別的多載，使用委派將它轉換成特定的類型。 您也可以結合這兩種方法。

#### <a name="to-create-an-overload-for-each-type"></a>為每種類型建立多載

您可以為想要支援的每種類型建立特定的多載。 下列程式碼範例示範適合 `int` 類型之 `Median` 方法的多載。

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="IntOverload":::

您現在可以呼叫 `integer` 和 `double` 類型的 `Median` 多載，如下列程式碼所示︰

:::code language="csharp" source="./snippets/Program.cs" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a>建立一般多載

您也可以建立接受一系列泛型物件的多載。 這個多載會接受委派作為參數，並使用它將泛型型別物件的序列轉換成特定的類型。

下列程式碼顯示 `Median` 方法的多載，接受 <xref:System.Func%602> 委派為參數。 這個委派會接受泛型型別 T 的物件，並傳回 `double` 類型的物件。

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="GenericOverload":::

您現在可以針對一系列的類型物件呼叫 `Median` 方法。 如果類型沒有自己的方法多載，則您必須傳遞委派參數。 在 C# 中，您可以針對此目的使用 Lambda 運算式。 另僅限 Visual Basic，如果您使用 `Aggregate` 或 `Group By` 子句而不是方法呼叫，您可以傳遞此子句範圍內的任何值或運算式。

下列程式碼範例示範如何呼叫 `Median` 方法，處理整數陣列及字串陣列。 針對字串，會計算陣列字串長度的中間值。 此範例會示範如何將 <xref:System.Func%602> 委派參數傳遞至每個案例的 `Median` 方法。

:::code language="csharp" source="./snippets/Program.cs" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-sequence"></a>加入傳回序列的方法

您可以使用傳回一系列值的自訂查詢方法來延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面。 在此情況下，方法必須傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的集合。 此等方法可用來將篩選條件或資料轉換套用至一系列的值。

下例示範如何建立名為 `AlternateElements` 的擴充方法，傳回集合中的每隔個項目，從第一個項目開始。

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="SequenceElement":::

您可為任何可列舉集合呼叫此擴充方法，就和您從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他方法一樣，如下列程式碼所示：

:::code language="csharp" source="./snippets/Program.cs" ID="SequenceUsage":::

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.IEnumerable%601>
- [擴充方法](../../classes-and-structs/extension-methods.md)
