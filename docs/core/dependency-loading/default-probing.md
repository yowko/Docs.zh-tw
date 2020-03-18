---
title: 預設探測 - .NET 核心
description: .NET Core 的系統概述.運行時.載入程式.程式集載入上下文.預設探測邏輯以查找依賴項。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399088"
---
# <a name="default-probing"></a>預設探測

實例<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>負責查找程式集的依賴項。 本文介紹了<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例的探測邏輯。

## <a name="host-configured-probing-properties"></a>主機配置的探測屬性

啟動運行時時，執行階段主機提供一組命名探測屬性，這些屬性配置<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>探測路徑。

每個探測屬性都是可選的。 如果存在，則每個屬性都是包含絕對路徑的分隔清單的字串值。 分隔符號在 Windows 上為";"在所有其他平臺上為"："。

|屬性名稱                 |描述  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | 平臺和應用程式程式集檔路徑的清單。 |
|`PLATFORM_RESOURCE_ROOTS`       | 用於搜索附屬資來源程式集的目錄路徑清單。 |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | 用於搜索非託管（本機）庫的目錄路徑清單。        |
|`APP_PATHS`                     | 用於搜索託管程式集的目錄路徑清單。 |
|`APP_NI_PATHS`                  | 用於搜索託管程式集的本機映射的目錄路徑清單。 |

### <a name="how-are-the-properties-populated"></a>屬性是如何填充的？

根據*\<myapp>.deps.json*檔是否存在，填充屬性有兩種主要方案。

- 當*\*.deps.json*檔存在時，將對其進行分析以填充探測屬性。
- 當*\*.deps.json*檔不存在時，假定應用程式的目錄包含所有依賴項。 目錄的內容用於填充探測屬性。

此外，任何引用框架的*\*.deps.json*檔也會得到類似的解析。

最後，環境變數`ADDITIONAL_DEPS`可用於添加其他依賴項。

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>如何查看來自託管代碼的探測屬性？

每個屬性都可以通過從上表中<xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType>調用具有屬性名稱的函數來可用。

### <a name="how-do-i-debug-the-probing-properties-construction"></a>如何調試探測屬性的構造？

啟用某些環境變數時，.NET Core 執行階段主機將輸出有用的跟蹤消息：

|環境變數        |描述  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |啟用跟蹤。|
|`COREHOST_TRACEFILE=<path>` |跟蹤到檔路徑而不是預設`stderr`。|
|`COREHOST_TRACE_VERBOSITY`  |將詳細程度從 1（最低）設置為 4（最高）。|

## <a name="managed-assembly-default-probing"></a>託管程式集預設探測

當探測以查找託管程式集時，請<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>按以下順序查看：

- 與 in<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>`TRUSTED_PLATFORM_ASSEMBLIES`匹配的檔（刪除檔副檔名後）。
- 具有常見檔副檔名`APP_NI_PATHS`的本機映射程式集檔。
- 程式集檔與`APP_PATHS`通用檔副檔名。

## <a name="satellite-resource-assembly-probing"></a>衛星（資源）程式集探測

要查找特定區域性的附屬程式集，構造一組檔路徑。

`PLATFORM_RESOURCE_ROOTS`對於 中的每個路徑，`APP_PATHS`然後，追加<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>字串、目錄分隔符號、<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>字串和副檔名".dll"。

如果存在任何匹配檔，請嘗試載入並返回它。

## <a name="unmanaged-native-library-probing"></a>非託管（本機）庫探測

當探測以查找非託管庫時，`NATIVE_DLL_SEARCH_DIRECTORIES`將搜索 查找匹配的庫。
