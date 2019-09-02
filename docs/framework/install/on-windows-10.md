---
title: 在 Windows 10 上安裝 .NET Framework
description: 了解如何在 Windows 10 或 Windows Server 2016 上安裝 .NET Framework。
author: rlander
ms.author: mairaw
ms.date: 04/18/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 33805230e0aa6c75443773d60e73f9463ee1fde5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106549"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016-and-later"></a>在 Windows 10 和 Windows Server 2016 以及更新版本上安裝 .NET Framework

在 Windows 上執行許多應用程式時需要 .NET Framework。 本文中的指示可協助您安裝所需的 .NET Framework 版本。 [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) 是提供的最新版本。

嘗試執行應用程式之後可能會進入此頁面，並會於您的電腦上看到類似如下的對話方塊：

![無法啟動這個應用程式](./media/this-application-could-not-be-started.png)

## <a name="net-framework-48"></a>.NET Framework 4.8

.NET Framework 4.8 隨附於下列項目中：

- [Windows 10 2019 年 5 月更新](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

> [!div class="button"]
> [下載 .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) 可用於執行專為 .NET Framework 4.0 到 4.7.2 建置的應用程式。

您可以將 [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) 安裝於：

- Windows 10 2018 年 10 月更新 (版本 1809)
- Windows 10 2018 年 4 月更新 (版本 1803)
- Windows 10 Fall Creators Update (版本 1709)
- Windows 10 Creators Update (版本 1703)
- Windows 10 年度更新版 (版本 1607)
- Windows Server 2019
- Windows Server，版本 1809
- Windows Server，版本 1803
- Windows Server 2016

以下項目不支援 .NET Framework 4.8：

- Windows 10 1507
- Windows 10 1511

若目前使用 Windows 10 1507 或 1511，且希望安裝.NET Framework 4.8，即必須先升級至更新版的 Windows 10。

## <a name="net-framework-462"></a>.NET Framework 4.6.2

[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345) 是 Windows 10 1507 和 1511 支援之最新版 .NET Framework。

.NET Framework 4.6.2 支援專為 .NET Framework 4.0 到 4.6.2 建置的應用程式。

## <a name="net-framework-35"></a>.NET Framework 3.5

請依照指示[在 Windows 10 上安裝 .NET Framework 3.5](dotnet-35-windows-10.md)。

.NET Framework 3.5 支援專為 .NET Framework 1.0 到 3.5 建置的應用程式。

## <a name="additional-information"></a>其他資訊

.NET Framework 4.x 版本是舊版的就地更新。 這表示：

- 您的電腦上只可安裝一個版本的 .NET framework 4.x。

- 若電腦上已安裝了更新的 .NET Framework 版本，就無法安裝舊版。

- 4.x 版的 .NET Framework 可用於執行專為 .NET Framework 4.0 及其小數點版本所建置的應用程式。 例如，.NET Framework 4.7 可用於執行專為 .NET Framework 4.0 到 4.7 所建置的應用程式。 最新版本 (.NET Framework 4.8) 可用於執行使用所有 .NET Framework 4.0 以上版本來建置的應用程式。

如需所有所有可下載之 .NET Framework 版本的清單，請參閱 [.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)頁面。

## <a name="help"></a>說明

若無法安裝正確的 .NET Framework 版本，可[連絡 Microsoft 取得協助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。

## <a name="see-also"></a>另請參閱

- [NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) (.NET 下載)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md)
- [安裝適用於開發人員的 .NET Framework](guide-for-developers.md)
