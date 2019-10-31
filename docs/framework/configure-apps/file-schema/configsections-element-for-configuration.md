---
title: <configuration> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6024144b6f12df22369366f04c3cbad02c5011d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119022"
---
# <a name="configsections-element-for-configuration"></a>\<設定的 \<configSections > 元素 >

包含設定區段和命名空間宣告。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp; **\<configSections >**

## <a name="attributes"></a>屬性

None

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [ **\<configuration>** ](configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<區段 >** ](section-element.md) | 包含設定區段宣告。 |
| [ **\<sectionGroup >** ](sectiongroup-element-for-configsections.md) | 定義設定區段的命名空間。 |
| [ **\<remove>** ](remove-element-for-configsections.md) | 移除預先定義的區段或區段群組。 |
| [ **\<clear>** ](clear-element-for-configsections.md) | 清除所有先前定義的區段和區段群組。 |

## <a name="remarks"></a>備註

如果這個元素是在設定檔中，它必須是 **\<設定 >** 元素的第一個子專案。

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

## <a name="see-also"></a>請參閱

- [.NET Framework 的設定檔架構](index.md)
