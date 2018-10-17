---
title: SourceLink 和.NET 程式庫
description: 使用 SourceLink 改善偵錯.NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49369795"
---
# <a name="sourcelink"></a>SourceLink

SourceLink 是一種技術，可讓來自 NuGet 的開發人員的.NET 組件的偵錯的來源的程式碼。 SourceLink 執行時建立 NuGet 套件，並將內嵌在組件和封裝的來源控制中繼資料。 開發人員下載封裝，並已在 Visual Studio 中啟用的 SourceLink 可以逐步執行原始程式碼。 SourceLink 提供來源控制項的中繼資料來建立絕佳的偵錯體驗。

## <a name="sourcelink-demo"></a>SourceLink 示範

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a>使用 SourceLink

使用 SourceLink 指示可於[dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub 存放庫。

您可以使用[NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)確認 SourceLink 中繼資料包含在封裝中成功內嵌。 檢查`Repository`中繼資料存在於註解識別碼和.pdb 檔案的位置與每個目標的.dll。

![在 [NuGet 套件總管] 的 SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink NuGet 封裝總管 中")

**請考慮 ✔️**使用 SourceLink 將原始檔控制中繼資料新增至您的組件和 NuGet 套件。

**請考慮 ✔️** PDB 檔納入 NuGet 套件。

>[!div class="step-by-step"]
[上一頁](./dependencies.md)
[下一頁](./publish-nuget-package.md)
