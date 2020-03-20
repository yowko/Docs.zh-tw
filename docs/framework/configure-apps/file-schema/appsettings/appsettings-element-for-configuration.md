---
title: <configuration> 的 <appSettings> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155527"
---
# <a name="appsettings-element-for-configuration"></a>\<用於\<配置>的應用設置>元素

包含自訂應用程式設定。 這是由 .NET 框架提供的預定義配置部分。

&nbsp; [** \<配置>**](../configuration-element.md)&nbsp;**應用設置>\<**

## <a name="syntax"></a>語法

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **檔**  | 選擇性屬性。<br><br>指定包含自訂應用程式佈建設置的外部檔的相對路徑。 指定的檔包含在**\<添加>、****\<刪除>** 和**\<清除>** 元素中指定的相同類型的設置，並使用與這些元素相同的鍵/值對格式。<br><br>指定的路徑與主設定檔相關。 對於 Windows 表單應用程式，這是二進位檔案夾（如 */bin/調試*），而不是應用程式佈建檔的位置。 對於 Web 表單應用程式，路徑相對於*Web.config*檔所在的應用程式根。<br><br>如果找不到指定的檔，運行時將忽略該屬性。 |

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [** \<配置>** 元素](../configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<添加>**](add-element-for-appsettings.md) | 添加自訂應用程式設定。 |
| [**\<明確>**](clear-element-for-appsettings.md) | 清除以前定義的所有應用程式設定。 |
| [**\<刪除>**](remove-element-for-appsettings.md) | 刪除以前定義的應用程式設定。 |

## <a name="remarks"></a>備註

appSettings>元素存儲自訂應用程式佈建資訊，如資料庫連接字串、檔路徑、XML Web 服務 URL 或應用程式的任何其他自訂配置資訊。 ** \< ** 使用<xref:System.Configuration.ConfigurationSettings>類在代碼中訪問**\<appSettings>** 元素中指定的鍵/值對。

您可以在**\<AppSettings>** *Web.config*和應用程式佈建檔的元素中使用**檔**屬性。 此屬性指定提供其他設置或覆蓋**\<appSettings>** 元素中指定的設置的設定檔。 **檔**屬性可用於原始程式碼管理團隊開發方案，例如當使用者想要覆蓋應用程式佈建檔中指定的專案設置時。

**檔**屬性指定的設定檔必須具有**\<appSettings>** 的根節點，而不是**\<配置>。**

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

## <a name="configuration-file"></a>組態檔

此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。

## <a name="see-also"></a>另請參閱

- [.NET 框架的設定檔架構](../index.md)
