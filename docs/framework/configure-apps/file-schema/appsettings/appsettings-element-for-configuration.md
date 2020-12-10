---
title: <configuration> 的 <appSettings> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 66260d15768781b7fa3d9397b8e8a7d9ad68ab95
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009790"
---
# <a name="appsettings-element-for-configuration"></a>\<configuration> 的 \<appSettings> 項目

包含自訂應用程式設定。 這是 .NET Framework 所提供的預先定義設定區段。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a>Syntax

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **file**  | 選擇性屬性。<br><br>指定包含自訂應用程式設定之外部檔案的相對路徑。 指定的檔案包含在、和專案中所指定的相同類型設定， **\<add>** **\<remove>** **\<clear>** 並使用與這些專案相同的索引鍵/值組格式。<br><br>指定的路徑是相對於主要設定檔案。 對於 Windows Forms 應用程式，這是 (的二進位檔案夾，例如 */bin/debug*) ，而不是應用程式佈建檔的位置。 針對 Web Form 的應用程式，路徑會相對於應用程式根目錄（ *web.config* 檔案所在位置）。<br><br>如果找不到指定的檔案，則執行時間會忽略該屬性。 |

## <a name="parent-element"></a>父元素

|     | 描述 |
| --- | ----------- |
| [**\<configuration>** 元素](../configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | 新增自訂應用程式設定。 |
| [**\<clear>**](clear-element-for-appsettings.md) | 清除所有先前定義的應用程式設定。 |
| [**\<remove>**](remove-element-for-appsettings.md) | 移除先前定義的應用程式設定。 |

## <a name="remarks"></a>備註

專案會 **\<appSettings>** 儲存自訂的應用程式設定資訊，例如資料庫連接字串、檔案路徑、XML Web 服務 url，或應用程式的任何其他自訂設定資訊。 在專案中指定的索引鍵/值組 **\<appSettings>** ，會使用類別在程式碼中存取 <xref:System.Configuration.ConfigurationSettings> 。

您可以在 **\<appSettings>** *Web.config* 和應用程式佈建檔的元素中使用 file 屬性。 這個屬性會指定提供其他設定的設定檔，或覆寫在元素中指定的設定 **\<appSettings>** 。 **檔** 屬性可用於原始檔控制小組開發案例，例如，當使用者想要覆寫應用程式佈建檔中指定的專案設定時。

**檔** 屬性指定的設定檔必須具有的根節點， **\<appSettings>** 而不是 **\<configuration>** 。

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

此元素可用於應用程式佈建檔、電腦設定檔 (*Machine.config*) ，以及不在應用程式目錄層級的 *Web.config* 檔案。

## <a name="see-also"></a>請參閱

- [.NET Framework 的設定檔架構](../index.md)
