---
title: 建立運算式資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 6e19e4e7cc0ea92e9d93e45c2a50d009e46b78c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175496"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="bb75d-102">建立運算式資料行</span><span class="sxs-lookup"><span data-stu-id="bb75d-102">Creating Expression Columns</span></span>
<span data-ttu-id="bb75d-103">您可以定義資料行的運算式，使其包含從相同資料列的其他資料行值，或從資料表的多重資料列的資料行值來計算所得的值。</span><span class="sxs-lookup"><span data-stu-id="bb75d-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="bb75d-104">若要定義要評估的運算式，請使用目標資料行的 <xref:System.Data.DataColumn.Expression%2A> 屬性，並使用 <xref:System.Data.DataColumn.ColumnName%2A> 屬性來參照運算式中的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="bb75d-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="bb75d-105">運算式資料行的 <xref:System.Data.DataColumn.DataType%2A> 必須適用於運算式傳回的值。</span><span class="sxs-lookup"><span data-stu-id="bb75d-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="bb75d-106">下表列出數個資料表的運算式資料行可能使用的方法。</span><span class="sxs-lookup"><span data-stu-id="bb75d-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="bb75d-107">運算式型別</span><span class="sxs-lookup"><span data-stu-id="bb75d-107">Expression type</span></span>|<span data-ttu-id="bb75d-108">範例</span><span class="sxs-lookup"><span data-stu-id="bb75d-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="bb75d-109">邏輯比對</span><span class="sxs-lookup"><span data-stu-id="bb75d-109">Comparison</span></span>|<span data-ttu-id="bb75d-110">「 總 > = 500"</span><span class="sxs-lookup"><span data-stu-id="bb75d-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="bb75d-111">計算</span><span class="sxs-lookup"><span data-stu-id="bb75d-111">Computation</span></span>|<span data-ttu-id="bb75d-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="bb75d-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="bb75d-113">彙總</span><span class="sxs-lookup"><span data-stu-id="bb75d-113">Aggregation</span></span>|<span data-ttu-id="bb75d-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="bb75d-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="bb75d-115">您可以設定**運算式**屬性上的現有**DataColumn**物件，或者您可以包含屬性的第三個引數傳遞至<xref:System.Data.DataColumn>建構函式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bb75d-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="bb75d-116">運算式可參考其他運算式資料行；但循環參考 (兩個運算式互相參考) 將產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bb75d-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="bb75d-117">如需有關撰寫運算式的規則，請參閱<xref:System.Data.DataColumn.Expression%2A>的屬性**DataColumn**類別。</span><span class="sxs-lookup"><span data-stu-id="bb75d-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb75d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb75d-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="bb75d-119">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="bb75d-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="bb75d-120">DataTable</span><span class="sxs-lookup"><span data-stu-id="bb75d-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="bb75d-121">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="bb75d-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
