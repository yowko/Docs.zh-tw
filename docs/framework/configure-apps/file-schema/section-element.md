---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153722"
---
# <a name="section-element"></a>\<節>元素

包含配置部分聲明。

[**\<配置>**](configuration-element.md)\
&nbsp;&nbsp;[**\<配置部分>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<第>節**

[**\<配置>**](configuration-element.md)\
&nbsp;&nbsp;[**\<配置部分>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<部分組>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<第>節**

## <a name="syntax"></a>語法

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>必要的屬性

|           | 描述 |
| --------- | ----------- |
| **名稱**  | 指定配置部分的名稱。 |
| **型別**  | 指定從設定檔讀取節的配置節處理常式類的名稱。 類型值具有語法"完全限定的截面處理常式-類名稱，簡單程式集名稱"。 簡單的程式集名稱是沒有 *.dll*檔副檔名的根檔案名。 |

## <a name="optional-attributes"></a>可選屬性

以下屬性僅適用于ASP.NET應用程式。 配置系統忽略這些屬性的其他應用程式類型。

|                     | 描述 |
| ------------------- | ----------- |
| **允許定義** | 指定該節可以使用的設定檔。 請使用下列其中一個值：<br><br>**所有位置**<br>允許在任何設定檔中使用該節。 這是預設值。<br>**僅限機器**<br>允許僅在機器設定檔 （*機器.config）* 中使用該部分。<br>**機器應用**<br>允許在電腦設定檔或應用程式佈建檔中使用節。 |
| **允許定位**   | 確定是否可以在**\<位置>** 元素中使用節。 請使用下列其中一個值：<br><br>**true**<br>允許在**\<位置>** 元素中使用節。 這是預設值。<br>**false**<br>不允許在**\<位置>** 元素中使用節。 |

## <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| [** \<配置部分>** 元素](configsections-element-for-configuration.md) | 包含配置部分和命名空間聲明。 |
| [第>節組**\< **元素](sectiongroup-element-for-configsections.md) | 為配置部分定義命名空間。 |

> [!NOTE]
> ** \<>元素的節**是**\<配置">"** 或**\<"組組">** 的子項目，但不能同時提供兩者。

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

聲明配置部分實質上定義設定檔的新元素。 新元素包含配置節處理常式（即實現介面的類）讀取的<xref:System.Configuration.IConfigurationSectionHandler>設置。 定義的節的屬性和子項目取決於用於讀取設置的節處理常式。

在*Machine.config 檔中*聲明配置部分處理常式使您能夠在該電腦上的任何應用程式佈建檔中使用配置節，除非**allowDefinition**屬性另有指定。

## <a name="example"></a>範例

下面的示例演示如何定義配置部分並定義該部分的設置：

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

此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。

## <a name="see-also"></a>另請參閱

- [.NET 框架的設定檔架構](index.md)
