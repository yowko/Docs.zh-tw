---
title: 單一分頁處理程式的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635392"
---
# <a name="custom-element-for-singletagsectionhandler"></a>單一分頁處理程式的自訂元素

在由\<節>元素定義的自訂設定部分中定義設定,並使用類<xref:System.Configuration.SingleTagSectionHandler>。

&nbsp;&nbsp;節名稱>[** \<**](configuration-element.md)* \<*

## <a name="syntax"></a>語法

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>屬性

屬性和屬性值是使用者定義的。

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<設定>**](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

節名稱>元素是由[**\<配置節>**](configsections-element-for-configuration.md)元素中[**\<>**](section-element.md)標記定義的自定義元素。 ** \<** 當您呼叫<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>時<xref:System.Collections.IDictionary>, 配置系統將傳回一個物件。

## <a name="example"></a>範例

以下範例聲明一個稱為**\<範例節>** 的自定義元素,其中包含類讀<xref:System.Configuration.SingleTagSectionHandler>取的 設定:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式設定檔、計算機設定檔 *(Machine.config)* 和*Web.config*檔,這些檔案不在應用程式目錄等級。

## <a name="see-also"></a>另請參閱

- [.NET 架構的設定檔架構](index.md)
