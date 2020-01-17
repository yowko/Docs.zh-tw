---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116171"
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

### <a name="troubleshoot"></a>疑難排解

如果封裝組合無法運作，就無法使用。 例如，沒有 ASP.NET Core SDK，SDK 元件會包含在 .NET Core SDK 中。 `aspnetcore-sdk-2.2` 的值不正確，應為 `dotnet-sdk-2.2`
