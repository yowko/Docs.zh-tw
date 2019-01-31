---
title: <add> NameValueSectionHandler 和 DictionarySectionHandler 的項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9b421b4bab32c1aae7a6ba7d69b9f4aea2ab99a5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278274"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<新增 > NameValueSectionHandler 和 DictionarySectionHandler 的項目

加入自訂應用程式設定。 每個**\<新增 >** 標記包含索引鍵/值組。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>語法

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>屬性

| 屬性 | 描述 |
| --------- | ----------- |
| **key**   | 必要屬性。<br><br>指定之設定的名稱。 |
| **value** | 必要屬性。<br><br>指定設定的值。 |

## <a name="parent-element"></a>父項目

| 元素 | 描述 |
| ------- | ------------|
| [**\<sectionName >** 項目](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | 定義設定使用的自訂組態區段<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。 |

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

這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。

## <a name="see-also"></a>另請參閱

- [適用於.NET Framework 的組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
