---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449389"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="bb57c-101">FileSystemInfo 擲回的 System.unauthorizedaccessexception</span><span class="sxs-lookup"><span data-stu-id="bb57c-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="bb57c-102">在 .NET Core 中，當呼叫端嘗試設定檔案屬性值但不具有寫入權限時，就會擲回 <xref:System.UnauthorizedAccessException>。</span><span class="sxs-lookup"><span data-stu-id="bb57c-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bb57c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="bb57c-103">Change description</span></span>

<span data-ttu-id="bb57c-104">在 .NET Framework 中，當呼叫端嘗試在 <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> 中設定檔案屬性值，但沒有寫入權限時，就會擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="bb57c-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="bb57c-105">在 .NET Core 中，會改為擲回 <xref:System.UnauthorizedAccessException>。</span><span class="sxs-lookup"><span data-stu-id="bb57c-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="bb57c-106">（在 .NET Core 中，如果呼叫端嘗試設定不正確檔案屬性，仍然會擲回 <xref:System.ArgumentException>）。</span><span class="sxs-lookup"><span data-stu-id="bb57c-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb57c-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bb57c-107">Version introduced</span></span>

<span data-ttu-id="bb57c-108">1.0</span><span class="sxs-lookup"><span data-stu-id="bb57c-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bb57c-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bb57c-109">Recommended action</span></span>

<span data-ttu-id="bb57c-110">視需要修改任何 `catch` 語句來攔截 <xref:System.UnauthorizedAccessException>，而不是 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="bb57c-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="bb57c-111">類別</span><span class="sxs-lookup"><span data-stu-id="bb57c-111">Category</span></span>

<span data-ttu-id="bb57c-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="bb57c-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb57c-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bb57c-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
