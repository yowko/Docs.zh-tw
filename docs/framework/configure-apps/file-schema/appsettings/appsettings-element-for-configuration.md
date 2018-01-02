---
title: "&lt;appSettings&gt;元素&lt;組態&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cebb9ba7ebeb483233276324289a4ddc5a0bc381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > 項目\<設定 >

包含自訂的應用程式設定。 這是.NET Framework 所提供的預先定義的組態區段。

[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings >**

## <a name="syntax"></a>語法

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>屬性

|           | 描述 |
| --------- | ----------- |
| **file**  | 選擇性屬性。<br><br>指定包含自訂的應用程式組態設定的外部檔案的相對路徑。 指定的檔案包含相同類型的設定中指定的**\<新增 >**， **\<移除 >**，和**\<清除 >**項目，並使用相同的索引鍵/值組格式與這些項目。<br><br>指定的路徑是相對於主要設定檔。 Windows Form 應用程式中，這是 [二進位] 資料夾 (例如*/bin/debug*)，不是應用程式組態檔的位置。 為 Web Form 應用程式，則路徑是相對於應用程式根目錄，其中*web.config*檔所在。<br><br>請注意，是否指定的檔案找不到執行階段會忽略此屬性。 |

## <a name="parent-element"></a>父項目

|     | 描述 |
| --- | ----------- |
| [**\<設定 >**項目](~/docs/framework/configure-apps/file-schema/configuration-element.md) | 通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。 |

## <a name="child-elements"></a>子元素

|     | 描述 |
| --- | ----------- |
| [**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | 新增自訂應用程式設定。 |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | 清除所有先前定義的應用程式設定。 |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | 移除先前定義的應用程式設定。 |

## <a name="remarks"></a>備註

 **\<AppSettings >**元素會儲存自訂應用程式組態資訊，例如資料庫連接字串、 檔案路徑、 XML Web 服務 Url 或任何其他自訂組態資訊應用程式。 中指定的索引鍵/值組 **\<appSettings >**項目在程式碼中使用存取<xref:System.Configuration.ConfigurationSettings>類別。

您可以使用**檔案**屬性 **\<appSettings >**元素*Web.config*和應用程式組態檔。 這個屬性會指定組態檔中提供額外的設定，或在指定的設定會覆寫 **\<appSettings >**項目。 **檔案**屬性可以用於原始檔控制小組開發案例中，例如當使用者想要覆寫應用程式組態檔中指定的專案設定。

所指定的組態檔**檔案**屬性必須具有根節點 **\<appSettings >**而**\<組態 >**.

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

此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。

## <a name="see-also"></a>另請參閱

[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)
