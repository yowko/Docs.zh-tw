---
title: Oracle 分散式異動
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a21134c3283d3d9d8d7660eecaaf74d60ecf6662
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166517"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="f05f6-102">Oracle 分散式異動</span><span class="sxs-lookup"><span data-stu-id="f05f6-102">Oracle Distributed Transactions</span></span>

<span data-ttu-id="f05f6-103">如果 <xref:System.Data.OracleClient.OracleConnection> 物件判定異動處於作用中，便會自動登記在現有的分散式異動中。</span><span class="sxs-lookup"><span data-stu-id="f05f6-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="f05f6-104">當從連接共用開啟或擷取連接時，會發生自動異動登記。</span><span class="sxs-lookup"><span data-stu-id="f05f6-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="f05f6-105">您可以停用現有交易的自動登記功能，方法是指定 </span><span class="sxs-lookup"><span data-stu-id="f05f6-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="f05f6-106">做為 <xref:System.Data.OracleClient.OracleConnection> 的連接字串參數。</span><span class="sxs-lookup"><span data-stu-id="f05f6-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f05f6-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f05f6-107">See also</span></span>

- [<span data-ttu-id="f05f6-108">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f05f6-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- <span data-ttu-id="f05f6-109">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="f05f6-109">[ADO.NET Overview](ado-net-overview.md)</span></span>
