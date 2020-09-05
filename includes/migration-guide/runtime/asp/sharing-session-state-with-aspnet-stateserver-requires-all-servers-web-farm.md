---
ms.openlocfilehash: 76425ca03c98cd6a23b8366257f9e0d53b486edb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496702"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="1f0f9-101">與 Asp.Net StateServer 共用工作階段狀態需要 Web 伺服陣列中的所有伺服器使用相同的 .NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="1f0f9-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="1f0f9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1f0f9-102">Details</span></span>

<span data-ttu-id="1f0f9-103">啟用 <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> 工作階段狀態時，指定之 Web 伺服陣列中的所有伺服器必須使用相同版本的 .NET Framework，才能正確共用狀態。</span><span class="sxs-lookup"><span data-stu-id="1f0f9-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1f0f9-104">建議</span><span class="sxs-lookup"><span data-stu-id="1f0f9-104">Suggestion</span></span>

<span data-ttu-id="1f0f9-105">請務必將共用狀態之 Web 伺服器上的 .NET Framework 版本同時升級。</span><span class="sxs-lookup"><span data-stu-id="1f0f9-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="1f0f9-106">名稱</span><span class="sxs-lookup"><span data-stu-id="1f0f9-106">Name</span></span>    | <span data-ttu-id="1f0f9-107">值</span><span class="sxs-lookup"><span data-stu-id="1f0f9-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1f0f9-108">範圍</span><span class="sxs-lookup"><span data-stu-id="1f0f9-108">Scope</span></span>   |<span data-ttu-id="1f0f9-109">Edge</span><span class="sxs-lookup"><span data-stu-id="1f0f9-109">Edge</span></span>|
|<span data-ttu-id="1f0f9-110">版本</span><span class="sxs-lookup"><span data-stu-id="1f0f9-110">Version</span></span>|<span data-ttu-id="1f0f9-111">4.5</span><span class="sxs-lookup"><span data-stu-id="1f0f9-111">4.5</span></span>|
|<span data-ttu-id="1f0f9-112">類型</span><span class="sxs-lookup"><span data-stu-id="1f0f9-112">Type</span></span>|<span data-ttu-id="1f0f9-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="1f0f9-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f0f9-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1f0f9-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
