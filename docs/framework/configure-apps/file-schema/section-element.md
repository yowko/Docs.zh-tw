---
title: <section> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 58f823ce0c128f30e361b4a631d41286533b5f0f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259211"
---
# <a name="section-element"></a>\<區段 > 項目

包含組態區段宣告。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a>語法

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>必要屬性

|           | 描述 |
| --------- | ----------- |
| **name**  | 指定的組態區段名稱。 |
| **type**  | 指定讀取組態檔區段的組態區段處理常式類別的名稱。 型別值的語法 」 fully-qualified-section-handler-class-name，簡單組件名稱 」。 簡單的組件名稱是根檔案名稱，而不需要 *.dll*副檔名。 |

## <a name="optional-attributes"></a>選擇性的屬性

以下為屬性只適用於 ASP.NET 應用程式。 組態系統會忽略這些屬性的其他應用程式類型。

|                     | 描述 |
| ------------------- | ----------- |
| **allowDefinition** | 指定區段可以用在哪一個組態檔。 使用下列其中一個值：<br><br>**Everywhere**<br>允許使用任何組態檔中區段。 這是預設值。<br>**MachineOnly**<br>允許區段只能用在電腦組態檔 (*Machine.config*)。<br>**MachineToApplication**<br>允許可用於電腦組態檔或應用程式組態檔區段。 |
| **allowLocation**   | 判斷是否可以使用區段內**\<位置 >** 項目。 使用下列其中一個值：<br><br>**true**<br>允許使用於區段**\<位置 >** 項目。 這是預設值。<br>**false**<br>不允許使用於區段**\<位置 >** 項目。 |

## <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configSections >** 項目](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | 包含組態區段和命名空間宣告。 |
| [**\<sectionGroup>** Element](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | 定義組態區段的命名空間。 |

> [!NOTE]
> A **\<一節 >** 項目是可能的子項目 **\<configSections >** 或 **\<sectionGroup >** 但不是兩者。

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

本質上宣告組態區段會定義組態檔的新項目。 新的項目包含的組態區段處理常式的設定 (也就是一個類別，實作<xref:System.Configuration.IConfigurationSectionHandler>介面) 讀取。 屬性和子項目的區段中定義取決於您用來讀取您的設定區段處理常式。

宣告中的組態區段處理常式*Machine.config*檔可讓您使用 [設定] 區段中任何應用程式組態檔，該電腦上，除非**allowDefinition**屬性指定不同的情況。

## <a name="example"></a>範例

下列範例示範如何定義組態區段，並定義該區段的設定：

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>組態檔

這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。

## <a name="see-also"></a>另請參閱

- [適用於.NET Framework 的組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
