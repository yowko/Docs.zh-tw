---
title: 預設探查-.NET Core
description: 介紹 .NET Core 的 AssemblyLoadCoNtext，以找出相依性的預設探查邏輯。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608420"
---
# <a name="default-probing"></a>預設探查

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>實例負責找出元件的相依性。 本文描述 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 實例的探查邏輯。

## <a name="host-configured-probing-properties"></a>主控制項設定的探查屬性

當執行時間啟動時，執行時間主機會提供一組可設定探查路徑的命名探查屬性 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 。

每個探查屬性都是選擇性的。 如果有的話，每個屬性都是包含絕對路徑的分隔清單的字串值。 分隔符號是 Windows 上的 '; '，其他所有平臺上的 '： '。

|屬性名稱                 |描述  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | 平臺和應用程式元件檔案路徑的清單。 |
|`PLATFORM_RESOURCE_ROOTS`       | 搜尋附屬資源元件的目錄路徑清單。 |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | 搜尋非受控 (原生) 程式庫的目錄路徑清單。        |
|`APP_PATHS`                     | 搜尋 managed 元件的目錄路徑清單。 |
|`APP_NI_PATHS`                  | 目錄路徑清單，以搜尋 managed 元件的原生映射。 |

### <a name="how-are-the-properties-populated"></a>屬性的填入方式為何？

有兩個主要案例可以根據檔案* \<myapp> 上的.deps.js*是否存在來填入屬性。

- 當* \*.deps.json*檔案存在時，會將它剖析為填入探查屬性。
- 當檔案* \*.deps.js*不存在時，會假設應用程式的目錄包含所有相依性。 目錄的內容會用來填入探查屬性。

此外，任何參考架構的檔案* \*.deps.js*也會以同樣的方式進行剖析。

最後，您 `ADDITIONAL_DEPS` 可以使用環境變數來新增其他相依性。  `dotnet.exe` 也包含 `--additional-deps` 可在應用程式啟動時設定此值的選擇性參數。

`APP_PATHS`和 `APP_NI_PATHS` 屬性預設不會填入，並且會針對大部分的應用程式省略。

您可以透過存取應用程式所使用之檔案上的所有* \*.deps.js*清單 `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` 。

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>如何? 從 managed 程式碼查看探查屬性？

<xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType>使用上表中的屬性名稱呼叫函式，即可取得每個屬性。

### <a name="how-do-i-debug-the-probing-properties-construction"></a>如何? debug 探查屬性的結構？

啟用特定環境變數時，.NET Core 執行時間主機會輸出有用的追蹤訊息：

|環境變數        |描述  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |啟用追蹤。|
|`COREHOST_TRACEFILE=<path>` |追蹤檔案路徑，而不是預設值 `stderr` 。|
|`COREHOST_TRACE_VERBOSITY`  |將詳細資訊從 1 (最低) 設定為 4 (最高) 。|

## <a name="managed-assembly-default-probing"></a>Managed 元件預設探查

探查以找出受管理的元件時，會依 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 序查看：

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` 移除檔案副檔名) 之後，符合 (的檔案。
- 具有通用副檔名的原生映射元件檔 `APP_NI_PATHS` 。
- `APP_PATHS`具有一般副檔名的元件檔。

## <a name="satellite-resource-assembly-probing"></a>附屬 (資源) 元件探查

若要尋找特定文化特性的附屬元件，請建立一組檔案路徑。

針對中的每個路徑 `PLATFORM_RESOURCE_ROOTS` `APP_PATHS` ，然後附加 <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 字串、目錄分隔符號、 <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 字串和副檔名 ' .dll '。

如果有任何相符的檔案存在，請嘗試載入並將其傳回。

## <a name="unmanaged-native-library-probing"></a>非受控 (原生) 程式庫探查

探查以找出未受管理的程式庫時， `NATIVE_DLL_SEARCH_DIRECTORIES` 會搜尋是否有相符的程式庫。
