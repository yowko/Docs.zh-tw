---
title: <remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214761"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素

移除先前定義的設定。

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>語法

```xml
<add remove="key" />
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **key**   | 必要屬性。<br><br>指定要移除之設定的名稱。 |

## <a name="parent-element"></a>父元素

| 元素 | 描述 |
| ------- | ------------|
| [**\<sectionName>** 元素](custom-element-2.md) | 定義使用和類別之自訂設定區段的設定 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

您可以使用 **\<remove>** 元素，從您的應用程式中移除在設定檔階層中較高層級定義的設定。

## <a name="example"></a>範例

下列範例顯示如何使用 **\<remove>** 應用程式佈建檔中的專案，來移除先前在電腦設定檔中定義的設定。

下列電腦設定檔程式碼會宣告區段， **\<mySection>** 並在其中新增兩個設定 `key1` `key2` ：

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

下列應用程式佈建檔案代碼會 `key2` 從移除設定 **\<mySection>** ：

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
