---
title: "移植到.NET Core-使用 Windows 相容性組件"
description: "Windows 相容性套件，請參閱了解如何使用它來連接埠現有.NET Framework 程式碼到.NET Core 和"
keywords: ".NET、.NET core、 Windows、 相容性"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 5094baee77aba4d1e148f807d842a4a2d3405cf7
ms.sourcegitcommit: 86cf9b4c7104485a9870645705b9a1a4b6ca8e2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2017
---
# <a name="using-the-windows-compatibility-pack"></a>使用 Windows 相容性組件

其中一個最常見移植到.NET Core 其現有的程式碼時，開發人員所面臨的問題是它們的相依應用程式開發介面和只存在於.NET Framework 中的技術。 *Windows 相容性套件*即將提供其中許多技術建置.NET Core 應用程式，以及標準的.NET 程式庫會變成更可行的現有程式碼。

此封裝是邏輯[延伸模組的.NET 標準 2.0](../whats-new/index.md#api-changes-and-library-support) ，大幅增加 API 集和現有的程式碼會編譯幾乎不需要修改。 但若要保留的.NET 標準承諾 （「 它是所有.NET 實作所都提供的 Api 集 」），這不包括無法跨所有平台，例如登錄，Windows Management Instrumentation (WMI) 的技術或反映發出應用程式開發介面。

*Windows 相容性套件*總結.NET 標準，並提供存取只是 Windows 的技術。 它特別適用於想要移動到.NET Core 但放入 Windows，做為第一個步驟中的計劃的客戶。 在這種情況下，無法使用僅限 Windows 技術是只使用零架構的優點移轉障礙。

## <a name="package-contents"></a>封裝內容

*Windows 相容性套件*會透過 NuGet 套件提供[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)而且可以從.NET Core 或標準.NET 為目標的專案參考。

它提供了大約 20000 Api，包括僅限 Windows，以及跨平台 Api，從下列技術領域：

* 字碼頁
* CodeDom
* 組態
* 目錄服務
* 繪圖
* ODBC
* 權限
* 連接埠
* Windows 存取控制清單 (ACL)
* Windows Communication Foundation (WCF)
* Windows 密碼編譯
* Windows 事件記錄檔
* Windows Management Instrumentation (WMI)
* Windows 效能計數器
* Windows 登錄
* Windows 執行階段快取
* Windows 服務

如需詳細資訊，請參閱[規格的相容性套件](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)。

## <a name="get-started"></a>開始使用

1. 在之前移轉，請確定看看[移轉程序](index.md)。

2. 當現有程式碼移植到.NET Core 或.NET 標準，安裝 NuGet 套件[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。

3. 如果您想要放入 Windows 時，所有設定。

4. 如果您想要在 Linux 或 macOS 執行.NET Core 應用程式或.NET 標準程式庫，使用[API 分析器](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/)若要尋找的 Api，將無法運作的跨平台的使用方式。

5. 請移除這些 Api 的用法，取代跨平台的替代方案，或保護使用平台檢查，例如：

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

如需示範，查看[的 Windows 相容性套件的 Channel 9 影片](https://channel9.msdn.com/Events/Connect/2017/T123)。

