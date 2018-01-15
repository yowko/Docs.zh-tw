---
title: "在 Windows 10 上安裝 .NET Framework"
description: "了解如何在 Windows 10 或 Windows Server 2016 上安裝 .NET Framework。"
author: rlander
ms.author: mairaw
keywords: ".NET Framework, 安裝"
ms.date: 12/20/2017
ms.topic: article
ms.custom: updateeachrelease
ms.prod: .net-framework
ms.workload: dotnet
ms.openlocfilehash: bd588dff62e5d4ac1c1059e697a07598ba272042
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a>在 Windows 10 和 Windows Server 2016 上安裝 .NET Framework

在 Windows 上執行許多應用程式時需要 .NET Framework。 本文中的指示可協助您安裝所需的 .NET Framework 版本。 [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) 是提供的最新版本。

嘗試執行應用程式之後可能會進入此頁面，並會於您的電腦上看到類似如下的對話方塊：

![無法啟動這個應用程式](./media/this-application-could-not-be-started.png)

## <a name="net-framework-471"></a>.NET Framework 4.7.1

.NET Framework 4.7.1 隨附於下列項目中：

* [Windows 10 Fall Creators Update (版本 1709)](https://www.microsoft.com/software-download/windows10)
* [Windows Server，1709 版](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709)

> [!div class="button"]
[下載 .NET Framework 4.7.1](https://www.microsoft.com/net/download/thank-you/net471?utm_source=ms-docs&utm_medium=referral)

[.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47) 可用於執行專為 .NET Framework 4.0 到 4.7.1 建置的應用程式。

您可將 [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) 安裝於：

* Windows 10 Creators Update (版本 1703)
* Windows 10 年度更新版 (版本 1607)
* Windows Server 2016

以下項目不支援 .NET Framework 4.7.1：

* Windows 10 1507
* Windows 10 1511

若目前使用 Windows 10 1507 或 1511，且希望安裝.NET Framework 4.7.1，即必須先升級至更新版的 Windows 10。

## <a name="net-framework-462"></a>.NET Framework 4.6.2

[.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) 是 Windows 10 1507 和 1511 支援之最新版 .NET Framework。

.NET Framework 4.6.2 支援專為 .NET Framework 4.0 到 4.6.2 建置的應用程式。

## <a name="net-framework-35"></a>.NET Framework 3.5

請依照指示[在 Windows 10 上安裝 .NET Framework 3.5](dotnet-35-windows-10.md)。

.NET Framework 3.5 支援專為 .NET Framework 1.0 到 3.5 建置的應用程式。

## <a name="additional-information"></a>其他資訊

.NET Framework 4.x 版本是舊版的就地更新。 這表示：

- 您的電腦上只可安裝一個版本的 .NET framework 4.x。

- 若電腦上已安裝了更新的 .NET Framework 版本，就無法安裝舊版。

- 4.x 版的 .NET Framework 可用於執行專為 .NET Framework 4.0 及其小數點版本所建置的應用程式。 例如，.NET Framework 4.7 可用於執行專為 .NET Framework 4.0 到 4.7 所建置的應用程式。 最新版本 (.NET Framework 4.7.1) 可用於執行專為所有從 4.0 開始的 .NET Framework 版本，所建置的應用程式。

如需所有所有可下載之 .NET Framework 版本的清單，請參閱 [.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)頁面。

## <a name="help"></a>說明

若無法安裝正確的 .NET Framework 版本，可[連絡 Microsoft 取得協助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。

## <a name="see-also"></a>另請參閱

[.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)   
[疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md)   
[安裝適用於開發人員的 .NET Framework](guide-for-developers.md)
