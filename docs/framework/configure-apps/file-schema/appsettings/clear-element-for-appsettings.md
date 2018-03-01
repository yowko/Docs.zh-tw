---
title: "&lt;清除&gt;元素&lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54479cab9abc2c1a107cd055341404c0fe1308fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clear-element-for-appsettings"></a>\<清除 > 項目\<appSettings >

清除自訂應用程式設定。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<清除 >**

## <a name="syntax"></a>語法

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>屬性

無

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | 包含自訂應用程式設定，例如檔案路徑、 XML Web 服務 Url 或任何其他的自訂應用程式組態資訊。 |

## <a name="child-elements"></a>子元素

無

## <a name="example"></a>範例

下列範例顯示如何清除自訂組態設定：

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>另請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
