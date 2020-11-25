---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032004"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="2b9ba-101">FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性</span><span class="sxs-lookup"><span data-stu-id="2b9ba-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="2b9ba-102">在 .NET Core 中， <xref:System.UnauthorizedAccessException> 當呼叫端嘗試設定檔案屬性值但沒有寫入權限時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="2b9ba-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2b9ba-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="2b9ba-103">Change description</span></span>

<span data-ttu-id="2b9ba-104">在 .NET Framework 中， <xref:System.ArgumentException> 當呼叫端嘗試在中設定檔案屬性值， <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> 但沒有寫入權限時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="2b9ba-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="2b9ba-105">在 .NET Core 中， <xref:System.UnauthorizedAccessException> 會改為擲回。</span><span class="sxs-lookup"><span data-stu-id="2b9ba-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="2b9ba-106">在 .NET Core 中 (， <xref:System.ArgumentException> 如果呼叫端嘗試設定不正確檔案屬性，仍會擲回。 ) </span><span class="sxs-lookup"><span data-stu-id="2b9ba-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b9ba-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="2b9ba-107">Version introduced</span></span>

<span data-ttu-id="2b9ba-108">1.0</span><span class="sxs-lookup"><span data-stu-id="2b9ba-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2b9ba-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="2b9ba-109">Recommended action</span></span>

<span data-ttu-id="2b9ba-110">`catch`視需要修改任何語句，以捕捉 <xref:System.UnauthorizedAccessException> instead of 或以外的 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="2b9ba-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="2b9ba-111">類別</span><span class="sxs-lookup"><span data-stu-id="2b9ba-111">Category</span></span>

<span data-ttu-id="2b9ba-112">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="2b9ba-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b9ba-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2b9ba-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
