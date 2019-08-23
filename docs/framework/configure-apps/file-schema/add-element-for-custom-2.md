---
title: <add>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921343"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<新增> NameValueSectionHandler 和 DictionarySectionHandler 的項目

新增自訂應用程式設定。 每個 **\<新增>** 標記包含索引鍵/值組。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**

## <a name="syntax"></a>語法

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>屬性

| 屬性 | 描述 |
| --------- | ----------- |
| **key**   | 必要屬性。<br><br>指定設定的名稱。 |
| **value** | 必要屬性。<br><br>指定設定的值。 |

## <a name="parent-element"></a>父項目

| 項目 | 描述 |
| ------- | ------------|
| [ **sectionName>\<** 元素](custom-element-2.md) | 定義使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別之自訂設定區段的設定。 |

## <a name="child-elements"></a>子元素

無

## <a name="example"></a>範例

下列範例示範如何定義自訂組態區段，然後使用 **\<新增>** 放一節中的設定項目：

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
