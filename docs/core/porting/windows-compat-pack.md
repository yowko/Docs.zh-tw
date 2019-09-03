---
title: 使用 Windows 相容性套件將程式碼移植到 .NET Core
description: 了解 Windows 相容性套件，以及如何使用它將現有的 .NET Framework 程式碼移植到 .NET Core
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 71e390881d4e9c7836622abeed49c0ea2e5f7526
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202558"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>使用 Windows 相容性套件將程式碼移植到 .NET Core

將現有程式碼移植到 .NET Core 時發現的一些最常見問題，是僅在 .NET Framework 中找到的 API 和技術相依性。 *Windows 相容性套件*提供許多這些技術，因此建置 .NET Core 應用程式和 .NET Standard 程式庫很容易。

此套件是邏輯的 [.NET Standard 2.0 延伸模組](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)，可大幅增加 API 集和現有的程式碼編譯，幾乎不需要修改。 但為信守 .NET Standard 的承諾 (「它是所有 .NET 實作提供的 API 集」)，這不包括無法跨所有平台的技術，例如登錄、Windows Management Instrumentation (WMI) 或反映發出 API。

「Windows 相容性套件」  位階高於 .NET Standard，並提供存取僅限 Windows 的技術。 它特別適合想要移至 .NET Core，但第一個步驟計劃停留在 Windows 的客戶。 在這種情況下，無法使用僅限 Windows 技術只是無架構優勢的移轉障礙。

## <a name="package-contents"></a>套件內容

「Windows 相容性套件」  透過 NuGet 套件 [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) 提供，可從以 .NET Core 或 .NET Standard 為目標的專案參考。

它提供約 20,000 個 API，包括僅限 Windows 以及來自下列技術領域的跨平台 API：

* 字碼頁
* CodeDom
* Configuration
* 目錄服務
* 繪圖
* ODBC
* 權限
* 連接埠
* Windows 存取控制清單 (ACL)
* Windows Communication Foundation (WCF)
* Windows 加密
* Windows EventLog
* Windows Management Instrumentation (WMI)
* Windows 效能計數器
* Windows 登錄
* Windows 執行階段快取
* Windows 服務

如需詳細資訊，請參閱[相容性套件規格](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)。

## <a name="get-started"></a>開始使用

1. 移植前，請務必查看[移植程序](index.md)。

2. 將現有的程式碼移植到 .NET Core 或 .NET Standard 時，請安裝 NuGet 套件 [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。

3. 如果您想要留在 Windows，即已完成所有準備。

4. 如果您想要在 Linux 或 macOS 上執行 .NET Core 應用程式或 .NET Standard 程式庫，請使用 [API 分析器](../../standard/analyzers/api-analyzer.md)尋找無法跨平台運作的 API 使用方式。

5. 移除這些 API 的使用方式，以跨平台的替代方案取代，或使用平台檢查保護它們，例如：

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

如需示範，請查看 [Channel 9 的 Windows 相容性套件影片](https://channel9.msdn.com/Events/Connect/2017/T123)。
