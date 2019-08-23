---
title: <appSettings> 的 <add> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 594ba4f289012e775e93acba98056b60bdd94cbd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927740"
---
# <a name="add-element-for-appsettings"></a>\<新增 appSettings > 的\<> 元素

新增自訂應用程式設定。

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**

## <a name="syntax"></a>語法

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>屬性

|           | 說明 |
| --------- | ----------- |
| **key**   | 必要屬性。<br><br>指定要加入之索引鍵的名稱。 |
| **value** | 必要屬性。<br><br>指定要加入之索引鍵的值。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | 包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。 |

## <a name="child-elements"></a>子元素

無

## <a name="example"></a>範例

下列範例顯示如何新增應用程式名稱的自訂設定:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

下列範例會使用`<add>`元素, 在 ASP.NET 應用程式中定義兩個相容性設定:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](../index.md)
