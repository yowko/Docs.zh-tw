---
title: '&lt;新增&gt;NameValueSectionHandler DictionarySectionHandler 的項目'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: aeb3e3a4be201369ca2df8d231498dd2400d3c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<新增 > NameValueSectionHandler DictionarySectionHandler 的項目

加入自訂應用程式設定。 每個**\<新增 >** 標記包含的索引鍵/值組。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<新增 >**

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
| [**\<sectionName >** 項目](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | 定義自訂組態區段，使用設定<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。 |

## <a name="child-elements"></a>子元素

無

## <a name="example"></a>範例

下列範例示範如何定義自訂組態區段，然後使用**\<新增 >** 放一節中的設定項目：

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

此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。

## <a name="see-also"></a>另請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
