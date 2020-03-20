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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154526"
---
# <a name="remove-element-for-configsections"></a>\<刪除>元素以\<進行配置>

刪除預定義的節或節組。

[**\<配置>**](configuration-element.md)\
&nbsp;&nbsp;[**\<配置部分>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<刪除>**

## <a name="syntax"></a>語法

```xml
<remove name="section name or section group name" />
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

可以使用**\<刪除>** 元素從應用程式中從設定檔層次結構中較高級別定義的節和節組中刪除。

## <a name="example"></a>範例

下面的示例演示如何使用應用程式佈建檔中的**\<刪除>** 元素來刪除以前在電腦設定檔中定義的部分。

以下電腦設定檔代碼聲明節**\<示例節>**：

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

以下應用程式佈建檔代碼將刪除**\<示例節>** 部分。 刪除後，應用程式無法檢索**\<示例節>** 中的設置。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。

## <a name="see-also"></a>另請參閱

- [.NET 框架的設定檔架構](index.md)
