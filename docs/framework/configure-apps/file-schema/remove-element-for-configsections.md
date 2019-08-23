---
title: <configSections> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4ff9bb537a31e28dbd4b878c1bc04c96262f85ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927463"
---
# <a name="remove-element-for-configsections"></a>\<移除 configSections > 的\<> 元素

移除預先定義的區段或區段群組。

[ **\<configuration>** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**

## <a name="syntax"></a>語法

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>屬性

|           | 說明 |
| --------- | ----------- |
| **name**  | 必要屬性。<br><br>指定要移除之區段或區段群組的名稱。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [ **configSections>\<** 元素](configsections-element-for-configuration.md) | 包含設定區段和命名空間宣告。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

您可以使用 **\<移除>** 區段和區段群組中移除您的應用程式組態檔階層架構中較高層級所定義的項目。

## <a name="example"></a>範例

下列範例示範如何使用 **\<移除>** 應用程式組態檔，以移除先前在電腦組態檔中定義的區段中的項目。

下列電腦設定檔程式碼會宣告 **\<sampleSection >** 區段:

```xml
<!-- Machine.config file -->
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

下列應用程式佈建檔程式碼會移除 **\<sampleSection >** 區段。 移除之後, 應用程式就無法抓取 **\<sampleSection >** 中的設定。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
