---
title: NameValueSectionHandler 和 DictionarySectionHandler 的 <remove> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc1519a794e24e04074dd2a674ecc2c0f3666521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118570"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<移除 NameValueSectionHandler 和 DictionarySectionHandler 的 > 元素

移除先前定義的設定。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**

## <a name="syntax"></a>語法

```xml
<add remove="key" />
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **key**   | 必要屬性。<br><br>指定要移除之設定的名稱。 |

## <a name="parent-element"></a>父項目

| 項目 | 描述 |
| ------- | ------------|
| [ **\<sectionName >** 元素](custom-element-2.md) | 定義使用 <xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 類別之自訂設定區段的設定。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

您可以使用 **\<移除 >** 元素，從您的應用程式中移除在設定檔階層中較高層級定義的設定。

## <a name="example"></a>範例

下列範例示範如何使用應用程式佈建檔中的 **\<移除 >** 元素，以移除先前在電腦設定檔中定義的設定。

下列電腦設定檔程式碼會宣告 **\<mySection >** 區段，並在其中加入兩個設定，`key1` 和 `key2`：

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

下列應用程式佈建檔案代碼會從 **\<mySection >** 移除 `key2` 設定：

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

## <a name="see-also"></a>請參閱

- [.NET Framework 的設定檔架構](index.md)
