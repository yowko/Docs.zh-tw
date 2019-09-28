---
title: 疑難排解「無法啟動此應用程式」
description: 如果您看到 [無法啟動此應用程式] 對話方塊，請瞭解該怎麼辦。
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 2534979e8dea886c2d7298c57e12b66d7a962c69
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401701"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>疑難排解「此應用程式無法啟動」錯誤訊息

針對 .NET Framework 所開發的應用程式通常需要在您的系統上安裝特定版本的 .NET Framework。 在某些情況下，您可能會嘗試執行應用程式，而不需要有已安裝的版本或所需的 .NET Framework 版本。 這通常會產生如下的錯誤對話方塊：

![無法啟動這個應用程式](media/application-not-started/app-could-not-be-started.png)

這通常表示下列其中一種情況：

- 系統上的 .NET Framework 安裝已損毀。

- 無法偵測到您的應用程式所需的 .NET Framework 版本。

若要解決此問題，讓您能夠執行應用程式，請執行下列動作：

1. 下載[.NET Framework Repair Tool （NetFxRepairTool）](https://www.microsoft.com/download/details.aspx?id=30135)。 此工具會在下載完成時自動執行。

1. 如果 .NET Framework 修復工具建議任何其他動作（例如下圖所示的動作），請選取 **[下一步]** 。

   ![建議變更](media/application-not-started/repair-tool-recommended-changes.png)

1. [.NET Framework 修復工具] 會顯示如下圖所示的對話方塊，指出變更已完成。 在您嘗試重新執行應用程式時，讓對話方塊保持開啟。 如果 .NET Framework 修復工具已識別並更正損毀的 .NET Framework 安裝，這應該會成功。

   ![建議變更](media/application-not-started/repair-tool-changes-complete.png)

1. 如果您的應用程式順利執行，請選取 [**完成]** 按鈕。 否則，請選取 [**下一步]** 按鈕。

1. 如果您選取 [**下一步]** 按鈕，[.NET Framework Repair] 工具會顯示如下的對話方塊。 選取 [**完成]** 按鈕，將診斷資訊傳送給 Microsoft。

   ![無法解決問題](media/application-not-started/repair-tool-no-resolution.png)

1. 如果您仍然無法執行應用程式，請安裝您的 Windows 版本所支援的最新版本 .NET Framework，如下表所示。

   |Windows 版本|.NET Framework 安裝|
   |---|---|
   |Windows 10 年度更新版和更新版本|[.NET Framework 4.8 執行時間](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10，Windows 10 11 月更新|[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345)|
   |Windows 8.1|[.NET Framework 4.8 執行時間](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981)|
   |Windows 7 SP1|[.NET Framework 4.8 執行時間](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   >  .NET Framework 4.8 已預先安裝在 Windows 10 5 月2019更新。

1. 嘗試啟動應用程式。

1. 在某些情況下，您可能會看到如下所示的對話方塊，這會要求您安裝 .NET Framework 3.5。 選取 [**下載並安裝此功能**] 以安裝 .NET Framework 3.5，然後再次啟動應用程式。

   ![無法解決問題](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>另請參閱

- [.NET Framework 系統需求](../get-started/system-requirements.md)
- [.NET Framework 安裝指南](index.md)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md)
