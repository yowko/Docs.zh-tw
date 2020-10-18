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
# <a name="msbuild-breaking-changes"></a>MSBuild 重大變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | - |
| [TargetFramework 從 netcoreapp 變更為 net](#targetframework-change-from-netcoreapp-to-net) | 5.0 |
| [以 .NET 5 為目標時，未定義 NETCOREAPP3_1 預處理器符號](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | 5.0 |
| [PublishDepsFilePath 行為變更](#publishdepsfilepath-behavior-change) | 5.0 |
| [.Props 檔案預設會匯入](#directorypackagesprops-files-is-imported-by-default) | 5.0 |
| [資源資訊清單檔案名變更](#resource-manifest-file-name-change) | 3.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [targetframework-name-change](../../../includes/core-changes/msbuild/5.0/targetframework-name-change.md)]

***

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
