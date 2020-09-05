---
ms.openlocfilehash: 26539011f0650c7a3bac9e1c41847561905fff58
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496714"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="9a25f-101">.NET Framework 1.1 和 2.0 的受控瀏覽器裝載控制項已封鎖</span><span class="sxs-lookup"><span data-stu-id="9a25f-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="9a25f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9a25f-102">Details</span></span>

<span data-ttu-id="9a25f-103">Internet Explorer 中已封鎖裝載這些控制項。</span><span class="sxs-lookup"><span data-stu-id="9a25f-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9a25f-104">建議</span><span class="sxs-lookup"><span data-stu-id="9a25f-104">Suggestion</span></span>

<span data-ttu-id="9a25f-105">Internet Explorer 將無法啟動使用 Managed 瀏覽器裝載控制項的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9a25f-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="9a25f-106">可還原先前行為的方式包括：在 x86 系統和 x64 系統的 32 位元處理序上，將登錄子機碼 <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> 的 EnableIEHosting 值設為 <code>1</code>，在 x64 系統的 64 位元處理序上，將登錄子機碼 <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> 的 <code>EnableIEHosting</code> 值設為 <code>1</code>。</span><span class="sxs-lookup"><span data-stu-id="9a25f-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="9a25f-107">名稱</span><span class="sxs-lookup"><span data-stu-id="9a25f-107">Name</span></span>    | <span data-ttu-id="9a25f-108">值</span><span class="sxs-lookup"><span data-stu-id="9a25f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9a25f-109">範圍</span><span class="sxs-lookup"><span data-stu-id="9a25f-109">Scope</span></span>   |<span data-ttu-id="9a25f-110">Minor</span><span class="sxs-lookup"><span data-stu-id="9a25f-110">Minor</span></span>|
|<span data-ttu-id="9a25f-111">版本</span><span class="sxs-lookup"><span data-stu-id="9a25f-111">Version</span></span>|<span data-ttu-id="9a25f-112">4.5</span><span class="sxs-lookup"><span data-stu-id="9a25f-112">4.5</span></span>|
|<span data-ttu-id="9a25f-113">類型</span><span class="sxs-lookup"><span data-stu-id="9a25f-113">Type</span></span>|<span data-ttu-id="9a25f-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="9a25f-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="9a25f-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9a25f-115">Affected APIs</span></span>

<span data-ttu-id="9a25f-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="9a25f-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
