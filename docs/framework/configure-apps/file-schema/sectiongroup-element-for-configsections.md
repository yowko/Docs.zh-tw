---
title: <configSections> 的 <sectionGroup> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4e28e8ccea1090e6a5704b541e09dc11681278ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920644"
---
# <a name="sectiongroup-element-for-configsections"></a>\<configSections > 的\<sectionGroup > 元素

定義設定區段的命名空間。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**

## <a name="syntax"></a>語法

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>屬性

|           | 說明 |
| --------- | ----------- |
| **name**  | 必要屬性。<br><br>指定您要定義之區段群組的名稱。 |

## <a name="parent-element"></a>父項目

|     | 說明 |
| --- | ----------- |
| [ **configSections>\<** 元素](configsections-element-for-configuration.md) | 包含設定區段和命名空間宣告。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<區段 >** ](section-element.md) | 包含設定區段宣告。 |

## <a name="remarks"></a>備註

宣告區段群組會建立設定區段的容器標記, 並確保與其他人所定義的設定區段沒有任何命名衝突。 您可以將 **\<sectionGroup >** 專案嵌套在彼此內。

## <a name="example"></a>範例

下列範例示範如何宣告區段群組, 並在區段群組中宣告區段:

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
