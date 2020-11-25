---
title: 重大變更：單一檔案發佈格式的元件相關 API 行為變更
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中元件檔案位置的多個相關 Api 在以單一檔案發行格式叫用時，會有行為變更。
ms.date: 11/01/2020
ms.openlocfilehash: d77e30318040c8298065073a41caab56f2ca3875
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760706"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="b5068-103">單一檔案發佈格式的元件相關 API 行為變更</span><span class="sxs-lookup"><span data-stu-id="b5068-103">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="b5068-104">多個與元件檔案位置相關的 Api 在以單一檔案發行格式叫用時，會有行為變更。</span><span class="sxs-lookup"><span data-stu-id="b5068-104">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

## <a name="change-description"></a><span data-ttu-id="b5068-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="b5068-105">Change description</span></span>

<span data-ttu-id="b5068-106">在 .NET 5.0 和更新版本的單一檔案發行中，配套的元件會從記憶體載入，而不是解壓縮至磁片。</span><span class="sxs-lookup"><span data-stu-id="b5068-106">In single-file publishing for .NET 5.0 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="b5068-107">針對單一檔案發佈的應用程式，這表示某些位置相關的 Api 會在 .NET 5.0 和更新版本上，傳回與舊版 .NET 不同的值。</span><span class="sxs-lookup"><span data-stu-id="b5068-107">For single-file published apps, this means that certain location-related APIs return different values on .NET 5.0 and later than on previous versions of .NET.</span></span> <span data-ttu-id="b5068-108">變更如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5068-108">The changes are as follows:</span></span>

| <span data-ttu-id="b5068-109">API</span><span class="sxs-lookup"><span data-stu-id="b5068-109">API</span></span> | <span data-ttu-id="b5068-110">舊版</span><span class="sxs-lookup"><span data-stu-id="b5068-110">Previous versions</span></span> | <span data-ttu-id="b5068-111">.NET 5.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="b5068-111">.NET 5.0 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="b5068-112">傳回解壓縮的 DLL 檔案路徑</span><span class="sxs-lookup"><span data-stu-id="b5068-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="b5068-113">針對配套的元件傳回空字串</span><span class="sxs-lookup"><span data-stu-id="b5068-113">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="b5068-114">傳回解壓縮的 DLL 檔案路徑</span><span class="sxs-lookup"><span data-stu-id="b5068-114">Returns extracted DLL file path</span></span> | <span data-ttu-id="b5068-115">針對配套的元件擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="b5068-115">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b5068-116">`null`針對配套的元件傳回</span><span class="sxs-lookup"><span data-stu-id="b5068-116">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="b5068-117">針對配套的元件擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="b5068-117">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="b5068-118">值為進入點 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="b5068-118">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="b5068-119">值是主機可執行檔的名稱</span><span class="sxs-lookup"><span data-stu-id="b5068-119">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="b5068-120">值是暫存的解壓縮目錄</span><span class="sxs-lookup"><span data-stu-id="b5068-120">Value is the temporary extraction directory</span></span> | <span data-ttu-id="b5068-121">值是主機可執行檔的包含目錄</span><span class="sxs-lookup"><span data-stu-id="b5068-121">Value is the containing directory of the host executable</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="b5068-122">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b5068-122">Version introduced</span></span>

<span data-ttu-id="b5068-123">5.0</span><span class="sxs-lookup"><span data-stu-id="b5068-123">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b5068-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b5068-124">Recommended action</span></span>

<span data-ttu-id="b5068-125">以單一檔案的形式發行時，請避免元件的檔案位置相依性。</span><span class="sxs-lookup"><span data-stu-id="b5068-125">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b5068-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b5068-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
