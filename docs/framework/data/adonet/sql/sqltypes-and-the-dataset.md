---
title: SqlTypes 和資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: a218a8e0fe3d2c17a0f09a40645c7b3ad26fb5ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072697"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="f8d96-102">SqlTypes 和資料集</span><span class="sxs-lookup"><span data-stu-id="f8d96-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="f8d96-103">ADO.NET 2.0 透過 `DataSet` 命名空間 (Namespace) 導入了 <xref:System.Data.SqlTypes> 的增強型別支援。</span><span class="sxs-lookup"><span data-stu-id="f8d96-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="f8d96-104"><xref:System.Data.SqlTypes> 中型別的設計目的是要提供與 SQL Server 資料庫中的資料型別具有相同語意 (Semantics) 及精確度的資料型別。</span><span class="sxs-lookup"><span data-stu-id="f8d96-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="f8d96-105"><xref:System.Data.SqlTypes> 中的每個資料型別，在 SQL Server 中都具有對應的資料型別，並且具有相同的基礎資料表示。</span><span class="sxs-lookup"><span data-stu-id="f8d96-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="f8d96-106">使用 SQL Server 資料型別時，若在 <xref:System.Data.SqlTypes> 中直接使用 <xref:System.Data.DataSet> 會有一些優點。</span><span class="sxs-lookup"><span data-stu-id="f8d96-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="f8d96-107"><xref:System.Data.SqlTypes> 與 SQL Server 原生資料型別支援相同的語意。</span><span class="sxs-lookup"><span data-stu-id="f8d96-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="f8d96-108">在 <xref:System.Data.SqlTypes> 的定義中指定其中一個 <xref:System.Data.DataColumn> 可避免將 decimal 或 numeric 資料型別轉換成其中一種 Common Language Runtime (CLR) 資料型別時可能會發生的精確度遺失。</span><span class="sxs-lookup"><span data-stu-id="f8d96-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8d96-109">範例</span><span class="sxs-lookup"><span data-stu-id="f8d96-109">Example</span></span>  
 <span data-ttu-id="f8d96-110">下列範例會建立 <xref:System.Data.DataTable> 物件，它會使用 <xref:System.Data.DataColumn> 而非 CLR 型別來明確定義 <xref:System.Data.SqlTypes> 資料型別。</span><span class="sxs-lookup"><span data-stu-id="f8d96-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="f8d96-111">該程式碼會將 SQL Server 中 AdventureWorks 資料庫內 Sales.SalesOrderDetail 資料表的資料，填入 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="f8d96-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="f8d96-112">出現在主控台視窗中的輸出顯示每個資料行的資料型別，以及從 SQL Server 擷取出來的值。</span><span class="sxs-lookup"><span data-stu-id="f8d96-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f8d96-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8d96-113">See also</span></span>

- [<span data-ttu-id="f8d96-114">SQL Server 資料類型對應</span><span class="sxs-lookup"><span data-stu-id="f8d96-114">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="f8d96-115">設定參數和參數資料類型</span><span class="sxs-lookup"><span data-stu-id="f8d96-115">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="f8d96-116">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="f8d96-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
