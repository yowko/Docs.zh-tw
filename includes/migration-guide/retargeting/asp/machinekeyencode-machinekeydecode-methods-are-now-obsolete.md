---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617136"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="c0ff9-101">MachineKey.Encode 和 MachineKey.Decode 方法現在已淘汰</span><span class="sxs-lookup"><span data-stu-id="c0ff9-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="c0ff9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c0ff9-102">Details</span></span>

<span data-ttu-id="c0ff9-103">這些方法現在已經過時。</span><span class="sxs-lookup"><span data-stu-id="c0ff9-103">These methods are now obsolete.</span></span> <span data-ttu-id="c0ff9-104">編譯呼叫這些方法的程式碼會產生編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="c0ff9-104">Compilation of code that calls these methods produces a compiler warning.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c0ff9-105">建議</span><span class="sxs-lookup"><span data-stu-id="c0ff9-105">Suggestion</span></span>

<span data-ttu-id="c0ff9-106">建議的替代方式為 <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> 和 <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>。</span><span class="sxs-lookup"><span data-stu-id="c0ff9-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="c0ff9-107">或者，您也可以隱藏建置警告，或使用舊版編譯器以避免出現警告。</span><span class="sxs-lookup"><span data-stu-id="c0ff9-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="c0ff9-108">這些 API 仍受到支援。</span><span class="sxs-lookup"><span data-stu-id="c0ff9-108">The APIs are still supported.</span></span>

| <span data-ttu-id="c0ff9-109">名稱</span><span class="sxs-lookup"><span data-stu-id="c0ff9-109">Name</span></span>    | <span data-ttu-id="c0ff9-110">值</span><span class="sxs-lookup"><span data-stu-id="c0ff9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c0ff9-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="c0ff9-111">Scope</span></span>   | <span data-ttu-id="c0ff9-112">Minor</span><span class="sxs-lookup"><span data-stu-id="c0ff9-112">Minor</span></span>       |
| <span data-ttu-id="c0ff9-113">版本</span><span class="sxs-lookup"><span data-stu-id="c0ff9-113">Version</span></span> | <span data-ttu-id="c0ff9-114">4.5</span><span class="sxs-lookup"><span data-stu-id="c0ff9-114">4.5</span></span>         |
| <span data-ttu-id="c0ff9-115">類型</span><span class="sxs-lookup"><span data-stu-id="c0ff9-115">Type</span></span>    | <span data-ttu-id="c0ff9-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="c0ff9-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c0ff9-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c0ff9-117">Affected APIs</span></span>

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
