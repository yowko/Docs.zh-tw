---
title: 風險降低：集區封鎖期
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01bd548bbafda34202705dda3dda148aae941e2b
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251105"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="b23f8-102">風險降低：集區封鎖期</span><span class="sxs-lookup"><span data-stu-id="b23f8-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="b23f8-103">已移除 Azure SQL Database 連線的連線集區封鎖期。</span><span class="sxs-lookup"><span data-stu-id="b23f8-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="b23f8-104">其他描述</span><span class="sxs-lookup"><span data-stu-id="b23f8-104">Additional description</span></span>  
 <span data-ttu-id="b23f8-105">在 .NET Framework 4.6.1 和舊版中，如果應用程式在連線到資料庫時發生暫時性連線失敗，由於連線集區會快取此錯誤並在 5 秒鐘到 1 分鐘後重新擲回，因此無法很快就重試連線。如需詳細資訊，請參閱 [SQL Server 連線共用 (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="b23f8-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="b23f8-106">此行為會對 Azure SQL Database 連線造成問題，連線通常會因暫時性錯誤而失敗，而且一般會在幾秒內復原。</span><span class="sxs-lookup"><span data-stu-id="b23f8-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="b23f8-107">連線集區封鎖功能表示應用程式有很長的一段時間無法連線到資料庫，即使資料庫可供使用也一樣。</span><span class="sxs-lookup"><span data-stu-id="b23f8-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="b23f8-108">此行為特別會對連線到 Azure SQL Database 且需要在幾秒內轉譯的 Web 應用程式造成問題。</span><span class="sxs-lookup"><span data-stu-id="b23f8-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="b23f8-109">從 .NET Framework 4.6.2 開始，針對已知 Azure SQL Database (\*.database.windows.net、\*.database.chinacloudapi.cn、\*.database.usgovcloudapi.net、\*.database.cloudapi.de) 的連線開啟要求，不會快取連線開啟錯誤。</span><span class="sxs-lookup"><span data-stu-id="b23f8-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="b23f8-110">至於所有其他連線嘗試，則會繼續強制執行連線集區封鎖期。</span><span class="sxs-lookup"><span data-stu-id="b23f8-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b23f8-111">影響</span><span class="sxs-lookup"><span data-stu-id="b23f8-111">Impact</span></span>  
 <span data-ttu-id="b23f8-112">這項變更允許立即重試 Azure SQL Database 的連線開啟嘗試，因而提升啟用雲端功能的應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="b23f8-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b23f8-113">緩和</span><span class="sxs-lookup"><span data-stu-id="b23f8-113">Mitigation</span></span>  
 <span data-ttu-id="b23f8-114">如果這項變更會對應用程式造成負面影響，可以藉由設定新的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> 屬性，來設定連線集區封鎖期。</span><span class="sxs-lookup"><span data-stu-id="b23f8-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="b23f8-115">屬性的值是 <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> 列舉的成員，可以採用三個值的其中一個值︰</span><span class="sxs-lookup"><span data-stu-id="b23f8-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="b23f8-116">將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> 屬性設為 <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType> 可以還原舊有行為。</span><span class="sxs-lookup"><span data-stu-id="b23f8-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b23f8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b23f8-117">See also</span></span>

- [<span data-ttu-id="b23f8-118">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="b23f8-118">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
