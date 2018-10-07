---
title: 應用程式設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f11be59941759687806591feb1edcce28b2119e6
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844226"
---
# <a name="application-settings-schema"></a><span data-ttu-id="995a4-102">應用程式設定結構描述</span><span class="sxs-lookup"><span data-stu-id="995a4-102">Application Settings schema</span></span>

<span data-ttu-id="995a4-103">應用程式設定可讓 Windows Form 或 ASP.NET 應用程式儲存及擷取應用程式範圍和使用者範圍設定。</span><span class="sxs-lookup"><span data-stu-id="995a4-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="995a4-104">在此情況下，*設定*是任一部分程式可能是應用程式特定的或目前使用者特定的資訊 — 來自使用者的資料庫連接字串的所有一切的慣用預設的視窗大小。</span><span class="sxs-lookup"><span data-stu-id="995a4-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="995a4-105">根據預設，Windows Forms 應用程式中的應用程式設定會使用<xref:System.Configuration.LocalFileSettingsProvider>類別，它會使用.NET 組態系統儲存在 XML 組態檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="995a4-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="995a4-106">如需使用應用程式設定之檔案的詳細資訊，請參閱[應用程式設定架構](~/docs/framework/winforms/advanced/application-settings-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="995a4-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="995a4-107">應用程式設定會定義下列項目，它會使用組態檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="995a4-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="995a4-108">元素</span><span class="sxs-lookup"><span data-stu-id="995a4-108">Element</span></span>                    | <span data-ttu-id="995a4-109">描述</span><span class="sxs-lookup"><span data-stu-id="995a4-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="995a4-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="995a4-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="995a4-111">包含所有**\<設定 >** 應用程式特定的標記。</span><span class="sxs-lookup"><span data-stu-id="995a4-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="995a4-112">**\<userSettings >**</span><span class="sxs-lookup"><span data-stu-id="995a4-112">**\<userSettings>**</span></span>        | <span data-ttu-id="995a4-113">包含所有**\<設定 >** 目前使用者特定的標記。</span><span class="sxs-lookup"><span data-stu-id="995a4-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="995a4-114">**\<設定 >**</span><span class="sxs-lookup"><span data-stu-id="995a4-114">**\<setting>**</span></span>             | <span data-ttu-id="995a4-115">定義設定。</span><span class="sxs-lookup"><span data-stu-id="995a4-115">Defines a setting.</span></span> <span data-ttu-id="995a4-116">子系 **\<applicationSettings >** 或是 **\<userSettings >**。</span><span class="sxs-lookup"><span data-stu-id="995a4-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="995a4-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="995a4-117">**\<value>**</span></span>               | <span data-ttu-id="995a4-118">定義設定的值。</span><span class="sxs-lookup"><span data-stu-id="995a4-118">Defines a setting's value.</span></span> <span data-ttu-id="995a4-119">子系**\<設定 >**。</span><span class="sxs-lookup"><span data-stu-id="995a4-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="995a4-120">\<applicationSettings > 項目</span><span class="sxs-lookup"><span data-stu-id="995a4-120">\<applicationSettings> element</span></span>

<span data-ttu-id="995a4-121">這個項目包含所有**\<設定 >** 特有的用戶端電腦上的應用程式的執行個體的標籤。</span><span class="sxs-lookup"><span data-stu-id="995a4-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="995a4-122">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="995a4-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="995a4-123">\<userSettings > 項目</span><span class="sxs-lookup"><span data-stu-id="995a4-123">\<userSettings> element</span></span>

<span data-ttu-id="995a4-124">這個項目包含所有**\<設定 >** 專屬於目前正在使用應用程式之使用者的標記。</span><span class="sxs-lookup"><span data-stu-id="995a4-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="995a4-125">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="995a4-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="995a4-126">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="995a4-126">\<setting> element</span></span>

<span data-ttu-id="995a4-127">這個項目定義的設定。</span><span class="sxs-lookup"><span data-stu-id="995a4-127">This element defines a setting.</span></span> <span data-ttu-id="995a4-128">它具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="995a4-128">It has the following attributes.</span></span>

| <span data-ttu-id="995a4-129">屬性</span><span class="sxs-lookup"><span data-stu-id="995a4-129">Attribute</span></span>        | <span data-ttu-id="995a4-130">描述</span><span class="sxs-lookup"><span data-stu-id="995a4-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="995a4-131">**name**</span><span class="sxs-lookup"><span data-stu-id="995a4-131">**name**</span></span>         | <span data-ttu-id="995a4-132">必要。</span><span class="sxs-lookup"><span data-stu-id="995a4-132">Required.</span></span> <span data-ttu-id="995a4-133">設定的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="995a4-133">The unique ID of the setting.</span></span> <span data-ttu-id="995a4-134">透過 Visual Studio 所建立的設定會儲存名稱`ProjectName.Properties.Settings`。</span><span class="sxs-lookup"><span data-stu-id="995a4-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="995a4-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="995a4-135">**serializedAs**</span></span> | <span data-ttu-id="995a4-136">必要。</span><span class="sxs-lookup"><span data-stu-id="995a4-136">Required.</span></span> <span data-ttu-id="995a4-137">要用來序列化成文字值的格式。</span><span class="sxs-lookup"><span data-stu-id="995a4-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="995a4-138">有效值為：</span><span class="sxs-lookup"><span data-stu-id="995a4-138">Valid values are:</span></span><br><br><span data-ttu-id="995a4-139">- `string`。</span><span class="sxs-lookup"><span data-stu-id="995a4-139">- `string`.</span></span> <span data-ttu-id="995a4-140">值序列化為字串，使用<xref:System.ComponentModel.TypeConverter>。</span><span class="sxs-lookup"><span data-stu-id="995a4-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="995a4-141">- `xml`。</span><span class="sxs-lookup"><span data-stu-id="995a4-141">- `xml`.</span></span> <span data-ttu-id="995a4-142">值會使用 XML 序列化進行序列化。</span><span class="sxs-lookup"><span data-stu-id="995a4-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="995a4-143">- `binary`。</span><span class="sxs-lookup"><span data-stu-id="995a4-143">- `binary`.</span></span> <span data-ttu-id="995a4-144">值會序列化為文字編碼的二進位檔使用二進位序列化。</span><span class="sxs-lookup"><span data-stu-id="995a4-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="995a4-145">- `custom`。</span><span class="sxs-lookup"><span data-stu-id="995a4-145">- `custom`.</span></span> <span data-ttu-id="995a4-146">設定提供者的這項設定的固有知識和序列化和還原序列化它。</span><span class="sxs-lookup"><span data-stu-id="995a4-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="995a4-147">\<值 > 項目</span><span class="sxs-lookup"><span data-stu-id="995a4-147">\<value> element</span></span>

<span data-ttu-id="995a4-148">這個項目包含設定的值。</span><span class="sxs-lookup"><span data-stu-id="995a4-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="995a4-149">範例</span><span class="sxs-lookup"><span data-stu-id="995a4-149">Example</span></span>

<span data-ttu-id="995a4-150">下列範例示範定義兩個應用程式範圍的設定和兩個使用者範圍設定的應用程式設定檔：</span><span class="sxs-lookup"><span data-stu-id="995a4-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="995a4-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="995a4-151">See also</span></span>

<span data-ttu-id="995a4-152">[應用程式設定概觀](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="995a4-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="995a4-153">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="995a4-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
