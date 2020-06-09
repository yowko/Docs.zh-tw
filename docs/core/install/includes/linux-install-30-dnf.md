---
ms.openlocfilehash: f9ea0ee6402187365cec5cdced1617ee2ae66bed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603066"
---

### <a name="install-the-sdk"></a>安裝 SDK

.NET Core SDK 可讓您使用 .NET Core 開發應用程式。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 若要安裝 .NET Core SDK，請執行下列命令：

```bash
sudo dnf install dotnet-sdk-3.0
```

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間可讓您執行使用 .NET Core 所建立且未包含執行時間的應用程式。 下列命令會安裝 ASP.NET Core 執行時間，這是適用于 .NET Core 的最相容執行時間。 在您的終端機中，執行下列命令。

```bash
sudo dnf install aspnetcore-runtime-3.0
```

除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間：在 `aspnetcore-runtime-3.0` 上述命令中以取代 `dotnet-runtime-3.0` 。

```bash
sudo dnf install dotnet-runtime-3.0
```
