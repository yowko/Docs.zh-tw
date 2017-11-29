---
title: "&lt;清除&gt;NameValueSectionHandler DictionarySectionHandler 的項目"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e91c3d9693cf656a8c56c82d1997f74c2b3d64c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<清除 > NameValueSectionHandler DictionarySectionHandler 的項目

清除所有先前定義的設定區段中。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<清除 >**

## <a name="syntax"></a>語法

```xml
<clear />
```

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父項目

|     | 說明 |
| --- | ------------|
| [**\<sectionName >**項目](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | 定義自訂組態區段，使用設定<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。 |

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

您可以使用**\<清除 >**項目移除您已在組態檔階層架構中較高層級定義的應用程式中的所有設定。

## <a name="example"></a>範例

此範例中定義的機器組態檔案和應用程式組態檔，並示範如何使用**\<清除 >**應用程式組態檔中清除先前定義的區段中的項目電腦組態檔。

下列的機器組態檔案程式碼會宣告區段 **\<mySection >**:

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

下列應用程式組態檔程式碼中移除的所有設定 **\<mySection >**。 應用程式無法擷取的任何設定中所宣告的中 **\<mySection >**機器組態檔區段。

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。

## <a name="see-also"></a>請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
