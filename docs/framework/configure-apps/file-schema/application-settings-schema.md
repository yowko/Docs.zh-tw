---
title: 應用程式設定架構
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242825"
---
# <a name="application-settings-schema"></a><span data-ttu-id="ed0f1-102">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="ed0f1-102">Application Settings schema</span></span>

<span data-ttu-id="ed0f1-103">應用程式設定可讓 Windows Forms 或 ASP.NET 應用程式儲存和取出應用程式範圍和使用者範圍的設定。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="ed0f1-104">在此內容中，*設定*是指特定于應用程式或目前使用者特有的任何資訊，也就是資料庫連接字串與使用者慣用預設視窗大小的任何一項。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="ed0f1-105">根據預設，Windows Forms 應用程式中的應用程式設定會使用 <xref:System.Configuration.LocalFileSettingsProvider> 類別，這會使用 .net 設定系統將設定儲存在 XML 設定檔中。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="ed0f1-106">如需應用程式設定所使用之檔案的詳細資訊，請參閱[應用程式設定架構](../../winforms/advanced/application-settings-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="ed0f1-107">應用程式設定會將下列元素定義為其使用的設定檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="ed0f1-108">元素</span><span class="sxs-lookup"><span data-stu-id="ed0f1-108">Element</span></span>                    | <span data-ttu-id="ed0f1-109">描述</span><span class="sxs-lookup"><span data-stu-id="ed0f1-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="ed0f1-110">包含 **\<setting>** 應用程式特定的所有標記。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="ed0f1-111">包含 **\<setting>** 目前使用者特定的所有標記。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="ed0f1-112">定義設定。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-112">Defines a setting.</span></span> <span data-ttu-id="ed0f1-113">或的子 **\<applicationSettings>** 系 **\<userSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="ed0f1-114">定義設定的值。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-114">Defines a setting's value.</span></span> <span data-ttu-id="ed0f1-115">的子系 **\<setting>** 。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="ed0f1-116">\<applicationSettings> 項目</span><span class="sxs-lookup"><span data-stu-id="ed0f1-116">\<applicationSettings> element</span></span>

<span data-ttu-id="ed0f1-117">此元素包含 **\<setting>** 用戶端電腦上應用程式實例特有的所有標記。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="ed0f1-118">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="ed0f1-119">\<userSettings> 項目</span><span class="sxs-lookup"><span data-stu-id="ed0f1-119">\<userSettings> element</span></span>

<span data-ttu-id="ed0f1-120">此元素包含 **\<setting>** 目前正在使用應用程式之使用者特有的所有標記。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="ed0f1-121">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="ed0f1-122">\<setting> 項目</span><span class="sxs-lookup"><span data-stu-id="ed0f1-122">\<setting> element</span></span>

<span data-ttu-id="ed0f1-123">此元素會定義設定。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-123">This element defines a setting.</span></span> <span data-ttu-id="ed0f1-124">它具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-124">It has the following attributes.</span></span>

| <span data-ttu-id="ed0f1-125">屬性</span><span class="sxs-lookup"><span data-stu-id="ed0f1-125">Attribute</span></span>        | <span data-ttu-id="ed0f1-126">描述</span><span class="sxs-lookup"><span data-stu-id="ed0f1-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="ed0f1-127">**name**</span><span class="sxs-lookup"><span data-stu-id="ed0f1-127">**name**</span></span>         | <span data-ttu-id="ed0f1-128">必要。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-128">Required.</span></span> <span data-ttu-id="ed0f1-129">設定的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-129">The unique ID of the setting.</span></span> <span data-ttu-id="ed0f1-130">透過 Visual Studio 建立的設定會以名稱儲存 `ProjectName.Properties.Settings` 。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="ed0f1-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="ed0f1-131">**serializeAs**</span></span> | <span data-ttu-id="ed0f1-132">必要。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-132">Required.</span></span> <span data-ttu-id="ed0f1-133">要用來將值序列化為文字的格式。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="ed0f1-134">有效值為：</span><span class="sxs-lookup"><span data-stu-id="ed0f1-134">Valid values are:</span></span><br><br><span data-ttu-id="ed0f1-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="ed0f1-135">- `string`.</span></span> <span data-ttu-id="ed0f1-136">此值會使用來序列化為字串 <xref:System.ComponentModel.TypeConverter> 。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="ed0f1-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="ed0f1-137">- `xml`.</span></span> <span data-ttu-id="ed0f1-138">此值會使用 XML 序列化進行序列化。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="ed0f1-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="ed0f1-139">- `binary`.</span></span> <span data-ttu-id="ed0f1-140">此值會使用二進位序列化序列化為文字編碼的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="ed0f1-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="ed0f1-141">- `custom`.</span></span> <span data-ttu-id="ed0f1-142">設定提供者具有此設定的固有知識，並將其序列化和還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="ed0f1-143">\<value> 項目</span><span class="sxs-lookup"><span data-stu-id="ed0f1-143">\<value> element</span></span>

<span data-ttu-id="ed0f1-144">此元素包含設定的值。</span><span class="sxs-lookup"><span data-stu-id="ed0f1-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="ed0f1-145">範例</span><span class="sxs-lookup"><span data-stu-id="ed0f1-145">Example</span></span>

<span data-ttu-id="ed0f1-146">下列範例顯示的應用程式佈建檔，會定義兩個應用程式範圍的設定和兩個使用者範圍的設定：</span><span class="sxs-lookup"><span data-stu-id="ed0f1-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ed0f1-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed0f1-147">See also</span></span>

- [<span data-ttu-id="ed0f1-148">應用程式設定總覽</span><span class="sxs-lookup"><span data-stu-id="ed0f1-148">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="ed0f1-149">Application Settings Architecture</span><span class="sxs-lookup"><span data-stu-id="ed0f1-149">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
