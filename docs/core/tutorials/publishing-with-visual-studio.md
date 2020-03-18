---
title: 使用視覺化工作室發佈您的 .NET 核心 Hello World 應用程式
description: 發行會建立一組執行您的 .NET Core 應用程式所需的檔案。
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156630"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>使用視覺化工作室發佈您的 .NET 核心 Hello World 應用程式

在[創建一個Hello世界應用程式與.NET核心在視覺工作室](with-visual-studio.md)，你建立了一個Hello世界主控台應用程式。 在[調試你的Hello世界應用程式與視覺化工作室](debugging-with-visual-studio.md)，你測試它使用視覺化工作室調試器。 現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。 發行會建立一組執行您的應用程式所需的檔案。 要部署檔，請將它們複製到目的電腦。

## <a name="publish-the-app"></a>發佈應用程式

1. 請確定 Visual Studio 正在組置您應用程式的發行版本。 如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。

   ![選取 [發行] 組建的 Visual Studio 工具列](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. 按右鍵**HelloWorld**專案（不是 HelloWorld 解決方案），然後從功能表中選擇 **"發佈**"。 （您還可以從主**生成**功能表中選擇 **"發佈 HelloWorld"。**

   ![Visual Studio [發行] 操作功能表](media/publishing-with-visual-studio/publish-context-menu.png)

1. 在 **"選取發佈目標**"頁上，選擇 **"資料夾**"，然後選擇"**創建設定檔**"。

   ![在視覺化工作室中選擇發佈目標](media/publishing-with-visual-studio/pick-publish-target.png)

1. 在 **"發佈"** 頁上，選擇 **"發佈**"。

   ![Visual Studio [發行] 視窗](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>檢查檔

發佈過程創建一個與框架相關的部署，這是一種部署類型，其中已發佈的應用程式在 .NET Core 支援的任何平臺上運行，系統上安裝了 .NET Core。 使用者可以通過按兩下可執行檔或從命令提示符發出`dotnet HelloWorld.dll`命令來運行已發佈的應用。

在以下步驟中，您將查看發佈過程創建的檔。

1. 開啟命令提示字元。

   打開命令提示符的一種方法是在 Windows 工作列上的搜索框中輸入**命令提示**符（或簡稱**cmd）。** 選擇**命令提示**桌面應用，或按 **"如果**已在搜尋結果中選中"。"

1. 導航到應用程式專案目錄的*bin_Release_netcoreapp3.1_發佈*子目錄中的已發佈應用程式。

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/published-files-output.png)

   如圖所示，已發佈的輸出包括以下檔：

      * *HelloWorld.deps.json*

         這是應用程式的運行時依賴項檔。 它定義了 .NET Core 元件和運行應用程式所需的庫（包括包含應用程式的動態連結程式庫）。 有關詳細資訊，請參閱[運行時設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。

      * *HelloWorld.dll*

         這是應用程式[與框架相關的部署](../deploying/deploy-with-cli.md#framework-dependent-deployment)版本。 要執行此動態連結程式庫，`dotnet HelloWorld.dll`請輸入命令提示符。

      * *HelloWorld.exe*

         這是應用程式[與框架相關的可執行](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。 要運行它，`HelloWorld.exe`請輸入命令提示符。

      * *HelloWorld.pdb* (對於部署為選用)

         這是調試符號檔。 此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。

      * *HelloWorld.runtimeconfig.json*

         這是應用程式的運行時設定檔。 它會識別建置您應用程式以在其上執行的 .NET Core 版本。 您還可以向其添加配置選項。 有關詳細資訊，請參閱[.NET Core 運行時配置設置](../run-time-config/index.md#runtimeconfigjson)。

## <a name="additional-resources"></a>其他資源

- [.NET 核心應用程式部署](../deploying/index.md)
