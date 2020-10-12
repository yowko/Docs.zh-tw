---
ms.openlocfilehash: 0d6847b7a937094f36efae70ae450cc37824221d
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955549"
---
### <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a><span data-ttu-id="07a3f-101">單一檔案發佈格式的元件相關 API 行為變更</span><span class="sxs-lookup"><span data-stu-id="07a3f-101">Assembly-related API behavior changes for single-file publishing format</span></span>

<span data-ttu-id="07a3f-102">多個與元件檔案位置相關的 Api 在以單一檔案發行格式叫用時，會有行為變更。</span><span class="sxs-lookup"><span data-stu-id="07a3f-102">Multiple APIs related to an assembly's file location have behavior changes when they're invoked in a single-file publishing format.</span></span>

#### <a name="change-description"></a><span data-ttu-id="07a3f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="07a3f-103">Change description</span></span>

<span data-ttu-id="07a3f-104">在 .NET 5.0 和更新版本的單一檔案發行中，配套的元件會從記憶體載入，而不是解壓縮至磁片。</span><span class="sxs-lookup"><span data-stu-id="07a3f-104">In single-file publishing for .NET 5.0 and later versions, bundled assemblies are loaded from memory instead of extracted to disk.</span></span> <span data-ttu-id="07a3f-105">針對單一檔案發佈的應用程式，這表示某些位置相關的 Api 會在 .NET 5.0 和更新版本上，傳回與舊版 .NET 不同的值。</span><span class="sxs-lookup"><span data-stu-id="07a3f-105">For single-file published apps, this means that certain location-related APIs return different values on .NET 5.0 and later than on previous versions of .NET.</span></span> <span data-ttu-id="07a3f-106">變更如下所示：</span><span class="sxs-lookup"><span data-stu-id="07a3f-106">The changes are as follows:</span></span>

| <span data-ttu-id="07a3f-107">API</span><span class="sxs-lookup"><span data-stu-id="07a3f-107">API</span></span> | <span data-ttu-id="07a3f-108">舊版</span><span class="sxs-lookup"><span data-stu-id="07a3f-108">Previous versions</span></span> | <span data-ttu-id="07a3f-109">.NET 5.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="07a3f-109">.NET 5.0 and later</span></span> |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | <span data-ttu-id="07a3f-110">傳回解壓縮的 DLL 檔案路徑</span><span class="sxs-lookup"><span data-stu-id="07a3f-110">Returns extracted DLL file path</span></span> | <span data-ttu-id="07a3f-111">針對配套的元件傳回空字串</span><span class="sxs-lookup"><span data-stu-id="07a3f-111">Returns empty string for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | <span data-ttu-id="07a3f-112">傳回解壓縮的 DLL 檔案路徑</span><span class="sxs-lookup"><span data-stu-id="07a3f-112">Returns extracted DLL file path</span></span> | <span data-ttu-id="07a3f-113">針對配套的元件擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="07a3f-113">Throws exception for bundled assemblies</span></span> |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | <span data-ttu-id="07a3f-114">`null`針對配套的元件傳回</span><span class="sxs-lookup"><span data-stu-id="07a3f-114">Returns `null` for bundled assemblies</span></span> | <span data-ttu-id="07a3f-115">針對配套的元件擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="07a3f-115">Throws exception for bundled assemblies</span></span> |
| `Environment.GetCommandLineArgs()[0]` | <span data-ttu-id="07a3f-116">值為進入點 DLL 的名稱</span><span class="sxs-lookup"><span data-stu-id="07a3f-116">Value is the name of the entry point DLL</span></span> | <span data-ttu-id="07a3f-117">值是主機可執行檔的名稱</span><span class="sxs-lookup"><span data-stu-id="07a3f-117">Value is the name of the host executable</span></span> |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | <span data-ttu-id="07a3f-118">值是暫存的解壓縮目錄</span><span class="sxs-lookup"><span data-stu-id="07a3f-118">Value is the temporary extraction directory</span></span> | <span data-ttu-id="07a3f-119">值是主機可執行檔的包含目錄</span><span class="sxs-lookup"><span data-stu-id="07a3f-119">Value is the containing directory of the host executable</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="07a3f-120">引進的版本</span><span class="sxs-lookup"><span data-stu-id="07a3f-120">Version introduced</span></span>

<span data-ttu-id="07a3f-121">5.0</span><span class="sxs-lookup"><span data-stu-id="07a3f-121">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="07a3f-122">建議的動作</span><span class="sxs-lookup"><span data-stu-id="07a3f-122">Recommended action</span></span>

<span data-ttu-id="07a3f-123">以單一檔案的形式發行時，請避免元件的檔案位置相依性。</span><span class="sxs-lookup"><span data-stu-id="07a3f-123">Avoid dependencies on the file location of assemblies when publishing as a single file.</span></span>

#### <a name="category"></a><span data-ttu-id="07a3f-124">類別</span><span class="sxs-lookup"><span data-stu-id="07a3f-124">Category</span></span>

- <span data-ttu-id="07a3f-125">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="07a3f-125">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="07a3f-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="07a3f-126">Affected APIs</span></span>

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
