---
title: <configuration> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155345"
---
# <a name="configsections-element-for-configuration"></a>\<配置>元素，用於\<配置>

包含配置部分和命名空間聲明。

&nbsp; [** \<配置>**](configuration-element.md)&nbsp;**配置>\<**

## <a name="attributes"></a>屬性

None

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<配置>**](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<第>節**](section-element.md) | 包含配置部分聲明。 |
| [**\<部分組>**](sectiongroup-element-for-configsections.md) | 為配置部分定義命名空間。 |
| [**\<刪除>**](remove-element-for-configsections.md) | 刪除預定義的節或節組。 |
| [**\<明確>**](clear-element-for-configsections.md) | 清除以前定義的所有節和節組。 |

## <a name="remarks"></a>備註

如果此元素位於設定檔中，則它必須是**\<配置>** 元素的第一個子項目。

## <a name="example"></a>範例

下面的示例演示如何定義配置部分並定義該部分的設置：

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

此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。

## <a name="see-also"></a>另請參閱

- [.NET 框架的設定檔架構](index.md)
