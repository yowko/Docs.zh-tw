---
title: "在 Windows 10 上安裝 .NET Framework"
description: "了解如何在 Windows 10 或 Windows Server 2016 上安裝.NET Framework。"
author: rlander
ms.author: mairaw
keywords: ".NET Framework, 安裝"
ms.date: 11/17/2017
ms.topic: article
ms.custom: updateeachrelease
ms.prod: .net-framework
ms.openlocfilehash: d7f8dd4c6ee9f7eeda389a955f806a5765876ea7
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a>在 Windows 10 和 Windows Server 2016 上安裝.NET Framework

.NET Framework 才能在 Windows 上執行許多應用程式。 這篇文章中的指示應該協助您安裝您所需要的.NET Framework 版本。 [.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47)是最新可用版本。

您可能已到達此頁面上嘗試執行應用程式後類似下列其中一個在電腦上看到的對話方塊：

![無法啟動此應用程式](./media/this-application-could-not-be-started.png)

## <a name="net-framework-471"></a>.NET framework 4.7.1

.NET Framework 4.7.1 隨附於：

* [Windows 10 年秋季建立者更新 （版本 1709年）](https://www.microsoft.com/software-download/windows10)
* [Windows Server 2016 （版本 1709年）](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709)

> [!div class="button"]
[下載.NET Framework 4.7.1](https://www.microsoft.com/net/download/thank-you/net471?utm_source=ms-docs&utm_medium=referral)

[.NET Framework 4.7.1](https://www.microsoft.com/download/details.aspx?id=56115&desc=dotnet47)可以用來執行建置 4.7.1 透過.NET Framework 4.0 的應用程式。

您可以安裝[.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47)上：

* Windows 10 建立者更新 （版本 1703年）
* Windows 10 年度更新 （版本 1607年）
* Windows Server 2016

不支援.NET Framework 4.7.1:

* Windows 10 1507
* Windows 10 1511

如果您使用 Windows 10 1507年或 1511年，而且您想要安裝.NET Framework 4.7.1，您必須先升級至較新版的 Windows 10。

## <a name="net-framework-461"></a>.NET Framework 4.6.1

[.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981)是最新支援.NET Framework 版本的 Windows 10 1507年和 1511年。

.NET Framework 4.6.1 支援.NET Framework 4.0，透過 4.6.1 的建置的應用程式。

## <a name="net-framework-35"></a>.NET Framework 3.5

請依照指示[在 Windows 10 上安裝 .NET Framework 3.5](dotnet-35-windows-10.md)。

.NET Framework 3.5 支援的.NET Framework 1.0 到 3.5 所建置的應用程式。

## <a name="additional-information"></a>其他資訊

.NET framework 4.x 版本是舊版的就地更新。 這表示下列項目：

- 您可以只有一個版本的.NET framework 4.x 安裝在您的電腦上。

- 如果已安裝較新版本，您無法在電腦上安裝舊版的.NET Framework。

- .NET framework 4.x 版本可以用來執行建置.NET Framework 4.0，透過該版本的應用程式。 例如，.NET Framework 4.7 可以用來執行建置 4.7 透過.NET Framework 4.0 的應用程式。 最新版本 (.NET Framework 4.7.1) 可以用來執行建置的應用程式將所有版本的.NET Framework 4.0 為開頭。

如需可供下載的.NET framework 的所有版本的清單，請參閱[.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)頁面。

## <a name="help"></a>說明

如果您無法取得安裝的.NET Framework 正確版本，您可以[連絡 Microsoft 以取得協助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。

## <a name="see-also"></a>請參閱

[.NET 下載](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)   
[疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md)   
[安裝.NET Framework 開發人員](guide-for-developers.md)