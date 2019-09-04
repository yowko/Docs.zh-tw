---
title: 預設探查-.NET Core
description: 瞭解 .net Core 的<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>探查邏輯以找出相依性。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 020b1d0342ae822021905d2e749037f45031eb22
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234640"
---
# <a name="default-probing"></a>預設探查

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例負責尋找元件的相依性。 本文說明<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例的探查邏輯。

## <a name="host-configured-probing-properties"></a>主機設定的探查屬性

當執行時間啟動時, 執行時間主機會提供一組命名探查屬性來<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>設定探查路徑。

每個探查屬性都是選擇性的。  如果有, 每個屬性都是字串值, 其中包含絕對路徑的分隔清單。 分隔符號是 Windows 上的 '; ' 和所有其他平臺上的 ': '。

|屬性名稱                 |描述  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | 平臺和應用程式元件檔案路徑的清單。 |
|`PLATFORM_RESOURCE_ROOTS`       | 要搜尋附屬資源元件的目錄路徑清單。 |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | 要搜尋非受控 (原生) 程式庫的目錄路徑清單。        |
|`APP_PATHS`                     | 要搜尋 managed 元件的目錄路徑清單 |
|`APP_NI_PATHS`                  | 要搜尋 managed 元件原生映射的目錄路徑清單。 |

### <a name="how-are-the-properties-populated"></a>屬性的填入方式為何？

根據`<myapp>.deps.json`檔案是否存在, 擴充屬性有兩個主要案例。

- `*.deps.json`當檔案存在時, 它會經過剖析以填入探查屬性。
- `*.deps.json`當檔案不存在時, 會假設應用程式的目錄包含所有相依性。 目錄的內容是用來填入探查屬性。

此外, 任何`*.deps.json`參考架構的檔案也會以同樣的方式進行剖析。

最後, 環境變數`ADDITIONAL_DEPS`可以用來新增其他相依性。

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>如何? 看到來自受控碼的探查屬性？

您可以使用上表中的<xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType>屬性名稱呼叫函式, 以取得每個屬性。

### <a name="how-do-i-debug-the-probing-properties-construction"></a>如何? debug 探查屬性的結構嗎？

啟用特定環境變數時, .NET Core 執行時間主機將會輸出有用的追蹤訊息:

|環境變數        |描述  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |啟用追蹤。|
|`COREHOST_TRACEFILE=<path>` |追蹤檔案路徑, 而不是預設值`stderr`。|
|`COREHOST_TRACE_VERBOSITY`  |設定從 1 (最低) 到 4 (最高) 的詳細資訊。|

## <a name="managed-assembly-default-probing"></a>受管理元件的預設探查

當探查找出 managed 元件時, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>會依序查看:
- 符合中<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES`的檔案 (移除副檔名之後)。
- 中`APP_NI_PATHS`的原生映射元件檔案與通用副檔名。
- 中`APP_PATHS`的元件檔和通用副檔名。

## <a name="satellite-resource-assembly-probing"></a>附屬 (資源) 元件探查

若要尋找特定文化特性的附屬元件, 請建立一組檔案路徑。

針對`PLATFORM_RESOURCE_ROOTS` <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 和中<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>的每個路徑,附加字串、目錄分隔符號、字串和副檔名'.dll'。`APP_PATHS`

如果有任何相符的檔案存在, 請嘗試載入並傳回它。

## <a name="unmanaged-native-library-probing"></a>非受控 (原生) 程式庫探查

當探查找出非受控程式庫時`NATIVE_DLL_SEARCH_DIRECTORIES` , 會搜尋尋找相符的程式庫。
