---
title: 重大變更： .props 檔案預設會匯入
description: 瞭解 .NET 5.0 中的重大變更，其中 NuGet 的 .props 檔案會自動匯入名為 .props 的檔案（如果在專案資料夾中找到的話）。
ms.date: 09/17/2020
ms.openlocfilehash: ee8a2999b801e81750d96a0bc985e3c8169224a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760642"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="da78d-103">.Props 檔案預設會匯入</span><span class="sxs-lookup"><span data-stu-id="da78d-103">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="da78d-104">NuGet 的 *.props* 檔案會自動匯入名為 *.props* 的檔案（如果在專案資料夾或其任何祖系中找到）。</span><span class="sxs-lookup"><span data-stu-id="da78d-104">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="da78d-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="da78d-105">Version introduced</span></span>

<span data-ttu-id="da78d-106">5.0</span><span class="sxs-lookup"><span data-stu-id="da78d-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="da78d-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="da78d-107">Change description</span></span>

<span data-ttu-id="da78d-108">在舊版的 .NET 中，您的專案檔中可能會有一個名為 *.props* 的檔案，而且在組建時，NuGet 的 *.props* 檔案不會自動匯入該檔案。</span><span class="sxs-lookup"><span data-stu-id="da78d-108">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="da78d-109">從 .NET 5.0 開始，如果檔案存在於專案資料夾或任何祖系中， *就* 會自動匯入這類檔案。</span><span class="sxs-lookup"><span data-stu-id="da78d-109">Starting in .NET 5.0, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="da78d-110">如果您的專案資料夾中有此名稱的檔案，此自動匯入可能會變更組建的行為。</span><span class="sxs-lookup"><span data-stu-id="da78d-110">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="da78d-111">例如，檔案會匯入，但不是之前，如果您明確匯入，則可能會變更匯入的順序。</span><span class="sxs-lookup"><span data-stu-id="da78d-111">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="da78d-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="da78d-112">Reason for change</span></span>

<span data-ttu-id="da78d-113">這項變更的目的是為了支援 NuGet 的 [中央套件版本](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) 設定。</span><span class="sxs-lookup"><span data-stu-id="da78d-113">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="da78d-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="da78d-114">Recommended action</span></span>

<span data-ttu-id="da78d-115">重新命名現有的 *.props* 檔案（如果不應自動匯入的話）。</span><span class="sxs-lookup"><span data-stu-id="da78d-115">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="da78d-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="da78d-116">Affected APIs</span></span>

<span data-ttu-id="da78d-117">N/A</span><span class="sxs-lookup"><span data-stu-id="da78d-117">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
