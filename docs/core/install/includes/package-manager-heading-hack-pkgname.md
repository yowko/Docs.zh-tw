---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602989"
---

新增至套件管理員摘要的封裝會以 hackable 格式命名： `{product}-{type}-{version}` 。

- **基礎**\
要安裝的 .NET 產品類型。 有效的選項包括：

  - dotnet
  - aspnetcore

- **型**\
選擇 SDK 或執行時間。 有效的選項包括：

  - sdk
  - 執行階段

- **版本**\
要安裝的 SDK 或執行階段版本。 本文一律會提供最新支援版本的指示。 有效的選項為任何已發行的版本，例如：

  - 3.1
  - 3.0
  - 2.1

  您嘗試下載的 SDK/執行時間可能不適用於您的 Linux 散發套件。 如需支援的發行版本清單，請參閱[.Net Core 相依性和需求](../linux.md)。

### <a name="examples"></a>範例

- 安裝 ASP.NET Core 3.1 執行時間：`aspnetcore-runtime-3.1`
- 安裝 .NET Core 2.1 執行時間：`dotnet-runtime-2.1`
- 安裝 .NET Core 3.1 SDK：`dotnet-sdk-3.1`

### <a name="package-missing"></a>套件遺失

如果封裝版本組合無效，則無法使用。 例如，沒有 ASP.NET Core SDK，SDK 元件會包含在 .NET Core SDK 中。 值 `aspnetcore-sdk-2.2` 不正確，應該是 `dotnet-sdk-2.2` 。 如需 .NET Core 支援的 Linux 發行版本清單，請參閱[.Net core 相依性和需求](../linux.md)。
