---
title: "&lt;區段&gt;項目"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8ed8b0211c8366d799fe158d91dcb42f92ad0cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="section-element"></a>\<區段 > 項目

包含組態區段宣告。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<c >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<區段 >**

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<c >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<區段 >**

## <a name="syntax"></a>語法

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>必要屬性

|           | 說明 |
| --------- | ----------- |
| **name**  | 指定之組態區段的名稱。 |
| **type**  | 指定從組態檔讀取區段的組態區段處理常式類別的名稱。 類型值的語法 」 fully-qualified-section-handler-class-name 簡單組件名稱 」。 簡單的組件名稱是根檔案名稱，而不*.dll*檔案副檔名。 |

## <a name="optional-attributes"></a>選擇性屬性

下列屬性就會只適用於 ASP.NET 應用程式。 組態系統會忽略這些屬性，其他應用程式類型。

|                     | 說明 |
| ------------------- | ----------- |
| **allowDefinition** | 指定可以在使用中的區段的組態檔。 使用下列其中一個值：<br><br>**每個地方**<br>允許以用於任何組態檔區段。 這是預設值。<br>**MachineOnly**<br>允許區段只能用在電腦組態檔 (*Machine.config*)。<br>**MachineToApplication**<br>允許用在電腦組態檔或應用程式組態檔區段。 |
| **allowLocation**   | 決定是否可以在使用區段**\<位置 >**項目。 使用下列其中一個值：<br><br>**true**<br>允許區段內使用**\<位置 >**項目。 這是預設值。<br>**false**<br>不允許使用於區段**\<位置 >**項目。 |

## <a name="parent-elements"></a>父元素

|     | 說明 |
| --- | ----------- |
| [**\<c >**項目](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | 包含組態區段和命名空間宣告。 |
| [**\<sectionGroup >**項目](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | 定義組態區段的命名空間。 |

> [!NOTE]
> A **\<區段 >**元素為子元素中的其中一個 **\<c >**或 **\<sectionGroup >**但不是兩者。

## <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

本質上宣告的組態區段會定義組態檔的新項目。 新的項目包含組態區段處理常式的設定 (也就是一個類別，實作<xref:System.Configuration.IConfigurationSectionHandler>介面) 讀取。 屬性和子項目的區段中定義取決於您用來讀取您的設定區段處理常式。

宣告中的組態區段處理常式*Machine.config*檔案可讓您在該電腦上任何應用程式組態檔中使用的組態區段除非**allowDefinition**屬性指定不同的情況。

## <a name="example"></a>範例

下列範例會示範如何定義組態區段，並定義區段的設定：

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

此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。

## <a name="see-also"></a>請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
