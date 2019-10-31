---
title: SingleTagSectionHandler 的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac2d01121e81b545556fb082fa7b82c31cccf9da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118841"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler 的自訂元素

定義自訂設定區段中，由 \<區段 > 元素所定義，並使用 <xref:System.Configuration.SingleTagSectionHandler> 類別的設定。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; *\<sectionName >*

## <a name="syntax"></a>語法

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>屬性

屬性和屬性值是使用者定義的。

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

**\<sectionName >** 元素是由[ **\<configSections >** ](configsections-element-for-configuration.md)元素的[ **\<區段 >** ](section-element.md)標記所定義的自訂元素。 當您呼叫 <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>時，設定系統會傳回 <xref:System.Collections.IDictionary> 物件。

## <a name="example"></a>範例

下列範例會宣告名為 **\<sampleSection >** 的自訂元素，其中包含 <xref:System.Configuration.SingleTagSectionHandler> 類別所讀取的設定：

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

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>請參閱

- [.NET Framework 的設定檔架構](index.md)
