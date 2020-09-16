---
title: 應用程式設定架構
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: fc9cd8ac3819c6a02019c871e7bd45ceb4c2cef7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552306"
---
# <a name="application-settings-schema"></a>應用程式設定架構

應用程式設定可讓 Windows Forms 或 ASP.NET 應用程式儲存和取出應用程式範圍和使用者範圍的設定。 在此內容中， *設定* 是指特定于應用程式或目前使用者特定的任何資訊片段，從資料庫連接字串到使用者慣用的預設視窗大小都有。

根據預設，Windows Forms 應用程式中的應用程式設定會使用 <xref:System.Configuration.LocalFileSettingsProvider> 類別，此類別會使用 .net 設定系統將設定儲存在 XML 設定檔中。 如需應用程式設定所使用之檔案的詳細資訊，請參閱 [應用程式設定架構](/dotnet/desktop/winforms/advanced/application-settings-architecture)。

應用程式設定會在其使用的設定檔中定義下列元素。

| 項目                    | 描述                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | 包含 **\<setting>** 應用程式特定的所有標記。                         |
| **\<userSettings>**        | 包含 **\<setting>** 目前使用者特定的所有標記。                        |
| **\<setting>**             | 定義設定。 或的子 **\<applicationSettings>** 系 **\<userSettings>** 。 |
| **\<value>**               | 定義設定的值。 的子系 **\<setting>** 。                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings> 項目

這個元素包含 **\<setting>** 用戶端電腦上應用程式實例專用的所有標記。 它不會定義任何屬性。

## <a name="usersettings-element"></a>\<userSettings> 項目

這個元素包含 **\<setting>** 目前正在使用應用程式之使用者的特定標記。 它不會定義任何屬性。

## <a name="setting-element"></a>\<setting> 項目

此元素會定義設定。 它具有下列屬性。

| 屬性        | 描述 |
| ---------------- | ----------- |
| **name**         | 必要。 設定的唯一識別碼。 透過 Visual Studio 建立的設定會以名稱儲存 `ProjectName.Properties.Settings` 。 |
| **serializeAs** | 必要。 用來將值序列化為文字的格式。 有效值為：<br><br>- `string`. 使用將值序列化為字串 <xref:System.ComponentModel.TypeConverter> 。<br>- `xml`. 此值會使用 XML 序列化進行序列化。<br>- `binary`. 使用二進位序列化將值序列化為文字編碼的二進位檔。<br />- `custom`. 設定提供者具有此設定的固有知識，並將其序列化和還原序列化。 |

## <a name="value-element"></a>\<value> 項目

這個元素包含設定的值。

## <a name="example"></a>範例

下列範例顯示的應用程式佈建檔會定義兩個應用程式範圍的設定，以及兩個使用者範圍的設定：

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

- [應用程式設定概觀](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [應用程式設定架構](/dotnet/desktop/winforms/advanced/application-settings-architecture)
