---
ms.openlocfilehash: 2a751acc129ebd1c917b87f8083ffef72c7d8c17
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568080"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="ba602-101">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="ba602-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="ba602-102">許多在 .NET Core 中傳回版本的 Api 現在都會傳回產品版本，而不是檔案版本。</span><span class="sxs-lookup"><span data-stu-id="ba602-102">Many of the APIs that return versions in .NET Core now returned the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ba602-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ba602-103">Change description</span></span>

<span data-ttu-id="ba602-104">在 .NET Core 2.2 和舊版中，.NET Core 元件之類的方法（例如 <xref:System.Environment.Version?displayProperty=nameWithType>、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>和 [檔案屬性] 對話方塊）會反映檔案版本。</span><span class="sxs-lookup"><span data-stu-id="ba602-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="ba602-105">從 .NET Core 3.0 開始，它們會反映產品版本。</span><span class="sxs-lookup"><span data-stu-id="ba602-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="ba602-106">下圖說明 .NET Core 2.2 （左側）和 .NET Core 3.0 （位於右邊）的*system.webserver*元件版本資訊差異，如**Windows Explorer** [檔案屬性] 對話方塊所顯示。</span><span class="sxs-lookup"><span data-stu-id="ba602-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="ba602-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ba602-108">Version introduced</span></span>

<span data-ttu-id="ba602-109">3.0</span><span class="sxs-lookup"><span data-stu-id="ba602-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ba602-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ba602-110">Recommended action</span></span>

<span data-ttu-id="ba602-111">無。</span><span class="sxs-lookup"><span data-stu-id="ba602-111">None.</span></span> <span data-ttu-id="ba602-112">這種變更應該可以直覺而不是簡直遲鈍進行版本偵測。</span><span class="sxs-lookup"><span data-stu-id="ba602-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="ba602-113">Category</span><span class="sxs-lookup"><span data-stu-id="ba602-113">Category</span></span>

<span data-ttu-id="ba602-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ba602-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ba602-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ba602-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
