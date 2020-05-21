---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721049"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="8373d-101">報告版本的 Api 現在會報告產品，而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="8373d-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="8373d-102">許多傳回 .NET Core 版本的 Api 現在會傳回產品版本，而不是檔案版本。</span><span class="sxs-lookup"><span data-stu-id="8373d-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8373d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="8373d-103">Change description</span></span>

<span data-ttu-id="8373d-104">在 .NET Core 2.2 和舊版中， <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> .net core 元件（例如、和）的 [檔案屬性] 對話方塊等方法會反映檔案版本。</span><span class="sxs-lookup"><span data-stu-id="8373d-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="8373d-105">從 .NET Core 3.0 開始，它們會反映產品版本。</span><span class="sxs-lookup"><span data-stu-id="8373d-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="8373d-106">下圖說明 .NET Core 2.2 （左側）和 .NET Core 3.0 （位於右邊）的*system.webserver*元件版本資訊差異，如**Windows Explorer** [檔案屬性] 對話方塊所顯示。</span><span class="sxs-lookup"><span data-stu-id="8373d-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="8373d-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="8373d-108">Version introduced</span></span>

<span data-ttu-id="8373d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="8373d-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8373d-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="8373d-110">Recommended action</span></span>

<span data-ttu-id="8373d-111">無。</span><span class="sxs-lookup"><span data-stu-id="8373d-111">None.</span></span> <span data-ttu-id="8373d-112">這種變更應該可以直覺而不是簡直遲鈍進行版本偵測。</span><span class="sxs-lookup"><span data-stu-id="8373d-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="8373d-113">類別</span><span class="sxs-lookup"><span data-stu-id="8373d-113">Category</span></span>

<span data-ttu-id="8373d-114">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="8373d-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8373d-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8373d-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
