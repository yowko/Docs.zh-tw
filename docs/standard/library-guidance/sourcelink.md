---
title: 來源連結與 .NET 程式庫
description: 使用來源連結改善 .NET 程式庫偵錯的最佳做法建議。
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744547"
---
# <a name="source-link"></a>來源連結

來源連結技術可讓開發人員對來自 NuGet 的 .NET 組件進行原始程式碼偵錯。 來源連結會在建立 NuGet 套件時執行，並將原始程式碼控制中繼資料內嵌在組件和套件。 下載套件並在 Visual Studio 中啟用來源連結的開發人員可以逐步執行原始程式碼。 來源連結提供原始程式碼控制中繼資料來建立絕佳的偵錯體驗。

## <a name="source-link-demo"></a>來源連結示範

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>使用來源連結

使用來源連結的指示位於 [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub 存放庫。

您可以使用 [NuGet 套件總管](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)確認來源連結中繼資料已成功內嵌在套件中。 檢查`Repository`中繼資料是否存在提交識別碼，並且 .pdb 檔是否與每個目標的 .dll 一起位於其中。

![NuGet 包資源管理器中的源連結](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet 包資源管理器中的源連結")

✔️ 請考慮使用來源連結以將原始程式碼控制中繼資料新增到您的組件與 NuGet 套件。

> [!TIP]
> 您可以將偵錯工具屬性新增至您的類型，進一步加強開發人員的偵錯體驗。
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> 可以自訂類別或欄位在偵錯工具變數視窗中顯示的方式。
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> 指示偵錯工具逐步執行程式碼，而不要進入程式碼。
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> 控制成員是否要顯示在偵錯工具變數視窗中。

✔️ CONSIDER發行符號檔 (`*.pdb`)。

> 如需最佳偵錯體驗，您的程式庫應該發佈符號檔，以及使用來源連結。 如需有關符號檔和符號套件的詳細資訊，請參閱[符號套件](./nuget.md#symbol-packages)。

>[!div class="step-by-step"]
>[上一個](dependencies.md)
>[下一個](publish-nuget-package.md)
