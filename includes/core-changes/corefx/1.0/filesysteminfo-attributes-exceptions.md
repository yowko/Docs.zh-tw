---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449389"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="be7e2-101">檔案系統資訊.屬性引發的未經授權的訪問異常</span><span class="sxs-lookup"><span data-stu-id="be7e2-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="be7e2-102">在 .NET Core<xref:System.UnauthorizedAccessException>中，當調用方嘗試設置檔案屬性值但沒有寫入權限時，將引發 。</span><span class="sxs-lookup"><span data-stu-id="be7e2-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="be7e2-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="be7e2-103">Change description</span></span>

<span data-ttu-id="be7e2-104">在 .NET Framework<xref:System.ArgumentException>中，當調用方嘗試在 中<xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>設置檔案屬性值但沒有寫入權限時，將引發 。</span><span class="sxs-lookup"><span data-stu-id="be7e2-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="be7e2-105">在 .NET 核心<xref:System.UnauthorizedAccessException>中，將改為引發 。</span><span class="sxs-lookup"><span data-stu-id="be7e2-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="be7e2-106">（在 .NET Core<xref:System.ArgumentException>中，如果調用方嘗試設置不正確檔案屬性，仍將引發 。</span><span class="sxs-lookup"><span data-stu-id="be7e2-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="be7e2-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="be7e2-107">Version introduced</span></span>

<span data-ttu-id="be7e2-108">1.0</span><span class="sxs-lookup"><span data-stu-id="be7e2-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="be7e2-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="be7e2-109">Recommended action</span></span>

<span data-ttu-id="be7e2-110">根據需要修改`catch`任何語句以捕獲<xref:System.UnauthorizedAccessException>而不是 或 添加<xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="be7e2-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="be7e2-111">類別</span><span class="sxs-lookup"><span data-stu-id="be7e2-111">Category</span></span>

<span data-ttu-id="be7e2-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="be7e2-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="be7e2-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="be7e2-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
