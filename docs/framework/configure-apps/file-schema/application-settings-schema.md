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
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242825"
---
# <a name="application-settings-schema"></a><span data-ttu-id="db6c1-102">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="db6c1-102">Application Settings schema</span></span>

<span data-ttu-id="db6c1-103">應用程式設置允許 Windows 窗體或 ASP.NET 應用程式儲存和檢索應用程式範圍和用戶範圍的設置。</span><span class="sxs-lookup"><span data-stu-id="db6c1-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="db6c1-104">在此上下文中,*設定*是可能特定於應用程式或特定於當前使用者的任何資訊 - 從資料庫連接字串到使用者首選預設視窗大小的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="db6c1-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="db6c1-105">預設情況下,Windows 表單應用程式中的應用程式設置<xref:System.Configuration.LocalFileSettingsProvider>使用類,該類使用.NET 配置系統在 XML 設定檔中儲存設定。</span><span class="sxs-lookup"><span data-stu-id="db6c1-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="db6c1-106">有關應用程式設定使用的檔案的詳細資訊,請參閱[應用程式設定架構結構](../../winforms/advanced/application-settings-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="db6c1-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="db6c1-107">應用程式設定將以下元素定義為它使用的設定檔的一部分。</span><span class="sxs-lookup"><span data-stu-id="db6c1-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="db6c1-108">項目</span><span class="sxs-lookup"><span data-stu-id="db6c1-108">Element</span></span>                    | <span data-ttu-id="db6c1-109">描述</span><span class="sxs-lookup"><span data-stu-id="db6c1-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="db6c1-110">**\<應用程式設定>**</span><span class="sxs-lookup"><span data-stu-id="db6c1-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="db6c1-111">包含特定於應用程式**\<的所有設置>** 標記。</span><span class="sxs-lookup"><span data-stu-id="db6c1-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="db6c1-112">**\<使用者設定>**</span><span class="sxs-lookup"><span data-stu-id="db6c1-112">**\<userSettings>**</span></span>        | <span data-ttu-id="db6c1-113">包含特定於當前用戶**\<的所有設置>** 標記。</span><span class="sxs-lookup"><span data-stu-id="db6c1-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="db6c1-114">**\<設定>**</span><span class="sxs-lookup"><span data-stu-id="db6c1-114">**\<setting>**</span></span>             | <span data-ttu-id="db6c1-115">定義設定。</span><span class="sxs-lookup"><span data-stu-id="db6c1-115">Defines a setting.</span></span> <span data-ttu-id="db6c1-116">應用程式>**\<或 用戶設置的子項>。** \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="db6c1-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="db6c1-117">**\<值>**</span><span class="sxs-lookup"><span data-stu-id="db6c1-117">**\<value>**</span></span>               | <span data-ttu-id="db6c1-118">定義設置的值。</span><span class="sxs-lookup"><span data-stu-id="db6c1-118">Defines a setting's value.</span></span> <span data-ttu-id="db6c1-119">設置>的子項。 \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="db6c1-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="db6c1-120">\<應用程式設定>元素</span><span class="sxs-lookup"><span data-stu-id="db6c1-120">\<applicationSettings> element</span></span>

<span data-ttu-id="db6c1-121">此元素包含特定於用戶端計算機上的應用程式實例的所有**\<設置>** 標記。</span><span class="sxs-lookup"><span data-stu-id="db6c1-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="db6c1-122">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="db6c1-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="db6c1-123">\<使用者設定>元素</span><span class="sxs-lookup"><span data-stu-id="db6c1-123">\<userSettings> element</span></span>

<span data-ttu-id="db6c1-124">此元素包含特定於當前使用該應用程式的使用者的所有**\<設置>** 標記。</span><span class="sxs-lookup"><span data-stu-id="db6c1-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="db6c1-125">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="db6c1-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="db6c1-126">\<設定>元素</span><span class="sxs-lookup"><span data-stu-id="db6c1-126">\<setting> element</span></span>

<span data-ttu-id="db6c1-127">此元素定義設置。</span><span class="sxs-lookup"><span data-stu-id="db6c1-127">This element defines a setting.</span></span> <span data-ttu-id="db6c1-128">它具有以下屬性。</span><span class="sxs-lookup"><span data-stu-id="db6c1-128">It has the following attributes.</span></span>

| <span data-ttu-id="db6c1-129">屬性</span><span class="sxs-lookup"><span data-stu-id="db6c1-129">Attribute</span></span>        | <span data-ttu-id="db6c1-130">描述</span><span class="sxs-lookup"><span data-stu-id="db6c1-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="db6c1-131">**名稱**</span><span class="sxs-lookup"><span data-stu-id="db6c1-131">**name**</span></span>         | <span data-ttu-id="db6c1-132">必要。</span><span class="sxs-lookup"><span data-stu-id="db6c1-132">Required.</span></span> <span data-ttu-id="db6c1-133">設置的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="db6c1-133">The unique ID of the setting.</span></span> <span data-ttu-id="db6c1-134">以視覺化工作室建立的設定將儲存與名稱`ProjectName.Properties.Settings`。</span><span class="sxs-lookup"><span data-stu-id="db6c1-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="db6c1-135">**序列化**</span><span class="sxs-lookup"><span data-stu-id="db6c1-135">**serializeAs**</span></span> | <span data-ttu-id="db6c1-136">必要。</span><span class="sxs-lookup"><span data-stu-id="db6c1-136">Required.</span></span> <span data-ttu-id="db6c1-137">為序列化文字值格式。</span><span class="sxs-lookup"><span data-stu-id="db6c1-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="db6c1-138">有效值為：</span><span class="sxs-lookup"><span data-stu-id="db6c1-138">Valid values are:</span></span><br><br><span data-ttu-id="db6c1-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="db6c1-139">- `string`.</span></span> <span data-ttu-id="db6c1-140">該值使用 序列化為字串。 <xref:System.ComponentModel.TypeConverter></span><span class="sxs-lookup"><span data-stu-id="db6c1-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="db6c1-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="db6c1-141">- `xml`.</span></span> <span data-ttu-id="db6c1-142">該值使用 XML 序列化進行序列化。</span><span class="sxs-lookup"><span data-stu-id="db6c1-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="db6c1-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="db6c1-143">- `binary`.</span></span> <span data-ttu-id="db6c1-144">該值使用二進位序列化將該值序列化為文本編碼二進位。</span><span class="sxs-lookup"><span data-stu-id="db6c1-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="db6c1-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="db6c1-145">- `custom`.</span></span> <span data-ttu-id="db6c1-146">設置提供程式對此設置有固有的知識,並序列化並取消序列化。</span><span class="sxs-lookup"><span data-stu-id="db6c1-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="db6c1-147">\<數值>元素</span><span class="sxs-lookup"><span data-stu-id="db6c1-147">\<value> element</span></span>

<span data-ttu-id="db6c1-148">此元素包含設置的值。</span><span class="sxs-lookup"><span data-stu-id="db6c1-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="db6c1-149">範例</span><span class="sxs-lookup"><span data-stu-id="db6c1-149">Example</span></span>

<span data-ttu-id="db6c1-150">下面的範例顯示了一個應用程式設定檔,該檔定義了兩個應用程式範圍設定和兩個使用者範圍設定:</span><span class="sxs-lookup"><span data-stu-id="db6c1-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="db6c1-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db6c1-151">See also</span></span>

- [<span data-ttu-id="db6c1-152">應用程式設定概述</span><span class="sxs-lookup"><span data-stu-id="db6c1-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="db6c1-153">Application Settings Architecture</span><span class="sxs-lookup"><span data-stu-id="db6c1-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
