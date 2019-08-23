---
title: <configuration> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927663"
---
# <a name="configsections-element-for-configuration"></a>\<configuration > 的\<configSections > 元素

包含設定區段和命名空間宣告。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<configSections>**

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父項目

|     | 說明 |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<區段 >** ](section-element.md) | 包含設定區段宣告。 |
| [ **\<sectionGroup>** ](sectiongroup-element-for-configsections.md) | 定義設定區段的命名空間。 |
| [ **\<remove>** ](remove-element-for-configsections.md) | 移除預先定義的區段或區段群組。 |
| [ **\<clear>** ](clear-element-for-configsections.md) | 清除所有先前定義的區段和區段群組。 |

## <a name="remarks"></a>備註

如果此項目是在組態檔中，它必須是第一個子項目 **\<組態>** 項目。

## <a name="example"></a>範例

下列範例顯示如何定義設定區段, 並定義該區段的設定:

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

此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
