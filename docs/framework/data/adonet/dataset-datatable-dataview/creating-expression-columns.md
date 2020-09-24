---
title: 建立運算式資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: ad14e4d3d6a1107f994d9536485257f9dc1851f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166842"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="0c0cb-102">建立運算式資料行</span><span class="sxs-lookup"><span data-stu-id="0c0cb-102">Creating Expression Columns</span></span>

<span data-ttu-id="0c0cb-103">您可以定義資料行的運算式，使其包含從相同資料列的其他資料行值，或從資料表的多重資料列的資料行值來計算所得的值。</span><span class="sxs-lookup"><span data-stu-id="0c0cb-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="0c0cb-104">若要定義要評估的運算式，請使用目標資料行的 <xref:System.Data.DataColumn.Expression%2A> 屬性，並使用 <xref:System.Data.DataColumn.ColumnName%2A> 屬性來參照運算式中的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="0c0cb-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="0c0cb-105">運算式資料行的 <xref:System.Data.DataColumn.DataType%2A> 必須適用於運算式傳回的值。</span><span class="sxs-lookup"><span data-stu-id="0c0cb-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="0c0cb-106">下表列出數個資料表的運算式資料行可能使用的方法。</span><span class="sxs-lookup"><span data-stu-id="0c0cb-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="0c0cb-107">運算式型別</span><span class="sxs-lookup"><span data-stu-id="0c0cb-107">Expression type</span></span>|<span data-ttu-id="0c0cb-108">範例</span><span class="sxs-lookup"><span data-stu-id="0c0cb-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="0c0cb-109">比較</span><span class="sxs-lookup"><span data-stu-id="0c0cb-109">Comparison</span></span>|<span data-ttu-id="0c0cb-110">"Total >= 500"</span><span class="sxs-lookup"><span data-stu-id="0c0cb-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="0c0cb-111">計算</span><span class="sxs-lookup"><span data-stu-id="0c0cb-111">Computation</span></span>|<span data-ttu-id="0c0cb-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="0c0cb-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="0c0cb-113">彙總</span><span class="sxs-lookup"><span data-stu-id="0c0cb-113">Aggregation</span></span>|<span data-ttu-id="0c0cb-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="0c0cb-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="0c0cb-115">您可以在現有的**DataColumn**物件上設定**Expression**屬性，也可以包含屬性做為傳遞給函式的第三個引數 <xref:System.Data.DataColumn> ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0c0cb-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="0c0cb-116">運算式可參考其他運算式資料行；但循環參考 (兩個運算式互相參考) 將產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0c0cb-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="0c0cb-117">如需撰寫運算式的規則，請參閱 <xref:System.Data.DataColumn.Expression%2A> **DataColumn** 類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="0c0cb-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0cb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c0cb-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="0c0cb-119">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="0c0cb-119">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="0c0cb-120">DataTables</span><span class="sxs-lookup"><span data-stu-id="0c0cb-120">DataTables</span></span>](datatables.md)
- <span data-ttu-id="0c0cb-121">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0c0cb-121">[ADO.NET Overview](../ado-net-overview.md)</span></span>
