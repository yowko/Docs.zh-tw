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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155345"
---
# <a name="configsections-element-for-configuration"></a>\<configuration> 的 \<configSections> 項目

包含設定區段和命名空間宣告。

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<section>**](section-element.md) | 包含設定區段宣告。 |
| [**\<sectionGroup>**](sectiongroup-element-for-configsections.md) | 定義設定區段的命名空間。 |
| [**\<remove>**](remove-element-for-configsections.md) | 移除預先定義的區段或區段群組。 |
| [**\<clear>**](clear-element-for-configsections.md) | 清除所有先前定義的區段和區段群組。 |

## <a name="remarks"></a>備註

如果這個元素是在設定檔中，它必須是元素的第一個子專案 **\<configuration>** 。

## <a name="example"></a>範例

下列範例顯示如何定義設定區段，並定義該區段的設定：

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

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
