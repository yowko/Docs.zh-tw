---
title: '&lt;清除&gt;項目&lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9439e2ac7634b242c9f847346f7dcf265d6ab419
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678001"
---
# <a name="clear-element-for-configsections"></a>\<清除 > 項目\<configSections >

清除所有先前定義的區段和區段群組。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>語法

```xml
<clear/>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **name**  | 必要屬性。<br><br>指定要移除的區段群組之區段的名稱。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<configSections >** 項目](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | 包含組態區段和命名空間宣告。 |

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

**\<清除 >** 項目會從您先前已定義在目前的組態檔中或在組態檔階層架構中較高層級的應用程式移除所有區段和區段群組。

## <a name="example"></a>範例

此範例中定義的機器組態檔案和應用程式組態檔，並示範如何使用**\<清除 >** 清除區段中預先定義的應用程式組態檔中的項目電腦組態檔。

下列的機器組態檔案程式碼會宣告兩個區段 **\<sampleSection >** 並 **\<anotherSampleSection >**，應用程式之前所讀取的來源組態檔：

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

下列應用程式組態檔程式碼會清除所有先前宣告的區段。 應用程式無法使用，或擷取在電腦組態檔中所宣告的各區段的設定。 不過，它可以在這裡使用的設定 **\<anotherSection >** 因為它的來源之後**\<清除 >** 項目。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>組態檔

這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。

## <a name="see-also"></a>另請參閱

- [適用於.NET Framework 的組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
