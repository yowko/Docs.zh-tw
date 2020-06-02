---
title: 從資料庫取得單一值
description: 瞭解如何在 ADO.NET 中傳回單一值。 這個範例程式碼會傳回所插入記錄的識別資料行值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286698"
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="e4862-104">從資料庫取得單一值</span><span class="sxs-lookup"><span data-stu-id="e4862-104">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="e4862-105">或許您需要以單一數值傳回資料庫資訊，而非以資料表或資料流的形式。</span><span class="sxs-lookup"><span data-stu-id="e4862-105">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="e4862-106">例如，您可能會想要傳回匯總函數的結果，例如 COUNT （ \* ）、SUM （Price）或 AVG （Quantity）。</span><span class="sxs-lookup"><span data-stu-id="e4862-106">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="e4862-107">**命令**物件提供使用**ExecuteScalar**方法傳回單一值的功能。</span><span class="sxs-lookup"><span data-stu-id="e4862-107">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="e4862-108">**ExecuteScalar**方法會以純量值傳回結果集中第一個資料列的第一個資料行的值。</span><span class="sxs-lookup"><span data-stu-id="e4862-108">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="e4862-109">下列程式碼範例會使用 <xref:System.Data.SqlClient.SqlCommand>，在資料庫中插入新的值。</span><span class="sxs-lookup"><span data-stu-id="e4862-109">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="e4862-110"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法是用來傳回所插入資料錄的識別資料行值。</span><span class="sxs-lookup"><span data-stu-id="e4862-110">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e4862-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4862-111">See also</span></span>

- [<span data-ttu-id="e4862-112">命令和參數</span><span class="sxs-lookup"><span data-stu-id="e4862-112">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="e4862-113">執行命令</span><span class="sxs-lookup"><span data-stu-id="e4862-113">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="e4862-114">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="e4862-114">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- <span data-ttu-id="e4862-115">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="e4862-115">[ADO.NET Overview](ado-net-overview.md)</span></span>
