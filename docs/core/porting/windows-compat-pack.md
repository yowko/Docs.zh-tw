---
title: 使用 Windows 相容性套件將程式碼移植到 .NET Core
description: 瞭解 Windows 相容性包以及如何使用它將現有的 .NET 框架代碼移植到 .NET Core。
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 166259ca37a2005d67f6c545e4843a940f05fb71
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228642"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>使用 Windows 相容性套件將程式碼移植到 .NET Core

將現有代碼移植到 .NET Core 時發現的一些最常見問題是依賴于 API 和僅在 .NET 框架中找到的技術。 *Windows 相容性套件*提供許多這些技術，因此建置 .NET Core 應用程式和 .NET Standard 程式庫很容易。

相容性包是[.NET 標準 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)的邏輯擴展，可顯著增加 API 集。 現有代碼編譯時幾乎沒有修改。 為了信守"所有 .NET 實現提供的 API 集"的承諾，.NET 標準不包括無法在所有平臺（如註冊表、Windows 管理檢測 （WMI） 或反射發出 API）中工作的技術。 Windows 相容性包位於 .NET 標準之上，提供對這些僅 Windows 技術的訪問。 對於想要遷移到 .NET Core 但計畫留在 Windows 上的客戶來說，這尤其有用，至少作為第一步。 在這種情況下，能夠使用僅 Windows 技術可消除遷移障礙。

## <a name="package-contents"></a>封裝內容

Windows 相容性包通過[Microsoft.Windows.相容性 NuGet 包](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)提供，可以從針對 .NET Core 或 .NET 標準的專案引用。

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

如需詳細資訊，請參閱[相容性套件規格](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md)。

## <a name="get-started"></a>開始使用

1. 在移植之前，請務必查看[移植過程](index.md)。

2. 將現有代碼移植到 .NET Core 或 .NET 標準時，請安裝[Microsoft.Windows.相容性 NuGet 包](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。

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
