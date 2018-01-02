---
title: "SingleTagSectionHandler 自訂項目"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ee722c7d5db9d58ab1a91f4b1299912981510af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler 自訂項目

定義中所定義的自訂組態區段的設定 <section> 項目，並使用<xref:System.Configuration.SingleTagSectionHandler>類別。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName >*

## <a name="syntax"></a>語法

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>屬性

屬性和屬性值是使用者定義。

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

 **\<SectionName >**項目是所定義的自訂項目[ **\<區段 >** ](~/docs/framework/configure-apps/file-schema/section-element.md)標記[ **\<c >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)項目。 組態系統會傳回<xref:System.Collections.IDictionary>物件時呼叫<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>。

## <a name="example"></a>範例

下列範例會宣告稱為自訂項目 **\<sampleSection >** ，其中包含所讀取的設定<xref:System.Configuration.SingleTagSectionHandler>類別：

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>組態檔

此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。

## <a name="see-also"></a>另請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
