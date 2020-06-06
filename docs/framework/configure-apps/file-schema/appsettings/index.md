---
title: 應用程式設定結構描述
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215420"
---
# <a name="app-settings-schema"></a>應用程式設定結構描述

包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| 元素 | 描述 |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | 包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 標記以控制應用程式設定。 具有選擇性 **file** 屬性。 |
| [**\<add>**](add-element-for-appsettings.md) | 定義設定。 的子系 **\<appSettings>** 。 需要 **key** 和 **value** 屬性。 |
| [**\<clear>**](clear-element-for-appsettings.md) | 清除所有設定。 的子系 **\<appSettings>** 。 沒有任何屬性。 |
| [**\<remove>**](remove-element-for-appsettings.md) | 移除設定。 的子系 **\<appSettings>** 。 需要 **key** 屬性。 |

## <a name="appsettings-element"></a>\<appSettings> 項目

此元素包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 標記，以控制應用程式設定。 它會定義 **file** 的選擇性屬性。

## <a name="add-element"></a>\<add> 項目

新增自訂應用程式設定作為應用程式設定集合的名稱/值組。 它會定義 **key** 和 **value** 的屬性。

## <a name="clear-element"></a>\<clear> 項目

移除繼承自訂應用程式設定的所有參考，並僅允許元素後面的專案所新增的參考 **\<add>** **\<clear>** 。 它不會定義任何屬性。

## <a name="remove-element"></a>\<remove> 項目

從應用程式設定集合移除所繼承之自訂應用程式設定的參考。 它會定義 **key** 的屬性。

## <a name="example"></a>範例

下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [應用程式設定總覽](../../../winforms/advanced/application-settings-overview.md)
- [Application Settings Architecture](../../../winforms/advanced/application-settings-architecture.md)
