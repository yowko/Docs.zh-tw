---
ms.openlocfilehash: 958a89015420ce5632d596688963d576c40b4cb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235163"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="385d7-101">與 Asp.Net StateServer 共用工作階段狀態需要 Web 伺服陣列中的所有伺服器使用相同的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="385d7-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="385d7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="385d7-102">Details</span></span>|<span data-ttu-id="385d7-103">啟用 <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> 工作階段狀態時，指定之 Web 伺服陣列中的所有伺服器必須使用相同版本的 .NET Framework，才能正確共用狀態。</span><span class="sxs-lookup"><span data-stu-id="385d7-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>|
|<span data-ttu-id="385d7-104">建議</span><span class="sxs-lookup"><span data-stu-id="385d7-104">Suggestion</span></span>|<span data-ttu-id="385d7-105">請務必將共用狀態之 Web 伺服器上的 .NET Framework 版本同時升級。</span><span class="sxs-lookup"><span data-stu-id="385d7-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>|
|<span data-ttu-id="385d7-106">範圍</span><span class="sxs-lookup"><span data-stu-id="385d7-106">Scope</span></span>|<span data-ttu-id="385d7-107">Edge</span><span class="sxs-lookup"><span data-stu-id="385d7-107">Edge</span></span>|
|<span data-ttu-id="385d7-108">版本</span><span class="sxs-lookup"><span data-stu-id="385d7-108">Version</span></span>|<span data-ttu-id="385d7-109">4.5</span><span class="sxs-lookup"><span data-stu-id="385d7-109">4.5</span></span>|
|<span data-ttu-id="385d7-110">類型</span><span class="sxs-lookup"><span data-stu-id="385d7-110">Type</span></span>|<span data-ttu-id="385d7-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="385d7-111">Runtime</span></span>|
|<span data-ttu-id="385d7-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="385d7-112">Affected APIs</span></span>|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
