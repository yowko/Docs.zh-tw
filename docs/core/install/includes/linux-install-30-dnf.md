---
ms.openlocfilehash: 8315b4f86dddfbb68534bc9ad3ad74907daa03d0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507041"
---

### <a name="install-the-sdk"></a>安裝 SDK

此 .NET Core SDK 可讓您使用 .NET Core 開發應用程式。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 若要安裝 .NET Core SDK，請執行下列命令：

```bash
sudo dnf install dotnet-sdk-3.0
```

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。 下列命令會安裝適用于 .NET Core 的 ASP.NET Core 執行時間，這是最相容的執行時間。 在您的終端機中執行下列命令。

```bash
sudo dnf install aspnetcore-runtime-3.0
```

除了 ASP.NET Core 執行時間之外，您還可以安裝 .NET Core 執行時間（不包括 ASP.NET Core 支援： `aspnetcore-runtime-3.0` 在先前的命令中將取代為） `dotnet-runtime-3.0` 。

```bash
sudo dnf install dotnet-runtime-3.0
```
