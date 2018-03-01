---
title: "&lt;移除&gt;元素&lt;c&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf2cb49fbeb01ad176a1d24d711cebc97ba14004
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-configsections"></a>\<移除 > 項目\<c >

預先定義的區段或區段群組中移除。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<c >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<移除 >**

## <a name="syntax"></a>語法

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **name**  | 必要屬性。<br><br>指定區段或要移除的區段群組的名稱。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<c >**項目](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | 包含組態區段和命名空間宣告。 |

# <a name="child-elements"></a>子元素

無

## <a name="remarks"></a>備註

您可以使用**\<移除 >**項目區段或區段群組中移除您已在組態檔階層架構中較高層級定義的應用程式。

## <a name="example"></a>範例

下列範例示範如何使用**\<移除 >**應用程式組態檔移除電腦組態檔中預先定義的區段中的項目。

下列的機器組態檔案程式碼會宣告區段 **\<sampleSection >**:

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

下列應用程式組態檔程式碼會移除 **\<sampleSection >** > 一節。 移除後，應用程式無法擷取中的設定 **\<sampleSection >**。

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>組態檔

此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。

## <a name="see-also"></a>另請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
