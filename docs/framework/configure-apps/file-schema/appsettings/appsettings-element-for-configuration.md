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
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="fbffe-102">\<appSettings> 項目 \<設定></span><span class="sxs-lookup"><span data-stu-id="fbffe-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="fbffe-103">包含自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="fbffe-103">Contains custom application settings.</span></span> <span data-ttu-id="fbffe-104">這是 .NET Framework 所提供的預先定義設定區段。</span><span class="sxs-lookup"><span data-stu-id="fbffe-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="fbffe-105">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="fbffe-105">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="fbffe-106">&nbsp;&nbsp; **\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="fbffe-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fbffe-107">語法</span><span class="sxs-lookup"><span data-stu-id="fbffe-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="fbffe-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fbffe-108">Attribute</span></span>

|           | <span data-ttu-id="fbffe-109">說明</span><span class="sxs-lookup"><span data-stu-id="fbffe-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="fbffe-110">**file**</span><span class="sxs-lookup"><span data-stu-id="fbffe-110">**file**</span></span>  | <span data-ttu-id="fbffe-111">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="fbffe-111">Optional attribute.</span></span><br><br><span data-ttu-id="fbffe-112">指定包含自訂應用程式設定之外部檔案的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="fbffe-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="fbffe-113">指定的檔案包含相同類型的設定中指定 **\<新增>** ， **\<移除>** ，以及 **\<清除>** 項目，並使用相同的索引鍵/值配對的格式設定為這些項目。</span><span class="sxs-lookup"><span data-stu-id="fbffe-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="fbffe-114">指定的路徑是相對於主要設定檔。</span><span class="sxs-lookup"><span data-stu-id="fbffe-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="fbffe-115">對於 Windows Forms 應用程式, 這是二進位檔案夾 (例如 */bin/debug*), 而不是應用程式佈建檔的位置。</span><span class="sxs-lookup"><span data-stu-id="fbffe-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="fbffe-116">若是 Web Forms 應用程式, 路徑會相對於*web.config*檔案所在的應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="fbffe-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="fbffe-117">請注意, 如果找不到指定的檔案, 執行時間會忽略屬性。</span><span class="sxs-lookup"><span data-stu-id="fbffe-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="fbffe-118">父項目</span><span class="sxs-lookup"><span data-stu-id="fbffe-118">Parent element</span></span>

|     | <span data-ttu-id="fbffe-119">說明</span><span class="sxs-lookup"><span data-stu-id="fbffe-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fbffe-120"> **\<組態>** 項目</span><span class="sxs-lookup"><span data-stu-id="fbffe-120">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="fbffe-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fbffe-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="fbffe-122">子元素</span><span class="sxs-lookup"><span data-stu-id="fbffe-122">Child elements</span></span>

|     | <span data-ttu-id="fbffe-123">描述</span><span class="sxs-lookup"><span data-stu-id="fbffe-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fbffe-124"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="fbffe-124">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="fbffe-125">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="fbffe-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="fbffe-126"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="fbffe-126">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="fbffe-127">清除所有先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="fbffe-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="fbffe-128"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="fbffe-128">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="fbffe-129">移除先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="fbffe-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="fbffe-130">備註</span><span class="sxs-lookup"><span data-stu-id="fbffe-130">Remarks</span></span>

<span data-ttu-id="fbffe-131">**\<AppSettings>** 項目會儲存自訂的應用程式組態資訊，例如資料庫連接字串、 檔案路徑、 XML Web 服務 Url 或任何其他自訂組態資訊應用程式。</span><span class="sxs-lookup"><span data-stu-id="fbffe-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="fbffe-132">中指定的索引鍵/值組 **\<appSettings>** 項目中的程式碼使用存取<xref:System.Configuration.ConfigurationSettings>類別。</span><span class="sxs-lookup"><span data-stu-id="fbffe-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="fbffe-133">您可以使用 **檔案** 屬性中 **\<appSettings>** 項目*Web.config*和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="fbffe-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="fbffe-134">這個屬性會指定組態檔中提供額外的設定或覆寫中指定的設定 **\<appSettings>** 項目。</span><span class="sxs-lookup"><span data-stu-id="fbffe-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="fbffe-135">**檔**屬性可用於原始檔控制小組開發案例, 例如當使用者想要覆寫應用程式佈建檔中指定的專案設定時。</span><span class="sxs-lookup"><span data-stu-id="fbffe-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="fbffe-136">所指定的組態檔**檔案**屬性必須具有根節點 **\<appSettings>** 而非 **\<組態>** .</span><span class="sxs-lookup"><span data-stu-id="fbffe-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="fbffe-137">範例</span><span class="sxs-lookup"><span data-stu-id="fbffe-137">Example</span></span>

<span data-ttu-id="fbffe-138">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="fbffe-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="fbffe-139">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="fbffe-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="fbffe-140">組態檔</span><span class="sxs-lookup"><span data-stu-id="fbffe-140">Configuration file</span></span>

<span data-ttu-id="fbffe-141">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="fbffe-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbffe-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbffe-142">See also</span></span>

- [<span data-ttu-id="fbffe-143">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="fbffe-143">Configuration file schema for the .NET Framework</span></span>](../index.md)
