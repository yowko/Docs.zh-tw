---
ms.openlocfilehash: 164d7a8277cf985735b959c73eb87391944e795b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602898"
---

### <a name="install-the-sdk"></a>安裝 SDK

.NET Core SDK 可讓您使用 .NET Core 開發應用程式。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 若要安裝 .NET Core SDK，請執行下列命令：

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> 如果您收到類似 [**找不到封裝 dotnet-sdk-2.1**] 的錯誤訊息，請參閱[APT 疑難排解](#apt-troubleshooting)一節。

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間可讓您執行使用 .NET Core 所建立且未包含執行時間的應用程式。 下列命令會安裝 ASP.NET Core 執行時間，這是適用于 .NET Core 的最相容執行時間。 在您的終端機中，執行下列命令。

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> 如果您收到類似 [**找不到套件 aspnetcore-執行時間-2.1**] 的錯誤訊息，請參閱[APT 疑難排解](#apt-troubleshooting)一節。

除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間：在 `aspnetcore-runtime-2.1` 上述命令中以取代 `dotnet-runtime-2.1` 。

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
