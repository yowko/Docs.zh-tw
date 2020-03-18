---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116370"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="3d82b-101">Microsoft 中的類型.VisualBasic.設備命名空間不可用</span><span class="sxs-lookup"><span data-stu-id="3d82b-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="3d82b-102">命名空間中<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>的類型不可用。</span><span class="sxs-lookup"><span data-stu-id="3d82b-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3d82b-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="3d82b-103">Version introduced</span></span>

<span data-ttu-id="3d82b-104">.NET 核心 3.0 預覽 8</span><span class="sxs-lookup"><span data-stu-id="3d82b-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="3d82b-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="3d82b-105">Change description</span></span>

<span data-ttu-id="3d82b-106">命名空間中<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>的類型在某些 .NET Core 3.0 預覽版本中可用。</span><span class="sxs-lookup"><span data-stu-id="3d82b-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="3d82b-107">它們不再可用，從 .NET 核心 3.0 預覽 9 開始。</span><span class="sxs-lookup"><span data-stu-id="3d82b-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="3d82b-108">已刪除這些類型，以避免不必要的程式集依賴關係或後續版本中的中斷更改。</span><span class="sxs-lookup"><span data-stu-id="3d82b-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3d82b-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3d82b-109">Recommended action</span></span>

<span data-ttu-id="3d82b-110">如果代碼取決於類型及其成員的使用<xref:Microsoft.VisualBasic.Devices>，則可以在 .NET 類庫中使用相應的類型或成員。</span><span class="sxs-lookup"><span data-stu-id="3d82b-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="3d82b-111">例如<xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType>，類的等效功能由<xref:System.DateTime?displayProperty=nameWithType>和<xref:System.Environment?displayProperty=nameWithType>類型提供，並且<xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType>與類的等效功能由命名空間中的<xref:System.IO.Ports?displayProperty=nameWithType>類型提供。</span><span class="sxs-lookup"><span data-stu-id="3d82b-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="3d82b-112">類別</span><span class="sxs-lookup"><span data-stu-id="3d82b-112">Category</span></span>

<span data-ttu-id="3d82b-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d82b-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3d82b-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3d82b-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
