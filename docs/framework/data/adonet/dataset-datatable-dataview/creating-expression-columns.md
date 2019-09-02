---
title: 建立運算式資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 8ae8c8e020a3d8ada5bdcd5037187e6f3abd33a4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203844"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="ff2c4-102">建立運算式資料行</span><span class="sxs-lookup"><span data-stu-id="ff2c4-102">Creating Expression Columns</span></span>
<span data-ttu-id="ff2c4-103">您可以定義資料行的運算式，使其包含從相同資料列的其他資料行值，或從資料表的多重資料列的資料行值來計算所得的值。</span><span class="sxs-lookup"><span data-stu-id="ff2c4-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="ff2c4-104">若要定義要評估的運算式，請使用目標資料行的 <xref:System.Data.DataColumn.Expression%2A> 屬性，並使用 <xref:System.Data.DataColumn.ColumnName%2A> 屬性來參照運算式中的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="ff2c4-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="ff2c4-105">運算式資料行的 <xref:System.Data.DataColumn.DataType%2A> 必須適用於運算式傳回的值。</span><span class="sxs-lookup"><span data-stu-id="ff2c4-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="ff2c4-106">下表列出數個資料表的運算式資料行可能使用的方法。</span><span class="sxs-lookup"><span data-stu-id="ff2c4-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="ff2c4-107">運算式型別</span><span class="sxs-lookup"><span data-stu-id="ff2c4-107">Expression type</span></span>|<span data-ttu-id="ff2c4-108">範例</span><span class="sxs-lookup"><span data-stu-id="ff2c4-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="ff2c4-109">邏輯比對</span><span class="sxs-lookup"><span data-stu-id="ff2c4-109">Comparison</span></span>|<span data-ttu-id="ff2c4-110">"Total > = 500"</span><span class="sxs-lookup"><span data-stu-id="ff2c4-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="ff2c4-111">計算</span><span class="sxs-lookup"><span data-stu-id="ff2c4-111">Computation</span></span>|<span data-ttu-id="ff2c4-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="ff2c4-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="ff2c4-113">彙總</span><span class="sxs-lookup"><span data-stu-id="ff2c4-113">Aggregation</span></span>|<span data-ttu-id="ff2c4-114">Sum(Price)</span><span class="sxs-lookup"><span data-stu-id="ff2c4-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="ff2c4-115">您可以在現有的**DataColumn**物件上設定<xref:System.Data.DataColumn> **Expression**屬性, 也可以將屬性包含為傳遞給此函式的第三個引數, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ff2c4-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="ff2c4-116">運算式可參考其他運算式資料行；但循環參考 (兩個運算式互相參考) 將產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff2c4-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="ff2c4-117">如需撰寫運算式的相關規則, <xref:System.Data.DataColumn.Expression%2A>請參閱**DataColumn**類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="ff2c4-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2c4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff2c4-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="ff2c4-119">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="ff2c4-119">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="ff2c4-120">DataTable</span><span class="sxs-lookup"><span data-stu-id="ff2c4-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="ff2c4-121">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="ff2c4-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
