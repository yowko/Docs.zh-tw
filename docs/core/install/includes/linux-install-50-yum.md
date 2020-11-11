---
ms.openlocfilehash: cc394741e399f4fc54dd67f1736f7027badf4c7d
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507090"
---

### <a name="install-the-sdk"></a>安裝 SDK

.NET SDK 可讓您使用 .NET 開發應用程式。 如果您安裝 .NET SDK，就不需要安裝對應的執行時間。 若要安裝 .NET SDK，請執行下列命令：

```bash
sudo yum install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a>安裝執行階段

ASP.NET Core 執行時間可讓您執行不提供執行時間的 .NET 所建立的應用程式。 下列命令會安裝 ASP.NET Core 執行時間，也就是最相容的 .NET 執行時間。 在您的終端機中執行下列命令：

```bash
sudo yum install aspnetcore-runtime-5.0
```

除了 ASP.NET Core 執行時間之外，您還可以安裝 .NET 執行時間，但不包括 ASP.NET Core 支援： `aspnetcore-runtime-5.0` 在先前的命令中將取代為 `dotnet-runtime-5.0` ：

```bash
sudo yum install dotnet-runtime-5.0
```
