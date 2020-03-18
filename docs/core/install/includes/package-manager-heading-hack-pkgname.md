---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77465977"
---

添加到包管理器源的包以可破解的格式命名： `{product}-{type}-{version}`。

- **產品**\
要安裝的 .NET 產品的類型。 有效的選項包括：

  - dotnet
  - 阿斯普內科

- **類型**\
選擇 SDK 或運行時。 有效的選項包括：

  - sdk
  - 執行階段

- **版本**\
要安裝的 SDK 或運行時的版本。 本文將始終提供最新受支援版本的說明。 有效選項是任何發佈的版本，例如：

  - 3.1
  - 3.0
  - 2.1

  您嘗試下載的 SDK/運行時可能不適用於 Linux 發行版本。 有關受支援的分發的清單，請參閱[.NET Core 依賴項和要求](../dependencies.md?pivots=os-linux)。

### <a name="examples"></a>範例

- 安裝ASP.NET核心 3.1 運行時：`aspnetcore-runtime-3.1`
- 安裝 .NET 核心 2.1 運行時：`dotnet-runtime-2.1`
- 安裝 .NET 核心 3.0 SDK：`dotnet-sdk-3.0`

### <a name="package-missing"></a>缺少包

如果包版本組合不起作用，則不可用。 例如，沒有ASP.NET核心 SDK，SDK 元件包含在 .NET 核心 SDK 中。 該值`aspnetcore-sdk-2.2`不正確，應為`dotnet-sdk-2.2`。 有關 .NET Core 支援的 Linux 發行版本的清單，請參閱[.NET Core 依賴項和要求](../dependencies.md?pivots=os-linux)。
