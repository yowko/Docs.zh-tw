---
title: MSBuild 重大變更
description: 列出 MSBuild for .NET Core 中的重大變更。
ms.date: 02/10/2020
ms.openlocfilehash: 9b0fba30c8955a6099bde0dc95b4df65a151d9e6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159480"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="d5e7d-103">MSBuild 重大變更</span><span class="sxs-lookup"><span data-stu-id="d5e7d-103">MSBuild breaking changes</span></span>

<span data-ttu-id="d5e7d-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="d5e7d-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d5e7d-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="d5e7d-105">Breaking change</span></span> | <span data-ttu-id="d5e7d-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d5e7d-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="d5e7d-107">TargetFramework 從 netcoreapp 變更為 net</span><span class="sxs-lookup"><span data-stu-id="d5e7d-107">TargetFramework change from netcoreapp to net</span></span>](#targetframework-change-from-netcoreapp-to-net) | <span data-ttu-id="d5e7d-108">5.0</span><span class="sxs-lookup"><span data-stu-id="d5e7d-108">5.0</span></span> |
| [<span data-ttu-id="d5e7d-109">以 .NET 5 為目標時，未定義 NETCOREAPP3_1 預處理器符號</span><span class="sxs-lookup"><span data-stu-id="d5e7d-109">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="d5e7d-110">5.0</span><span class="sxs-lookup"><span data-stu-id="d5e7d-110">5.0</span></span> |
| [<span data-ttu-id="d5e7d-111">PublishDepsFilePath 行為變更</span><span class="sxs-lookup"><span data-stu-id="d5e7d-111">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="d5e7d-112">5.0</span><span class="sxs-lookup"><span data-stu-id="d5e7d-112">5.0</span></span> |
| [<span data-ttu-id="d5e7d-113">.Props 檔案預設會匯入</span><span class="sxs-lookup"><span data-stu-id="d5e7d-113">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="d5e7d-114">5.0</span><span class="sxs-lookup"><span data-stu-id="d5e7d-114">5.0</span></span> |
| [<span data-ttu-id="d5e7d-115">資源資訊清單檔案名變更</span><span class="sxs-lookup"><span data-stu-id="d5e7d-115">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="d5e7d-116">3.0</span><span class="sxs-lookup"><span data-stu-id="d5e7d-116">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d5e7d-117">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="d5e7d-117">.NET 5.0</span></span>

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="d5e7d-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d5e7d-118">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
