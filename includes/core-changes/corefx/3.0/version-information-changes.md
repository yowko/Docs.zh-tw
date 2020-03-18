---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344437"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="e67f1-101">報表版本的 API 現在報告產品，而不是檔版本</span><span class="sxs-lookup"><span data-stu-id="e67f1-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="e67f1-102">返回 .NET Core 中版本的許多 API 現在返回產品版本，而不是檔版本。</span><span class="sxs-lookup"><span data-stu-id="e67f1-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e67f1-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="e67f1-103">Change description</span></span>

<span data-ttu-id="e67f1-104">在 .NET Core 2.2 和早期版本中<xref:System.Environment.Version?displayProperty=nameWithType>，<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>方法（如 .NET Core 程式集的檔案屬性對話方塊）反映檔版本。</span><span class="sxs-lookup"><span data-stu-id="e67f1-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="e67f1-105">從 .NET Core 3.0 開始，它們反映了產品版本。</span><span class="sxs-lookup"><span data-stu-id="e67f1-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="e67f1-106">下圖說明瞭 Windows**資源管理器**檔案屬性對話方塊顯示的*System.Runtime.dll*.NET Core 2.2（左側）和 .NET Core 3.0（右側）的版本資訊差異。</span><span class="sxs-lookup"><span data-stu-id="e67f1-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="e67f1-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="e67f1-108">Version introduced</span></span>

<span data-ttu-id="e67f1-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e67f1-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e67f1-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e67f1-110">Recommended action</span></span>

<span data-ttu-id="e67f1-111">無。</span><span class="sxs-lookup"><span data-stu-id="e67f1-111">None.</span></span> <span data-ttu-id="e67f1-112">此更改應使版本檢測直觀，而不是過時。</span><span class="sxs-lookup"><span data-stu-id="e67f1-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="e67f1-113">類別</span><span class="sxs-lookup"><span data-stu-id="e67f1-113">Category</span></span>

<span data-ttu-id="e67f1-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="e67f1-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e67f1-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e67f1-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
