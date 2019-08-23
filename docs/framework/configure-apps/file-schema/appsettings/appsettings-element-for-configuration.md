---
title: <configuration> 的 <appSettings> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: a64db49b521651ccff8b928720fe3273f8600b68
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921332"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings> 項目 \<設定>

包含自訂應用程式設定。 這是 .NET Framework 所提供的預先定義設定區段。

[ **\<configuration>** ](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings>**

## <a name="syntax"></a>語法

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>屬性

|           | 說明 |
| --------- | ----------- |
| **file**  | 選擇性屬性。<br><br>指定包含自訂應用程式設定之外部檔案的相對路徑。 指定的檔案包含相同類型的設定中指定 **\<新增>** ， **\<移除>** ，以及 **\<清除>** 項目，並使用相同的索引鍵/值配對的格式設定為這些項目。<br><br>指定的路徑是相對於主要設定檔。 對於 Windows Forms 應用程式, 這是二進位檔案夾 (例如 */bin/debug*), 而不是應用程式佈建檔的位置。 若是 Web Forms 應用程式, 路徑會相對於*web.config*檔案所在的應用程式根目錄。<br><br>請注意, 如果找不到指定的檔案, 執行時間會忽略屬性。 |

## <a name="parent-element"></a>父項目

|     | 說明 |
| --- | ----------- |
| [ **\<組態>** 項目](../configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [ **\<add>** ](add-element-for-appsettings.md) | 新增自訂應用程式設定。 |
| [ **\<clear>** ](clear-element-for-appsettings.md) | 清除所有先前定義的應用程式設定。 |
| [ **\<remove>** ](remove-element-for-appsettings.md) | 移除先前定義的應用程式設定。 |

## <a name="remarks"></a>備註

**
          \<AppSettings>** 項目會儲存自訂的應用程式組態資訊，例如資料庫連接字串、 檔案路徑、 XML Web 服務 Url 或任何其他自訂組態資訊應用程式。 中指定的索引鍵/值組 **\<appSettings>** 項目中的程式碼使用存取<xref:System.Configuration.ConfigurationSettings>類別。

您可以使用 **檔案** 屬性中 **\<appSettings>** 項目*Web.config*和應用程式組態檔。 這個屬性會指定組態檔中提供額外的設定或覆寫中指定的設定 **\<appSettings>** 項目。 **檔**屬性可用於原始檔控制小組開發案例, 例如當使用者想要覆寫應用程式佈建檔中指定的專案設定時。

所指定的組態檔**檔案**屬性必須具有根節點 **\<appSettings>** 而非 **\<組態>** .

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

此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。

## <a name="see-also"></a>另請參閱

- [.NET Framework 的設定檔架構](../index.md)
