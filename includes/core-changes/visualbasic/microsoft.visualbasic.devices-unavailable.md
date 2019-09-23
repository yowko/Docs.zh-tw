---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181766"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="16c53-101">Microsoft 中的類型命名空間無法使用</span><span class="sxs-lookup"><span data-stu-id="16c53-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="16c53-102"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>命名空間中的類型無法使用。</span><span class="sxs-lookup"><span data-stu-id="16c53-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="16c53-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="16c53-103">Version introduced</span></span>

<span data-ttu-id="16c53-104">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="16c53-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="16c53-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="16c53-105">Details</span></span>

<span data-ttu-id="16c53-106"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>命名空間中的類型可在某些 .net Core 3.0 Preview 版本中取得。</span><span class="sxs-lookup"><span data-stu-id="16c53-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="16c53-107">從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。</span><span class="sxs-lookup"><span data-stu-id="16c53-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="16c53-108">已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。</span><span class="sxs-lookup"><span data-stu-id="16c53-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="16c53-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="16c53-109">Recommended action</span></span>

<span data-ttu-id="16c53-110">如果您的程式碼相依于<xref:Microsoft.VisualBasic.Devices>類型及其成員的使用，您可以在 .net 類別庫中使用對應的類型或成員。</span><span class="sxs-lookup"><span data-stu-id="16c53-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="16c53-111">例如<xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> ，類別的對等功能是<xref:System.DateTime?displayProperty=nameWithType>由和<xref:System.Environment?displayProperty=nameWithType>類型提供，而<xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType>類別的對等功能則是由<xref:System.IO.Ports?displayProperty=nameWithType>命名空間中的類型提供。</span><span class="sxs-lookup"><span data-stu-id="16c53-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="16c53-112">分類</span><span class="sxs-lookup"><span data-stu-id="16c53-112">Category</span></span>

<span data-ttu-id="16c53-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16c53-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="16c53-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="16c53-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

