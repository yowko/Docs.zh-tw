---
title: NameValueSectionHandler 和 DictionarySectionHandler 自訂項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 3a16952c5cd3759873faeb0fce45b8aa5170b083
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler 和 DictionarySectionHandler 自訂項目

定義自訂組態區段，使用設定<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<新增 >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md)如<xref:System.Configuration.NameValueSectionHandler>和 <xref:System.Configuration.DictionarySectionHandler>  | 加入自訂應用程式設定。 |
| [**\<移除 >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md)如<xref:System.Configuration.NameValueSectionHandler>和 <xref:System.Configuration.DictionarySectionHandler> |    移除先前定義的設定。 |
| [**\<清除 >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md)如<xref:System.Configuration.NameValueSectionHandler>和 <xref:System.Configuration.DictionarySectionHandler> | 清除所有先前定義的設定區段中。 |

## <a name="remarks"></a>備註

**\<SectionName >** 項目是所定義的自訂項目**\<區段 >** 標記 **\<c >** 項目。

下表顯示每個組態區段處理常式會傳回物件 ConfigurationSettings.GetConfig 方法的型別：

| 組態區段處理常式                        | 傳回型別                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>範例

下列範例示範如何宣告使用的區段<xref:System.Configuration.DictionarySectionHandler>和<xref:System.Configuration.NameValueSectionHandler>類別。 

第一個自訂的元素是 **\<dictionarySample >**，其中包含所讀取的設定<xref:System.Configuration.DictionarySectionHandler>類別`System.dll`組件。 第二個自訂項目，則 **\<mySection >**，其中包含所讀取的設定<xref:System.Configuration.NameValueSectionHandler>類別`System.dll`組件。

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。

## <a name="see-also"></a>另請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
