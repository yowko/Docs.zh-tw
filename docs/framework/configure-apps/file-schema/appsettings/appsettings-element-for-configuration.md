---
title: "&lt;appSettings&gt;元素&lt;組態&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cebb9ba7ebeb483233276324289a4ddc5a0bc381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="08385-102">\<appSettings > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="08385-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="08385-103">包含自訂的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="08385-103">Contains custom application settings.</span></span> <span data-ttu-id="08385-104">這是.NET Framework 所提供的預先定義的組態區段。</span><span class="sxs-lookup"><span data-stu-id="08385-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="08385-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="08385-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="08385-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="08385-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="08385-107">語法</span><span class="sxs-lookup"><span data-stu-id="08385-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="08385-108">屬性</span><span class="sxs-lookup"><span data-stu-id="08385-108">Attribute</span></span>

|           | <span data-ttu-id="08385-109">描述</span><span class="sxs-lookup"><span data-stu-id="08385-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="08385-110">**file**</span><span class="sxs-lookup"><span data-stu-id="08385-110">**file**</span></span>  | <span data-ttu-id="08385-111">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="08385-111">Optional attribute.</span></span><br><br><span data-ttu-id="08385-112">指定包含自訂的應用程式組態設定的外部檔案的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="08385-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="08385-113">指定的檔案包含相同類型的設定中指定的**\<新增 >**， **\<移除 >**，和**\<清除 >**項目，並使用相同的索引鍵/值組格式與這些項目。</span><span class="sxs-lookup"><span data-stu-id="08385-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="08385-114">指定的路徑是相對於主要設定檔。</span><span class="sxs-lookup"><span data-stu-id="08385-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="08385-115">Windows Form 應用程式中，這是 [二進位] 資料夾 (例如*/bin/debug*)，不是應用程式組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="08385-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="08385-116">為 Web Form 應用程式，則路徑是相對於應用程式根目錄，其中*web.config*檔所在。</span><span class="sxs-lookup"><span data-stu-id="08385-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="08385-117">請注意，是否指定的檔案找不到執行階段會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="08385-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="08385-118">父項目</span><span class="sxs-lookup"><span data-stu-id="08385-118">Parent element</span></span>

|     | <span data-ttu-id="08385-119">描述</span><span class="sxs-lookup"><span data-stu-id="08385-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="08385-120">**\<設定 >**項目</span><span class="sxs-lookup"><span data-stu-id="08385-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="08385-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="08385-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="08385-122">子元素</span><span class="sxs-lookup"><span data-stu-id="08385-122">Child elements</span></span>

|     | <span data-ttu-id="08385-123">描述</span><span class="sxs-lookup"><span data-stu-id="08385-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="08385-124">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="08385-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="08385-125">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="08385-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="08385-126">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="08385-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="08385-127">清除所有先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="08385-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="08385-128">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="08385-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="08385-129">移除先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="08385-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="08385-130">備註</span><span class="sxs-lookup"><span data-stu-id="08385-130">Remarks</span></span>

<span data-ttu-id="08385-131"> **\<AppSettings >**元素會儲存自訂應用程式組態資訊，例如資料庫連接字串、 檔案路徑、 XML Web 服務 Url 或任何其他自訂組態資訊應用程式。</span><span class="sxs-lookup"><span data-stu-id="08385-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="08385-132">中指定的索引鍵/值組 **\<appSettings >**項目在程式碼中使用存取<xref:System.Configuration.ConfigurationSettings>類別。</span><span class="sxs-lookup"><span data-stu-id="08385-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="08385-133">您可以使用**檔案**屬性 **\<appSettings >**元素*Web.config*和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="08385-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="08385-134">這個屬性會指定組態檔中提供額外的設定，或在指定的設定會覆寫 **\<appSettings >**項目。</span><span class="sxs-lookup"><span data-stu-id="08385-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="08385-135">**檔案**屬性可以用於原始檔控制小組開發案例中，例如當使用者想要覆寫應用程式組態檔中指定的專案設定。</span><span class="sxs-lookup"><span data-stu-id="08385-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="08385-136">所指定的組態檔**檔案**屬性必須具有根節點 **\<appSettings >**而**\<組態 >**.</span><span class="sxs-lookup"><span data-stu-id="08385-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="08385-137">範例</span><span class="sxs-lookup"><span data-stu-id="08385-137">Example</span></span>

<span data-ttu-id="08385-138">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="08385-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="08385-139">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="08385-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="08385-140">組態檔</span><span class="sxs-lookup"><span data-stu-id="08385-140">Configuration file</span></span>

<span data-ttu-id="08385-141">此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="08385-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="08385-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08385-142">See also</span></span>

[<span data-ttu-id="08385-143">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="08385-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
