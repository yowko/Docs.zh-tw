---
title: NameValueSectionHandler 和 DictionarySectionHandler 的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215483"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler 和 DictionarySectionHandler 的自訂元素

定義使用 <xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 類別之自訂設定區段的設定。

[ **\<configuration>** ](configuration-element.md)\
&nbsp;&nbsp; **\<sectionName >**

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<新增**](add-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 的 >  | 新增自訂應用程式設定。 |
| [ **\<移除**](remove-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 的 > | 移除先前定義的設定。 |
| [ **\<清除**](clear-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 的 > | 清除區段中所有先前定義的設定。 |

## <a name="remarks"></a>備註

**\<SectionName>** 項目是所定義的自訂項目 **\<區段>** 標記中 **\<configSections>** 項目。

下表顯示每個設定區段處理常式的 ConfigurationSettings GetConfig 方法所傳回的物件類型：

| 設定區段處理常式                        | 傳回類型                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>範例

下列範例顯示如何宣告使用 <xref:System.Configuration.DictionarySectionHandler> 和 <xref:System.Configuration.NameValueSectionHandler> 類別的區段。

第一個自訂元素是 **\<dictionarySample >** ，其中包含 `System.dll` 元件中 <xref:System.Configuration.DictionarySectionHandler> 類別所讀取的設定。 第二個自訂元素是 **\<mySection >** ，其中包含 `System.dll` 元件中 <xref:System.Configuration.NameValueSectionHandler> 類別所讀取的設定。

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

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
