---
title: 從資料庫取得單一值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794744"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="b0e2a-102">從資料庫取得單一值</span><span class="sxs-lookup"><span data-stu-id="b0e2a-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="b0e2a-103">或許您需要以單一數值傳回資料庫資訊，而非以資料表或資料流的形式。</span><span class="sxs-lookup"><span data-stu-id="b0e2a-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="b0e2a-104">例如，您可能會想要傳回匯總函數的結果，例如 COUNT （\*）、SUM （Price）或 AVG （Quantity）。</span><span class="sxs-lookup"><span data-stu-id="b0e2a-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="b0e2a-105">**命令**物件提供使用**ExecuteScalar**方法傳回單一值的功能。</span><span class="sxs-lookup"><span data-stu-id="b0e2a-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="b0e2a-106">**ExecuteScalar**方法會以純量值傳回結果集中第一個資料列的第一個資料行的值。</span><span class="sxs-lookup"><span data-stu-id="b0e2a-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="b0e2a-107">下列程式碼範例會使用 <xref:System.Data.SqlClient.SqlCommand>，在資料庫中插入新的值。</span><span class="sxs-lookup"><span data-stu-id="b0e2a-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="b0e2a-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法是用來傳回所插入資料錄的識別資料行值。</span><span class="sxs-lookup"><span data-stu-id="b0e2a-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b0e2a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e2a-109">See also</span></span>

- [<span data-ttu-id="b0e2a-110">命令和參數</span><span class="sxs-lookup"><span data-stu-id="b0e2a-110">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b0e2a-111">執行命令</span><span class="sxs-lookup"><span data-stu-id="b0e2a-111">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="b0e2a-112">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="b0e2a-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="b0e2a-113">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="b0e2a-113">ADO.NET Overview</span></span>](ado-net-overview.md)
