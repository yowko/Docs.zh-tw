---
ms.openlocfilehash: 77e04333ed2b9a5ca8b900c1355fb5b12957772d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234642"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="8a6be-101">MachineKey.Encode 和 MachineKey.Decode 方法現在已淘汰</span><span class="sxs-lookup"><span data-stu-id="8a6be-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8a6be-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8a6be-102">Details</span></span>|<span data-ttu-id="8a6be-103">這些方法現在已經過時。</span><span class="sxs-lookup"><span data-stu-id="8a6be-103">These methods are now obsolete.</span></span> <span data-ttu-id="8a6be-104">編譯呼叫這些方法的程式碼會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="8a6be-104">Compilation of code that calls these methods produces a compiler warning.</span></span>|
|<span data-ttu-id="8a6be-105">建議</span><span class="sxs-lookup"><span data-stu-id="8a6be-105">Suggestion</span></span>|<span data-ttu-id="8a6be-106">建議的替代方式為 <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> 和 <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>。</span><span class="sxs-lookup"><span data-stu-id="8a6be-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="8a6be-107">或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。</span><span class="sxs-lookup"><span data-stu-id="8a6be-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="8a6be-108">這些 API 仍受到支援。</span><span class="sxs-lookup"><span data-stu-id="8a6be-108">The APIs are still supported.</span></span>|
|<span data-ttu-id="8a6be-109">範圍</span><span class="sxs-lookup"><span data-stu-id="8a6be-109">Scope</span></span>|<span data-ttu-id="8a6be-110">次要</span><span class="sxs-lookup"><span data-stu-id="8a6be-110">Minor</span></span>|
|<span data-ttu-id="8a6be-111">版本</span><span class="sxs-lookup"><span data-stu-id="8a6be-111">Version</span></span>|<span data-ttu-id="8a6be-112">4.5</span><span class="sxs-lookup"><span data-stu-id="8a6be-112">4.5</span></span>|
|<span data-ttu-id="8a6be-113">類型</span><span class="sxs-lookup"><span data-stu-id="8a6be-113">Type</span></span>|<span data-ttu-id="8a6be-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8a6be-114">Retargeting</span></span>|
|<span data-ttu-id="8a6be-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8a6be-115">Affected APIs</span></span>|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|
