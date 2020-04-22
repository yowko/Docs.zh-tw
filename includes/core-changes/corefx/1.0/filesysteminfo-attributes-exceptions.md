---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021802"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="1f4b8-101">檔案系統資訊.屬性引發的未經授權的存取異常</span><span class="sxs-lookup"><span data-stu-id="1f4b8-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="1f4b8-102">在 .NET<xref:System.UnauthorizedAccessException>Core 中,當呼叫者嘗試設定檔屬性值但沒有寫入權限時,將引發 。</span><span class="sxs-lookup"><span data-stu-id="1f4b8-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1f4b8-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="1f4b8-103">Change description</span></span>

<span data-ttu-id="1f4b8-104">在 .NET Framework<xref:System.ArgumentException>中,當呼叫者<xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>嘗試在 中設定檔屬性值但沒有寫入權限時,將引發 。</span><span class="sxs-lookup"><span data-stu-id="1f4b8-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="1f4b8-105">在 .NET<xref:System.UnauthorizedAccessException>核心 中,將改為引發 。</span><span class="sxs-lookup"><span data-stu-id="1f4b8-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="1f4b8-106">(在 .NET<xref:System.ArgumentException>Core 中,如果呼叫者嘗試設定無效的檔案屬性,仍將引發 。</span><span class="sxs-lookup"><span data-stu-id="1f4b8-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1f4b8-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="1f4b8-107">Version introduced</span></span>

<span data-ttu-id="1f4b8-108">1.0</span><span class="sxs-lookup"><span data-stu-id="1f4b8-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1f4b8-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1f4b8-109">Recommended action</span></span>

<span data-ttu-id="1f4b8-110">根據需要修改`catch`任何敘述以捕捉<xref:System.UnauthorizedAccessException>而不是或<xref:System.ArgumentException>新增 。</span><span class="sxs-lookup"><span data-stu-id="1f4b8-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="1f4b8-111">類別</span><span class="sxs-lookup"><span data-stu-id="1f4b8-111">Category</span></span>

<span data-ttu-id="1f4b8-112">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="1f4b8-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f4b8-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1f4b8-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
