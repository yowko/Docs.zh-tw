---
title: <configSections> 的 <clear> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155423"
---
# <a name="clear-element-for-configsections"></a>\<用於\<配置>的透明>元素

清除以前定義的所有節和節組。

&nbsp; [** \<配置>**](configuration-element.md)&nbsp;&nbsp;**配置>\<清晰的>** [** \< **](configsections-element-for-configuration.md) &nbsp; &nbsp; &nbsp;

## <a name="syntax"></a>語法

```xml
<clear/>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **名稱**  | 必要屬性。<br><br>指定要刪除的節或節組的名稱。 |

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [** \<配置部分>** 元素](configsections-element-for-configuration.md) | 包含配置部分和命名空間聲明。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

** \<清除>** 元素從應用程式中刪除當前設定檔前面或設定檔層次結構中較高級別定義的所有節和節組。

## <a name="example"></a>範例

本示例定義電腦設定檔和應用程式佈建檔，並演示如何在應用程式佈建檔中使用**\<清除>** 元素來清除以前在電腦設定檔中定義的部分。

以下電腦設定檔代碼聲明兩個部分，**\<示例節>****\<和另一個Sample節>**，在應用程式佈建檔之前讀取：

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

以下應用程式佈建檔代碼清除以前聲明的所有部分。 應用程式無法使用或檢索在電腦設定檔中聲明的任一部分中的設置。 但是，它可以使用**\<另一節>** 設置，因為它在**\<明確>** 元素之後出現。

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

此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。

## <a name="see-also"></a>另請參閱

- [.NET 框架的設定檔架構](index.md)
