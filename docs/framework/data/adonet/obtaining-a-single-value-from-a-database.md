---
title: 從資料庫取得單一值
description: 瞭解如何在 ADO.NET 中傳回單一值。 此範例程式碼會傳回所插入記錄的識別資料行值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 9ce29bc1321814bd60cfaacd222fc55a3fbf12ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150722"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="8a62f-104">從資料庫取得單一值</span><span class="sxs-lookup"><span data-stu-id="8a62f-104">Obtaining a Single Value from a Database</span></span>

<span data-ttu-id="8a62f-105">或許您需要以單一數值傳回資料庫資訊，而非以資料表或資料流的形式。</span><span class="sxs-lookup"><span data-stu-id="8a62f-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="8a62f-106">例如，您可能想要傳回彙總函式的結果，例如 COUNT (\*) 、SUM (Price) 或 AVG (Quantity) 。</span><span class="sxs-lookup"><span data-stu-id="8a62f-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="8a62f-107">**命令**物件提供使用**ExecuteScalar**方法傳回單一值的功能。</span><span class="sxs-lookup"><span data-stu-id="8a62f-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="8a62f-108">**ExecuteScalar**方法會以純量值形式傳回結果集第一個資料列的第一個資料行值。</span><span class="sxs-lookup"><span data-stu-id="8a62f-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="8a62f-109">下列程式碼範例會使用 <xref:System.Data.SqlClient.SqlCommand>，在資料庫中插入新的值。</span><span class="sxs-lookup"><span data-stu-id="8a62f-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="8a62f-110"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法是用來傳回所插入資料錄的識別資料行值。</span><span class="sxs-lookup"><span data-stu-id="8a62f-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8a62f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a62f-111">See also</span></span>

- [<span data-ttu-id="8a62f-112">命令和參數</span><span class="sxs-lookup"><span data-stu-id="8a62f-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="8a62f-113">執行命令</span><span class="sxs-lookup"><span data-stu-id="8a62f-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="8a62f-114">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="8a62f-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- <span data-ttu-id="8a62f-115">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="8a62f-115">[ADO.NET Overview](ado-net-overview.md)</span></span>
