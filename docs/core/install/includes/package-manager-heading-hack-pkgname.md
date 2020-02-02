---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920650"
---

新增至套件管理員摘要的封裝會以 hackable 格式命名： `{product}-{type}-{version}`。

- **產品**\
要安裝的 .NET 產品類型。 有效的選項為：

  - dotnet
  - aspnetcore

- **類型**\
選擇 SDK 或執行時間。 有效的選項為：

  - SDK
  - 執行階段 ( runtime)

- **版本**\
要安裝的 SDK 或執行階段版本。 本文一律會提供最新支援版本的指示。 有效的選項為任何已發行的版本，例如：

  - 3.0
  - 2.2
  - 2.1

### <a name="examples"></a>範例

- 安裝 .NET Core 2.2 SDK： `dotnet-sdk-2.2`
- 安裝 ASP.NET Core 3.1 執行時間： `aspnetcore-runtime-3.1`
- 安裝 .NET Core 2.1 執行時間： `dotnet-runtime-2.1`

### <a name="package-missing"></a>套件遺失

如果封裝版本組合無效，則無法使用。 例如，沒有 ASP.NET Core SDK，SDK 元件會包含在 .NET Core SDK 中。 `aspnetcore-sdk-2.2` 的值不正確，應為 `dotnet-sdk-2.2`。
