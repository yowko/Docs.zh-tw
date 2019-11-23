---
title: <appSettings> 的 <configuration> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6112d87afcca8b2f54508d03d3ea4c0781d7e475
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119274"
---
# <a name="appsettings-element-for-configuration"></a>\<設定的 \<appSettings > 元素 >

包含自訂應用程式設定。 這是 .NET Framework 所提供的預先定義設定區段。

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings >**

## <a name="syntax"></a>語法

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **file**  | 選擇性屬性。<br><br>指定包含自訂應用程式設定之外部檔案的相對路徑。 指定的檔案所包含的設定類型與 **\<加入 >** 、 **\<移除 >** ，以及 **\<清除 >** 元素中所指定的相同，並使用與這些專案相同的索引鍵/值組格式。<br><br>指定的路徑是相對於主要設定檔。 對於 Windows Forms 應用程式，這是二進位檔案夾（例如 */bin/debug*），而不是應用程式佈建檔的位置。 若是 Web Forms 應用程式，路徑會相對於*web.config*檔案所在的應用程式根目錄。<br><br>請注意，如果找不到指定的檔案，執行時間會忽略屬性。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [ **\<設定 >** 元素](../configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<add>** ](add-element-for-appsettings.md) | 新增自訂應用程式設定。 |
| [ **\<clear>** ](clear-element-for-appsettings.md) | 清除所有先前定義的應用程式設定。 |
| [ **\<remove>** ](remove-element-for-appsettings.md) | 移除先前定義的應用程式設定。 |

## <a name="remarks"></a>備註

**\<AppSettings>** 項目會儲存自訂的應用程式組態資訊，例如資料庫連接字串、 檔案路徑、 XML Web 服務 Url 或任何其他自訂組態資訊應用程式。 **\<appSettings >** 元素中指定的索引鍵/值組，會在程式碼中使用 <xref:System.Configuration.ConfigurationSettings> 類別來存取。

您可以在*web.config 和應用*程式設定檔的 **\<appSettings >** 元素中使用**file**屬性。 這個屬性會指定提供其他設定的設定檔，或覆寫 **\<appSettings >** 元素中指定的設定。 **檔**屬性可用於原始檔控制小組開發案例，例如當使用者想要覆寫應用程式佈建檔中指定的專案設定時。

**檔**屬性所指定的設定檔，必須具有 **\<appSettings >** 的根節點，而不是 **\<設定 >** 。

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

此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](../index.md)
