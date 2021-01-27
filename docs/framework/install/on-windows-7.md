---
title: 在 Windows 7 SP1 上安裝 .NET Framework
description: 了解如何在 Windows 7 SP1 上安裝 .NET Framework。
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899083"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a>在 Windows 7 SP1 和 Windows Server 2008 R2 上安裝 .NET Framework

在 Windows 上執行許多應用程式時需要 .NET Framework。 您可以使用下列指示來安裝它。 嘗試執行應用程式並在電腦上看到下列對話方塊之後，可能會進入此頁面。

![無法啟動這個應用程式](./media/this-application-could-not-be-started.png)

這些指令將協助您安裝所需的 .NET Framework 版本。 [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) 是最新版本。 Windows 7 SP1 和 Windows Server 2008 R2 支援它，並且包含於 [Windows 10 2019 年 5 月更新](https://support.microsoft.com/help/4028685/windows-10-get-the-update)。

## <a name="net-framework-48"></a>.NET Framework 4.8

> [!div class="button"]
> [下載 .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) 可用來執行針對 .NET Framework 4.0 或更新版本建置的應用程式。

### <a name="offline-installer"></a>離線安裝程式

在 Windows 7 上進行 .NET Framework 的離線安裝時，必須先確定已在目的電腦上安裝最新的 [Microsoft 根憑證授權單位 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) 。

_certmgr.exe_ 工具可以自動安裝憑證，並從 Visual Studio 或 Windows SDK 取得。 執行 .NET Framework 安裝程式之前，會使用下列命令來安裝憑證：

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a>.NET Framework 3.5

[.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) 隨附於 Windows 7。

.NET Framework 3.5 支援針對 .NET Framework 1.0 到 3.5 建置的應用程式。

## <a name="help"></a>説明

如果您無法安裝正確的 .NET Framework 版本，可以[連絡 Microsoft 以取得協助](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。

## <a name="see-also"></a>另請參閱

- [下載 .NET Framework](https://dotnet.microsoft.com/download)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](troubleshoot-blocked-installations-and-uninstallations.md)
- [安裝適用於開發人員的 .NET Framework](guide-for-developers.md)
