---
title: '&lt;appSettings&gt;項目&lt;組態&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 0ba57f51d3b1e78239677317933507ff009db035
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190927"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="93b94-102">\<appSettings > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="93b94-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="93b94-103">包含自訂的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="93b94-103">Contains custom application settings.</span></span> <span data-ttu-id="93b94-104">這是.NET Framework 所提供的預先定義的組態區段。</span><span class="sxs-lookup"><span data-stu-id="93b94-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="93b94-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="93b94-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="93b94-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="93b94-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="93b94-107">語法</span><span class="sxs-lookup"><span data-stu-id="93b94-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="93b94-108">屬性</span><span class="sxs-lookup"><span data-stu-id="93b94-108">Attribute</span></span>

|           | <span data-ttu-id="93b94-109">描述</span><span class="sxs-lookup"><span data-stu-id="93b94-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="93b94-110">**file**</span><span class="sxs-lookup"><span data-stu-id="93b94-110">**file**</span></span>  | <span data-ttu-id="93b94-111">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="93b94-111">Optional attribute.</span></span><br><br><span data-ttu-id="93b94-112">指定包含自訂的應用程式組態設定的外部檔案的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="93b94-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="93b94-113">指定的檔案包含相同類型的設定中指定**\<新增 >**， **\<移除 >**，以及**\<清除 >** 項目，並使用相同的索引鍵/值配對的格式設定為這些項目。</span><span class="sxs-lookup"><span data-stu-id="93b94-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="93b94-114">指定的路徑是相對於主要設定檔。</span><span class="sxs-lookup"><span data-stu-id="93b94-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="93b94-115">Windows Forms 應用程式，這是 [二進位] 資料夾 (例如 */bin/debug*)，不是應用程式組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="93b94-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="93b94-116">為 Web Form 應用程式，則路徑是相對於應用程式根目錄，其中*web.config*檔案所在的。</span><span class="sxs-lookup"><span data-stu-id="93b94-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="93b94-117">請注意，是否指定的檔案找不到執行階段會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="93b94-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="93b94-118">父項目</span><span class="sxs-lookup"><span data-stu-id="93b94-118">Parent element</span></span>

|     | <span data-ttu-id="93b94-119">描述</span><span class="sxs-lookup"><span data-stu-id="93b94-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="93b94-120">**\<組態 >** 項目</span><span class="sxs-lookup"><span data-stu-id="93b94-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="93b94-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="93b94-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="93b94-122">子元素</span><span class="sxs-lookup"><span data-stu-id="93b94-122">Child elements</span></span>

|     | <span data-ttu-id="93b94-123">描述</span><span class="sxs-lookup"><span data-stu-id="93b94-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="93b94-124">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="93b94-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="93b94-125">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="93b94-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="93b94-126">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="93b94-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="93b94-127">清除所有先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="93b94-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="93b94-128">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="93b94-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="93b94-129">移除先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="93b94-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="93b94-130">備註</span><span class="sxs-lookup"><span data-stu-id="93b94-130">Remarks</span></span>

<span data-ttu-id="93b94-131">**\<AppSettings >** 項目會儲存自訂的應用程式組態資訊，例如資料庫連接字串、 檔案路徑、 XML Web 服務 Url 或任何其他自訂組態資訊應用程式。</span><span class="sxs-lookup"><span data-stu-id="93b94-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="93b94-132">中指定的索引鍵/值組 **\<appSettings >** 項目中的程式碼使用存取<xref:System.Configuration.ConfigurationSettings>類別。</span><span class="sxs-lookup"><span data-stu-id="93b94-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="93b94-133">您可以使用**檔案**屬性中 **\<appSettings >** 項目*Web.config*和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="93b94-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="93b94-134">這個屬性會指定組態檔中提供額外的設定或覆寫中指定的設定 **\<appSettings >** 項目。</span><span class="sxs-lookup"><span data-stu-id="93b94-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="93b94-135">**檔案**屬性可以用於原始檔控制小組開發案例中，例如當使用者想要覆寫應用程式組態檔中指定的專案設定。</span><span class="sxs-lookup"><span data-stu-id="93b94-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="93b94-136">所指定的組態檔**檔案**屬性必須具有根節點 **\<appSettings >** 而非**\<組態 >**.</span><span class="sxs-lookup"><span data-stu-id="93b94-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="93b94-137">範例</span><span class="sxs-lookup"><span data-stu-id="93b94-137">Example</span></span>

<span data-ttu-id="93b94-138">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="93b94-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="93b94-139">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="93b94-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="93b94-140">組態檔</span><span class="sxs-lookup"><span data-stu-id="93b94-140">Configuration file</span></span>

<span data-ttu-id="93b94-141">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="93b94-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="93b94-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93b94-142">See also</span></span>

- [<span data-ttu-id="93b94-143">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="93b94-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
