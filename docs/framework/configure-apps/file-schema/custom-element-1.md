---
title: SingleTagSectionHandler 的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635392"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler 的自訂元素

定義自訂設定區段中，由 \<section> 元素定義並使用類別的設定 <xref:System.Configuration.SingleTagSectionHandler> 。

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>語法

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>屬性

屬性和屬性值是使用者定義的。

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

**\<sectionName>** 元素是由專案中的標記所定義的自訂元素 [**\<section>**](section-element.md) [**\<configSections>**](configsections-element-for-configuration.md) 。 <xref:System.Collections.IDictionary>當您呼叫時，設定系統會傳回物件 <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> 。

## <a name="example"></a>範例

下列範例會宣告名為的自訂元素 **\<sampleSection>** ，其中包含類別所讀取的設定 <xref:System.Configuration.SingleTagSectionHandler> ：

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

此專案可用於應用程式佈建檔 *、電腦設定檔（machine.config*），以及不在應用程式目錄層級的*web.config*檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
