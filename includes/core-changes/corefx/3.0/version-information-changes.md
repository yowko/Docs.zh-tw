---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021624"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="d464e-101">報表版本的 API 現在報告產品,而不是檔案版本</span><span class="sxs-lookup"><span data-stu-id="d464e-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="d464e-102">返回 .NET Core 中版本的許多 API 現在傳回產品版本,而不是檔版本。</span><span class="sxs-lookup"><span data-stu-id="d464e-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d464e-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d464e-103">Change description</span></span>

<span data-ttu-id="d464e-104">在 .NET Core 2.2<xref:System.Environment.Version?displayProperty=nameWithType>和<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>早期版本中, 方法(如 .NET Core 程式集的檔屬性對話框)反映檔版本。</span><span class="sxs-lookup"><span data-stu-id="d464e-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="d464e-105">從 .NET Core 3.0 開始,它們反映了產品版本。</span><span class="sxs-lookup"><span data-stu-id="d464e-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="d464e-106">下圖說明了 Windows**資源管理器**文件屬性對話*System.Runtime.dll*框顯示的 .NET Core 2.2(左側)和 .NET Core 3.0(右側)的版本資訊差異。</span><span class="sxs-lookup"><span data-stu-id="d464e-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![產品版本資訊的差異](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="d464e-108">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="d464e-108">Version introduced</span></span>

<span data-ttu-id="d464e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="d464e-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d464e-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d464e-110">Recommended action</span></span>

<span data-ttu-id="d464e-111">無。</span><span class="sxs-lookup"><span data-stu-id="d464e-111">None.</span></span> <span data-ttu-id="d464e-112">此更改應使版本檢測直觀,而不是過時。</span><span class="sxs-lookup"><span data-stu-id="d464e-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="d464e-113">類別</span><span class="sxs-lookup"><span data-stu-id="d464e-113">Category</span></span>

<span data-ttu-id="d464e-114">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="d464e-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d464e-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d464e-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
