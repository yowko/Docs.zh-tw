---
title: 使用 Windows 相容性套件將程式碼移植到 .NET Core
description: 瞭解 Windows 相容性套件，以及如何使用它將現有的 .NET Framework 程式碼移植到 .NET Core。
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733618"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>使用 Windows 相容性套件將程式碼移植到 .NET Core

將現有程式碼移植到 .NET Core 時所發現的一些最常見問題，是只在 .NET Framework 中找到的 Api 和技術相依性。 *Windows 相容性套件*提供許多這些技術，因此建置 .NET Core 應用程式和 .NET Standard 程式庫很容易。

相容性套件是[.NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)的邏輯延伸模組，可大幅增加 API 集。 現有的程式碼會進行編譯，幾乎不會進行任何修改。 為了維持「所有 .NET 部署所提供的一組 Api」的承諾，.NET Standard 不包含無法在所有平臺（例如登錄、Windows Management Instrumentation （WMI）或反映發出 Api）上工作的技術。 Windows 相容性套件位於 .NET Standard 之上，並可讓您存取這些僅限 Windows 的技術。 它特別適用于想要移至 .NET Core 但打算保留在 Windows 上的客戶，至少是第一個步驟。 在這種情況下，能夠使用僅限 Windows 的技術會移除遷移障礙。

## <a name="package-contents"></a>封裝內容

Windows 相容性套件是透過[Microsoft. Windows 相容性 NuGet 套件](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)提供，而且可以從以 .net Core 或 .NET Standard 為目標的專案中參考。

它提供約 20,000 個 API，包括僅限 Windows 以及來自下列技術領域的跨平台 API：

- 字碼頁
- CodeDom
- 組態
- 目錄服務
- 繪圖
- ODBC
- 權限
- 連接埠
- Windows 存取控制清單 (ACL)
- Windows Communication Foundation (WCF)
- Windows 加密
- Windows EventLog
- Windows Management Instrumentation (WMI)
- Windows 效能計數器
- Windows 登錄
- Windows 執行階段快取
- Windows 服務

如需詳細資訊，請參閱[相容性套件規格](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)。

## <a name="get-started"></a>開始使用

1. 在移植之前，請務必查看[移植](index.md)程式。

2. 將現有程式碼移植到 .NET Core 或 .NET Standard 時，請安裝[Microsoft Windows 相容性 NuGet 套件](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。

   如果您想要留在 Windows，即已完成所有準備。

3. 如果您想要在 Linux 或 macOS 上執行 .NET Core 應用程式或 .NET Standard 程式庫，請使用 [API 分析器](../../standard/analyzers/api-analyzer.md)尋找無法跨平台運作的 API 使用方式。

4. 移除這些 API 的使用方式，以跨平台的替代方案取代，或使用平台檢查保護它們，例如：

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
