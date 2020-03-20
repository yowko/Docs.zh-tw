---
title: 單一標籤節處理常式的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 04360a796b18cf1e414f1f84bff247a1e9d8ef9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155150"
---
# <a name="custom-element-for-singletagsectionhandler"></a>單一標籤節處理常式的自訂元素

在由\<節>元素定義的自訂配置部分中定義設置，並使用類<xref:System.Configuration.SingleTagSectionHandler>。

&nbsp; [** \<配置>**](configuration-element.md)&nbsp;*節名稱>\<*

## <a name="syntax"></a>語法

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>屬性

屬性和屬性值是使用者定義的。

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<配置>**](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

** \<節名稱>** 元素是由[**\<配置節>**](configsections-element-for-configuration.md)元素中[**\<>**](section-element.md)標記定義的自訂元素。 當您調用<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>時，<xref:System.Collections.IDictionary>配置系統將返回一個物件。

## <a name="example"></a>範例

以下示例聲明一個稱為**\<示例節>** 的自訂元素，其中包含類讀取的<xref:System.Configuration.SingleTagSectionHandler>設置：

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

此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。

## <a name="see-also"></a>另請參閱

- [.NET 框架的設定檔架構](index.md)
