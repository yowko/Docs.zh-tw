---
title: <clear>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214748"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<clear>NameValueSectionHandler 和 DictionarySectionHandler 的元素

清除區段中所有先前定義的設定。

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>語法

```xml
<clear />
```

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ------------|
| [**\<sectionName>** 元素](custom-element-2.md) | 定義使用和類別之自訂設定區段的設定 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

您可以使用 **\<clear>** 元素，從您的應用程式中移除在設定檔階層中較高層級定義的所有設定。

## <a name="example"></a>範例

這個範例會定義電腦設定檔和應用程式佈建檔，並示範如何使用 **\<clear>** 應用程式佈建檔中的專案，清除電腦設定檔中先前定義的區段。

下列電腦設定檔程式碼會宣告區段 **\<mySection>** ：

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

下列應用程式佈建檔案代碼會從移除所有設定 **\<mySection>** 。 應用程式無法在電腦設定檔的區段中，取得在中宣告的任何設定 **\<mySection>** 。

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
