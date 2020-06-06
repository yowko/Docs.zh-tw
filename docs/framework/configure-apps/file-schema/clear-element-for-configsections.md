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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155423"
---
# <a name="clear-element-for-configsections"></a>\<configSections> 的 \<clear> 項目

清除所有先前定義的區段和區段群組。

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>語法

```xml
<clear/>
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

**\<clear>** 元素會從您的應用程式移除先前在目前設定檔或設定檔階層中較高層級定義的所有區段和區段群組。

## <a name="example"></a>範例

這個範例會定義電腦設定檔和應用程式佈建檔，並示範如何使用 **\<clear>** 應用程式佈建檔中的專案，清除電腦設定檔中先前定義的區段。

下列電腦設定檔程式碼會宣告兩個區段，分別 **\<sampleSection>** **\<anotherSampleSection>** 是在應用程式佈建檔之前讀取：

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

下列應用程式佈建檔程式碼會清除所有先前宣告的區段。 應用程式無法在電腦設定檔中宣告的任一區段中使用或抓取設定。 不過，它可以使用的設定， **\<anotherSection>** 因為它是在 **\<clear>** 元素之後。

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

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](index.md)
