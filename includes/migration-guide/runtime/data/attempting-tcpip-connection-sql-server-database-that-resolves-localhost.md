---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237823"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="1bb4d-101">嘗試建立 TCP/IP 連線至解析為 `localhost` 的 SQL Server 資料庫會失敗</span><span class="sxs-lookup"><span data-stu-id="1bb4d-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1bb4d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1bb4d-102">Details</span></span>|<span data-ttu-id="1bb4d-103">在 .NET Framework 4.6 和 4.6.1 中，嘗試建立 TCP/IP 連線至解析為 <code>localhost</code> 的 SQL Server 資料庫會失敗，錯誤為：「建立連線至 SQL Server 時，發生網路相關或執行個體特定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bb4d-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="1bb4d-104">找不到或無法存取伺服器。</span><span class="sxs-lookup"><span data-stu-id="1bb4d-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="1bb4d-105">確認執行個名稱是否正確，以及 SQL Server 是否設定為允許遠端連線</span><span class="sxs-lookup"><span data-stu-id="1bb4d-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="1bb4d-106">(提供者：SQL 網路介面，錯誤：26 - 尋找指定的伺服器/執行個體時發生錯誤)&quot;</span><span class="sxs-lookup"><span data-stu-id="1bb4d-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>|
|<span data-ttu-id="1bb4d-107">建議</span><span class="sxs-lookup"><span data-stu-id="1bb4d-107">Suggestion</span></span>|<span data-ttu-id="1bb4d-108">在 .NET Framework 4.6.2 中已解決此問題，並還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="1bb4d-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="1bb4d-109">若要連線至解析為 <code>localhost</code> 的 SQL Server 資料庫，請升級至 .NET Framework 4.6.2。</span><span class="sxs-lookup"><span data-stu-id="1bb4d-109">To connect to a SQL Server databsae that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>|
|<span data-ttu-id="1bb4d-110">範圍</span><span class="sxs-lookup"><span data-stu-id="1bb4d-110">Scope</span></span>|<span data-ttu-id="1bb4d-111">次要</span><span class="sxs-lookup"><span data-stu-id="1bb4d-111">Minor</span></span>|
|<span data-ttu-id="1bb4d-112">版本</span><span class="sxs-lookup"><span data-stu-id="1bb4d-112">Version</span></span>|<span data-ttu-id="1bb4d-113">4.6</span><span class="sxs-lookup"><span data-stu-id="1bb4d-113">4.6</span></span>|
|<span data-ttu-id="1bb4d-114">類型</span><span class="sxs-lookup"><span data-stu-id="1bb4d-114">Type</span></span>|<span data-ttu-id="1bb4d-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="1bb4d-115">Runtime</span></span>|
