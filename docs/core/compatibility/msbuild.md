---
title: MSBuild 重大變更
description: 列出 MSBuild for .NET Core 中的重大變更。
ms.date: 02/10/2020
ms.openlocfilehash: b57c70d21e061c59f26b11a025d4d05ce3b8ca99
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654729"
---
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="0c236-103">MSBuild 重大變更</span><span class="sxs-lookup"><span data-stu-id="0c236-103">MSBuild breaking changes</span></span>

<span data-ttu-id="0c236-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="0c236-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="0c236-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="0c236-105">Breaking change</span></span> | <span data-ttu-id="0c236-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0c236-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="0c236-107">以 .NET 5 為目標時，未定義 NETCOREAPP3_1 預處理器符號</span><span class="sxs-lookup"><span data-stu-id="0c236-107">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="0c236-108">5.0</span><span class="sxs-lookup"><span data-stu-id="0c236-108">5.0</span></span> |
| [<span data-ttu-id="0c236-109">PublishDepsFilePath 行為變更</span><span class="sxs-lookup"><span data-stu-id="0c236-109">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="0c236-110">5.0</span><span class="sxs-lookup"><span data-stu-id="0c236-110">5.0</span></span> |
| [<span data-ttu-id="0c236-111">.Props 檔案預設會匯入</span><span class="sxs-lookup"><span data-stu-id="0c236-111">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="0c236-112">5.0</span><span class="sxs-lookup"><span data-stu-id="0c236-112">5.0</span></span> |
| [<span data-ttu-id="0c236-113">資源資訊清單檔案名變更</span><span class="sxs-lookup"><span data-stu-id="0c236-113">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="0c236-114">3.0</span><span class="sxs-lookup"><span data-stu-id="0c236-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="0c236-115">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="0c236-115">.NET 5.0</span></span>

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="0c236-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0c236-116">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
