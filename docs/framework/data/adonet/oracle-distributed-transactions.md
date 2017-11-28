---
title: "Oracle 分散式異動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c48232bb204b71c662a99bf210ad54fc3ee9eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="61f49-102">Oracle 分散式異動</span><span class="sxs-lookup"><span data-stu-id="61f49-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="61f49-103">如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定交易處於作用中，便會自動登記在現有的分散式交易中。</span><span class="sxs-lookup"><span data-stu-id="61f49-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="61f49-104">當從連接共用開啟或擷取連接時，會發生自動交易登記。</span><span class="sxs-lookup"><span data-stu-id="61f49-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="61f49-105">您可以停用現有交易的自動登記功能，方法是指定 </span><span class="sxs-lookup"><span data-stu-id="61f49-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="61f49-106">做為 <xref:System.Data.OracleClient.OracleConnection> 的連接字串參數。</span><span class="sxs-lookup"><span data-stu-id="61f49-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f49-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61f49-107">See Also</span></span>  
 [<span data-ttu-id="61f49-108">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="61f49-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="61f49-109">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="61f49-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
