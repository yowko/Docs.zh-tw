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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7147173dc9f132fa2dd14d20526d59927a183bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115259"
---
# <a name="section-element"></a>\<區段 > 元素

包含設定區段宣告。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<區段 >**

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup >** ](sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**區段 >**

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
| **name**  | 指定設定區段的名稱。 |
| **type**  | 指定在設定檔案中讀取區段的設定區段處理常式類別名稱。 類型值的語法為「完整區段-處理常式類別名稱，簡單元件名稱」。 簡單元件名稱是不含 *.dll*副檔名的根檔案名。 |

## <a name="optional-attributes"></a>選擇性屬性

下列屬性僅適用于 ASP.NET 應用程式。 設定系統會忽略其他應用程式類型的這些屬性。

|                     | 描述 |
| ------------------- | ----------- |
| **allowDefinition** | 指定區段可以用於哪一個設定檔。 使用下列其中一個值：<br><br>**位置**<br>允許在任何設定檔案中使用區段。 這是預設值。<br>**MachineOnly**<br>允許區段僅用於電腦設定檔（*machine.config*）。<br>**MachineToApplication**<br>允許在電腦設定檔或應用程式佈建檔中使用區段。 |
| **allowLocation**   | 判斷區段是否可以在 **\<位置 >** 元素中使用。 使用下列其中一個值：<br><br>**true**<br>允許在 **\<位置 >** 元素中使用區段。 這是預設值。<br>**false**<br>不允許在 **\<位置 >** 元素中使用區段。 |

## <a name="parent-elements"></a>父元素

|     | 描述 |
| --- | ----------- |
| [ **\<configSections >** 元素](configsections-element-for-configuration.md) | 包含設定區段和命名空間宣告。 |
| [ **\<sectionGroup >** 元素](sectiongroup-element-for-configsections.md) | 定義設定區段的命名空間。 |

> [!NOTE]
> **\<區段 >** 元素是 **\<configSections >** 或 **\<sectionGroup >** （而非兩者）的子項目。

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

宣告設定區段基本上會定義設定檔的新元素。 新專案包含設定區段處理常式（也就是實作為 <xref:System.Configuration.IConfigurationSectionHandler> 介面的類別）所讀取的設定。 您所定義之區段的屬性和子專案，取決於您用來讀取設定的區段處理常式。

在*machine.config*檔案中宣告設定區段處理常式，可讓您在該電腦上的任何應用程式佈建檔中使用 configuration 區段，除非**allowDefinition**屬性另行指定。

## <a name="example"></a>範例

下列範例顯示如何定義設定區段，並定義該區段的設定：

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

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>請參閱

- [.NET Framework 的設定檔架構](index.md)
