---
title: <configSections> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154526"
---
# <a name="remove-element-for-configsections"></a>\<configSections> 的 \<remove> 項目

移除預先定義的區段或區段群組。

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>語法

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **name**  | 必要屬性。<br><br>指定要移除之區段或區段群組的名稱。 |

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configSections>** 元素](configsections-element-for-configuration.md) | 包含設定區段和命名空間宣告。 |

## <a name="child-elements"></a>子元素

None

## <a name="remarks"></a>備註

您可以使用 **\<remove>** 元素，從您的應用程式移除在設定檔階層中較高層級定義的區段和區段群組。

## <a name="example"></a>範例

下列範例顯示如何使用 **\<remove>** 應用程式佈建檔中的專案，來移除先前在電腦設定檔中定義的區段。

下列電腦設定檔程式碼會宣告區段 **\<sampleSection>** ：

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

下列應用程式佈建檔案代碼會移除 **\<sampleSection>** 區段。 移除之後，應用程式就無法抓取中的設定 **\<sampleSection>** 。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
