---
title: "建立運算式資料行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c1b0b7be8be6bec0c5a8850029bd3336d107f0a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-expression-columns"></a><span data-ttu-id="9b04e-102">建立運算式資料行</span><span class="sxs-lookup"><span data-stu-id="9b04e-102">Creating Expression Columns</span></span>
<span data-ttu-id="9b04e-103">您可以定義資料行的運算式，使其包含從相同資料列的其他資料行值，或從資料表的多重資料列的資料行值來計算所得的值。</span><span class="sxs-lookup"><span data-stu-id="9b04e-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="9b04e-104">若要定義要評估的運算式，請使用目標資料行的 <xref:System.Data.DataColumn.Expression%2A> 屬性，並使用 <xref:System.Data.DataColumn.ColumnName%2A> 屬性來參照運算式中的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="9b04e-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="9b04e-105">運算式資料行的 <xref:System.Data.DataColumn.DataType%2A> 必須適用於運算式傳回的值。</span><span class="sxs-lookup"><span data-stu-id="9b04e-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="9b04e-106">下表列出數個資料表的運算式資料行可能使用的方法。</span><span class="sxs-lookup"><span data-stu-id="9b04e-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="9b04e-107">運算式型別</span><span class="sxs-lookup"><span data-stu-id="9b04e-107">Expression type</span></span>|<span data-ttu-id="9b04e-108">範例</span><span class="sxs-lookup"><span data-stu-id="9b04e-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="9b04e-109">比較</span><span class="sxs-lookup"><span data-stu-id="9b04e-109">Comparison</span></span>|<span data-ttu-id="9b04e-110">"Total >= 500"</span><span class="sxs-lookup"><span data-stu-id="9b04e-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="9b04e-111">計算</span><span class="sxs-lookup"><span data-stu-id="9b04e-111">Computation</span></span>|<span data-ttu-id="9b04e-112">"UnitPrice * Quantity"</span><span class="sxs-lookup"><span data-stu-id="9b04e-112">"UnitPrice * Quantity"</span></span>|  
|<span data-ttu-id="9b04e-113">彙總</span><span class="sxs-lookup"><span data-stu-id="9b04e-113">Aggregation</span></span>|<span data-ttu-id="9b04e-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="9b04e-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="9b04e-115">您可以設定**運算式**屬性上的現有**DataColumn**物件，或者您可以包含屬性做為第三個引數傳遞給<xref:System.Data.DataColumn>建構函式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="9b04e-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="9b04e-116">運算式可參考其他運算式資料行；但循環參考 (兩個運算式互相參考) 將產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9b04e-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="9b04e-117">如需有關撰寫運算式的規則，請參閱<xref:System.Data.DataColumn.Expression%2A>屬性**DataColumn**類別。</span><span class="sxs-lookup"><span data-stu-id="9b04e-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b04e-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b04e-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="9b04e-119">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="9b04e-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="9b04e-120">DataTable</span><span class="sxs-lookup"><span data-stu-id="9b04e-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="9b04e-121">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="9b04e-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
