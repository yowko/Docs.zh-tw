---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538811"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="b42e6-101">.Props 檔案預設會匯入</span><span class="sxs-lookup"><span data-stu-id="b42e6-101">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="b42e6-102">NuGet 的 *.props* 檔案會自動匯入名為 *.props* 的檔案（如果在專案資料夾或其任何祖系中找到）。</span><span class="sxs-lookup"><span data-stu-id="b42e6-102">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b42e6-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b42e6-103">Version introduced</span></span>

<span data-ttu-id="b42e6-104">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="b42e6-104">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="b42e6-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="b42e6-105">Change description</span></span>

<span data-ttu-id="b42e6-106">在舊版的 .NET 中，您的專案檔中可能會有一個名為 *.props* 的檔案，而且在組建時，NuGet 的 *.props* 檔案不會自動匯入該檔案。</span><span class="sxs-lookup"><span data-stu-id="b42e6-106">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="b42e6-107">從 .NET 5.0 開始，如果檔案存在於專案資料夾或任何祖系中， *就* 會自動匯入這類檔案。</span><span class="sxs-lookup"><span data-stu-id="b42e6-107">Starting in .NET 5.0, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="b42e6-108">如果您的專案資料夾中有此名稱的檔案，此自動匯入可能會變更組建的行為。</span><span class="sxs-lookup"><span data-stu-id="b42e6-108">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="b42e6-109">例如，檔案會匯入，但不是之前，如果您明確匯入，則可能會變更匯入的順序。</span><span class="sxs-lookup"><span data-stu-id="b42e6-109">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b42e6-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b42e6-110">Reason for change</span></span>

<span data-ttu-id="b42e6-111">這項變更的目的是為了支援 NuGet 的 [中央套件版本](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) 設定。</span><span class="sxs-lookup"><span data-stu-id="b42e6-111">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b42e6-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b42e6-112">Recommended action</span></span>

<span data-ttu-id="b42e6-113">重新命名現有的 *.props* 檔案（如果不應自動匯入的話）。</span><span class="sxs-lookup"><span data-stu-id="b42e6-113">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

#### <a name="category"></a><span data-ttu-id="b42e6-114">類別</span><span class="sxs-lookup"><span data-stu-id="b42e6-114">Category</span></span>

<span data-ttu-id="b42e6-115">MSBuild</span><span class="sxs-lookup"><span data-stu-id="b42e6-115">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b42e6-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b42e6-116">Affected APIs</span></span>

<span data-ttu-id="b42e6-117">N/A</span><span class="sxs-lookup"><span data-stu-id="b42e6-117">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
