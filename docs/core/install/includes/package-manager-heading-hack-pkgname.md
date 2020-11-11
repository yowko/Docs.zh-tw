---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506848"
---

加入封裝管理員摘要的封裝會以 hackable 格式命名： `{product}-{type}-{version}` 。

- **產品**\
要安裝的 .NET 產品類型。 有效的選項包括：

  - dotnet
  - aspnetcore

- **類型**\
選擇 SDK 或執行時間。 有效的選項包括：

  - sdk
  - 執行階段

- **版本**\
要安裝的 SDK 或執行階段版本。 本文一律會提供最新支援版本的指示。 有效的選項為任何已發行的版本，例如：

  - 5.0
  - 3.1
  - 3.0
  - 2.1

  您嘗試下載的 SDK/執行時間可能無法用於您的 Linux 散發套件。 如需支援的發行版本清單，請參閱 [.Net Core 相依性和需求](../linux.md)。

### <a name="examples"></a>範例

- 安裝 ASP.NET Core 5.0 執行時間： `aspnetcore-runtime-5.0`
- 安裝 .NET Core 2.1 執行時間： `dotnet-runtime-2.1`
- 安裝 .NET 5.0 SDK： `dotnet-sdk-5.0`
- 安裝 .NET Core 3.1 SDK： `dotnet-sdk-3.1`

### <a name="package-missing"></a>封裝遺失

如果封裝版本組合無法運作，則無法使用。 例如，沒有 ASP.NET Core SDK，SDK 元件隨附于 .NET SDK。 值 `aspnetcore-sdk-2.2` 不正確，應該是 `dotnet-sdk-2.2` 。 如需 .NET Core 所支援的 Linux 發行版本清單，請參閱 .Net 相依性 [和需求](../linux.md)。
