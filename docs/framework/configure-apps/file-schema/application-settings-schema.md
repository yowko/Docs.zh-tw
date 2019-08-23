---
title: 應用程式設定架構
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927754"
---
# <a name="application-settings-schema"></a>應用程式設定架構

應用程式設定可讓 Windows Forms 或 ASP.NET 應用程式儲存和取出應用程式範圍和使用者範圍的設定。 在此內容中,*設定*是指特定于應用程式或目前使用者特有的任何資訊, 也就是資料庫連接字串與使用者慣用預設視窗大小的任何一項。

根據預設, Windows Forms 應用程式中的應用程式設定<xref:System.Configuration.LocalFileSettingsProvider>會使用類別, 這會使用 .net 設定系統將設定儲存在 XML 設定檔中。 如需應用程式設定所使用之檔案的詳細資訊, 請參閱[應用程式設定架構](../../winforms/advanced/application-settings-architecture.md)。

應用程式設定會將下列元素定義為其使用的設定檔的一部分。

| 項目                    | 描述                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | 包含所有 **\<設定>** 應用程式特定的標記。                         |
| **\<userSettings>**        | 包含所有 **\<設定>** 目前使用者特定的標記。                        |
| **\<setting>**             | 定義設定。 ApplicationSettings > 或 **\<**  **userSettings\<>** 的子系。 |
| **\<value>**               | 定義設定的值。 子系 **\<設定>** 。                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > 元素

這個項目包含所有 **\<設定>** 特有的用戶端電腦上的應用程式的執行個體的標籤。 它不會定義任何屬性。

## <a name="usersettings-element"></a>\<userSettings > 元素

這個項目包含所有 **\<設定>** 專屬於目前正在使用應用程式之使用者的標記。 它不會定義任何屬性。

## <a name="setting-element"></a>\<設定 > 元素

此元素會定義設定。 它具有下列屬性。

| 屬性        | 說明 |
| ---------------- | ----------- |
| **name**         | 必要項。 設定的唯一識別碼。 透過 Visual Studio 建立的設定會以名稱`ProjectName.Properties.Settings`儲存。 |
| **serializedAs** | 必要項。 要用來將值序列化為文字的格式。 有效值為：<br><br>- `string`. 此值會使用<xref:System.ComponentModel.TypeConverter>來序列化為字串。<br>- `xml`. 此值會使用 XML 序列化進行序列化。<br>- `binary`. 此值會使用二進位序列化序列化為文字編碼的二進位檔。<br />- `custom`. 設定提供者具有此設定的固有知識, 並將其序列化和還原序列化。 |

## <a name="value-element"></a>\<值 > 元素

此元素包含設定的值。

## <a name="example"></a>範例

下列範例顯示的應用程式佈建檔, 會定義兩個應用程式範圍的設定和兩個使用者範圍的設定:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [應用程式設定概觀](../../winforms/advanced/application-settings-overview.md)
- [應用程式設定架構](../../winforms/advanced/application-settings-architecture.md)
