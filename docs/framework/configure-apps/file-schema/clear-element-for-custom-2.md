---
title: <clear>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: fbb689db4abc5d59729d9a4d9807a02a0983d40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927701"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<清除> NameValueSectionHandler 和 DictionarySectionHandler 的項目

清除區段中所有先前定義的設定。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>語法

```xml
<clear />
```

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ------------|
| [ **sectionName>\<** 元素](custom-element-2.md) | 定義使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別之自訂設定區段的設定。 |

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

您可以使用 **\<清除>** 来移除您已定義在組態檔階層架構中較高層級的應用程式中的所有設定項目。

## <a name="example"></a>範例

此範例中定義的機器組態檔案和應用程式組態檔，並示範如何使用 **\<清除>** 清除區段中預先定義的應用程式組態檔中的項目電腦組態檔。

下列電腦設定檔程式碼會宣告 **\<mySection >** 區段:

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

下列應用程式佈建檔案代碼會從 **\<mySection >** 移除所有設定。 應用程式無法在電腦設定檔的 **\<mySection >** 區段中, 取得在中宣告的任何設定。

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
