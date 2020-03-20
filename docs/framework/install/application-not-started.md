---
title: 故障排除"無法啟動此應用程式"
description: 瞭解如果看到"無法啟動此應用程式"對話方塊該怎麼辦。
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965902"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>排除"無法啟動此應用程式"錯誤訊息

為 .NET 框架開發的應用程式通常需要在系統上安裝 .NET 框架的特定版本。 在某些情況下，您可能嘗試在沒有已安裝版本或 .NET Framework 的預期版本的情況下運行應用程式。 這通常會生成如下所示的錯誤對話方塊：

![無法啟動這個應用程式](media/application-not-started/app-could-not-be-started.png)

這通常表示以下條件之一：

- 系統上的 .NET 框架安裝已損壞。

- 無法檢測到應用程式所需的 .NET 框架版本。

要解決此問題，以便運行應用程式，請執行以下操作：

1. 下載[.NET 框架修復工具 （NetFx 修復工具.exe）。](https://www.microsoft.com/download/details.aspx?id=30135) 下載完成後，該工具將自動運行。

1. 如果 .NET 框架修復工具建議執行任何其他操作（如下圖所示的操作），請選擇"**下一步**"。

   ![建議變更](media/application-not-started/repair-tool-recommended-changes.png)

1. .NET 框架修復工具顯示下圖中顯示的對話方塊，以指示更改已完成。 嘗試重新運行應用程式時，請保持對話方塊打開狀態。 如果 .NET 框架修復工具已識別並更正損壞的 .NET 框架安裝，則此成功。

   ![建議變更](media/application-not-started/repair-tool-changes-complete.png)

1. 如果應用程式成功運行，請選擇 **"完成"** 按鈕。 否則，選擇"**下一步**"按鈕。

1. 如果選擇了"**下一步"** 按鈕，.NET 框架修復工具將顯示一個對話方塊，如下所示。 選擇 **"完成"** 按鈕以向 Microsoft 發送診斷資訊。

   ![無法解決問題](media/application-not-started/repair-tool-no-resolution.png)

1. 如果仍然無法運行該應用程式，請安裝 Windows 版本支援的 .NET 框架的最新版本，如下表所示。

   |Windows 版本|.NET 框架安裝|
   |---|---|
   |Windows 10 周年更新和更高版本|[.NET 框架 4.8 運行時](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |視窗 10， Windows 10 11 月更新|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET 框架 4.8 運行時](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[.NET 框架 4.8 運行時](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET 框架 4.8 預先安裝在 2019 年 5 月 10 日的 Windows 更新中。

1. 嘗試啟動應用程式。

1. 在某些情況下，您可能會看到如下所示的對話方塊，該對話方塊要求您安裝 .NET 框架 3.5。 選擇 **"下載並安裝此功能**"以安裝 .NET 框架 3.5，然後再次啟動該應用程式。

   ![無法解決問題](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>另請參閱

- [.NET Framework 系統需求](../get-started/system-requirements.md)
- [.NET Framework 安裝指南](index.md)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md)
