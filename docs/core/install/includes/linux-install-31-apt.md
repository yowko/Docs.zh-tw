---
ms.openlocfilehash: 56f5d27eb9be2f8eb3e335c5ec161dba1bcfdb1e
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135783"
---

### <a name="install-the-sdk"></a>安裝 SDK

.NET Core SDK 可讓您使用 .NET Core 開發應用程式。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 若要安裝 .NET Core SDK，請執行下列命令：

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> 如果您收到類似「 **找不到套件 dotnet-sdk-3.1** 」的錯誤訊息，請參閱 [APT 疑難排解](#apt-troubleshooting) 一節。

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。 下列命令會安裝適用于 .NET Core 的 ASP.NET Core 執行時間，這是最相容的執行時間。 在您的終端機中執行下列命令。

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> 如果您收到類似「 **找不到封裝 aspnetcore-runtime-3.1** 」的錯誤訊息，請參閱 [APT 疑難排解](#apt-troubleshooting) 一節。

除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `aspnetcore-runtime-3.1` 在先前的命令中將取代為 `dotnet-runtime-3.1` 。

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
