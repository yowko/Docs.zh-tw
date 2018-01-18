---
title: "從資料庫取得單一值"
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
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 41c3547d203a9958d3ad84303469c1e9591e6bd3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="75b99-102">從資料庫取得單一值</span><span class="sxs-lookup"><span data-stu-id="75b99-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="75b99-103">或許您需要以單一數值傳回資料庫資訊，而非以資料表或資料流的形式。</span><span class="sxs-lookup"><span data-stu-id="75b99-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="75b99-104">比方說，您可能想要傳回的結果，例如計數彙總函式 (\\*)、 sum (price) 或 AVG(Quantity)。</span><span class="sxs-lookup"><span data-stu-id="75b99-104">For example, you may want to return the result of an aggregate function such as COUNT(\\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="75b99-105">**命令**物件可讓您傳回單一值使用**ExecuteScalar**方法。</span><span class="sxs-lookup"><span data-stu-id="75b99-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="75b99-106">**ExecuteScalar**方法傳回時，做為純量值，結果集的第一個資料列的第一個資料行的值。</span><span class="sxs-lookup"><span data-stu-id="75b99-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="75b99-107">下列程式碼範例會使用 <xref:System.Data.SqlClient.SqlCommand>，在資料庫中插入新的值。</span><span class="sxs-lookup"><span data-stu-id="75b99-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="75b99-108"><xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> 方法是用來傳回所插入資料錄的識別資料行值。</span><span class="sxs-lookup"><span data-stu-id="75b99-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="75b99-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="75b99-109">See Also</span></span>  
 [<span data-ttu-id="75b99-110">命令和參數</span><span class="sxs-lookup"><span data-stu-id="75b99-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="75b99-111">執行命令</span><span class="sxs-lookup"><span data-stu-id="75b99-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="75b99-112">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="75b99-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="75b99-113">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="75b99-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
