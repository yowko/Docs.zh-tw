---
title: <remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920953"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<移除 NameValueSectionHandler 和 DictionarySectionHandler > 元素

移除先前定義的設定。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**

## <a name="syntax"></a>語法

```xml
<add remove="key" />
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **key**   | 必要屬性。<br><br>指定要移除之設定的名稱。 |

## <a name="parent-element"></a>父項目

| 項目 | 說明 |
| ------- | ------------|
| [ **sectionName>\<** 元素](custom-element-2.md) | 定義使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別之自訂設定區段的設定。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

您可以使用 **\<移除>** 來移除您已定義在組態檔階層架構中較高層級的應用程式設定的項目。

## <a name="example"></a>範例

下列範例示範如何使用 **\<移除>** 應用程式組態檔中移除先前在電腦組態檔中定義的設定項目。

下列電腦設定檔程式碼會宣告區段 **\<mySection >** 並在其中`key1`新增`key2`兩個設定:

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

下列應用程式佈建檔案代碼會`key2`從 **\<mySection >** 移除設定:

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
