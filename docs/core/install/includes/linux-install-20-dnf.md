---
ms.openlocfilehash: 787b0a04c5bf312ad3f3e7834664e70dae9678e0
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93136301"
---

### <a name="install-the-sdk"></a>安裝 SDK

.NET Core SDK 可讓您使用 .NET Core 開發應用程式。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 若要安裝 .NET Core SDK，請執行下列命令：

```bash
sudo dnf install dotnet-sdk-2.0
```

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。 下列命令會安裝適用于 .NET Core 的 ASP.NET Core 執行時間，這是最相容的執行時間。 在您的終端機中執行下列命令。

```bash
sudo dnf install aspnetcore-runtime-2.0
```

除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `aspnetcore-runtime-2.0` 在先前的命令中將取代為 `dotnet-runtime-2.0` 。

```bash
sudo dnf install dotnet-runtime-2.0
```
