---
title: Oracle 分散式異動
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a3b8a50b42b945a0cdc1cbfbc4cc9eab835e90e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505395"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="e36f0-102">Oracle 分散式異動</span><span class="sxs-lookup"><span data-stu-id="e36f0-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="e36f0-103">如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定交易處於作用中，便會自動登記在現有的分散式交易中。</span><span class="sxs-lookup"><span data-stu-id="e36f0-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="e36f0-104">當從連接共用開啟或擷取連接時，會發生自動交易登記。</span><span class="sxs-lookup"><span data-stu-id="e36f0-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="e36f0-105">您可以停用現有交易的自動登記功能，方法是指定 </span><span class="sxs-lookup"><span data-stu-id="e36f0-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="e36f0-106">做為 <xref:System.Data.OracleClient.OracleConnection> 的連接字串參數。</span><span class="sxs-lookup"><span data-stu-id="e36f0-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e36f0-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e36f0-107">See Also</span></span>  
 [<span data-ttu-id="e36f0-108">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e36f0-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="e36f0-109">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e36f0-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
