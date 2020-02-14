---
title: <appSettings> 的 <configuration> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 47d7648aae08544890a4dd2e42cedbf68a8acc72
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214727"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="1f262-102">\<設定的 \<appSettings > 元素 ></span><span class="sxs-lookup"><span data-stu-id="1f262-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="1f262-103">包含自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="1f262-103">Contains custom application settings.</span></span> <span data-ttu-id="1f262-104">這是 .NET Framework 所提供的預先定義設定區段。</span><span class="sxs-lookup"><span data-stu-id="1f262-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="1f262-105">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1f262-105">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="1f262-106">&nbsp;&nbsp; **\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="1f262-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1f262-107">語法</span><span class="sxs-lookup"><span data-stu-id="1f262-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="1f262-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1f262-108">Attribute</span></span>

|           | <span data-ttu-id="1f262-109">描述</span><span class="sxs-lookup"><span data-stu-id="1f262-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="1f262-110">**file**</span><span class="sxs-lookup"><span data-stu-id="1f262-110">**file**</span></span>  | <span data-ttu-id="1f262-111">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="1f262-111">Optional attribute.</span></span><br><br><span data-ttu-id="1f262-112">指定包含自訂應用程式設定之外部檔案的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="1f262-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="1f262-113">指定的檔案所包含的設定類型與 **\<加入 >** 、 **\<移除 >** ，以及 **\<清除 >** 元素中所指定的相同，並使用與這些專案相同的索引鍵/值組格式。</span><span class="sxs-lookup"><span data-stu-id="1f262-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="1f262-114">指定的路徑是相對於主要設定檔。</span><span class="sxs-lookup"><span data-stu-id="1f262-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="1f262-115">對於 Windows Forms 應用程式，這是二進位檔案夾（例如 */bin/debug*），而不是應用程式佈建檔的位置。</span><span class="sxs-lookup"><span data-stu-id="1f262-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="1f262-116">若是 Web Forms 應用程式，路徑會相對於*web.config*檔案所在的應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="1f262-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="1f262-117">請注意，如果找不到指定的檔案，執行時間會忽略屬性。</span><span class="sxs-lookup"><span data-stu-id="1f262-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="1f262-118">父元素</span><span class="sxs-lookup"><span data-stu-id="1f262-118">Parent element</span></span>

|     | <span data-ttu-id="1f262-119">描述</span><span class="sxs-lookup"><span data-stu-id="1f262-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1f262-120"> **\<設定 >** 元素</span><span class="sxs-lookup"><span data-stu-id="1f262-120">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="1f262-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="1f262-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="1f262-122">子元素</span><span class="sxs-lookup"><span data-stu-id="1f262-122">Child elements</span></span>

|     | <span data-ttu-id="1f262-123">描述</span><span class="sxs-lookup"><span data-stu-id="1f262-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1f262-124"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="1f262-124">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="1f262-125">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="1f262-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="1f262-126"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="1f262-126">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="1f262-127">清除所有先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="1f262-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="1f262-128"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="1f262-128">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="1f262-129">移除先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="1f262-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="1f262-130">備註</span><span class="sxs-lookup"><span data-stu-id="1f262-130">Remarks</span></span>

<span data-ttu-id="1f262-131">**\<AppSettings>** 項目會儲存自訂的應用程式組態資訊，例如資料庫連接字串、 檔案路徑、 XML Web 服務 Url 或任何其他自訂組態資訊應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f262-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="1f262-132">**\<appSettings >** 元素中指定的索引鍵/值組，會在程式碼中使用 <xref:System.Configuration.ConfigurationSettings> 類別來存取。</span><span class="sxs-lookup"><span data-stu-id="1f262-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="1f262-133">您可以在*web.config 和應用*程式設定檔的 **\<appSettings >** 元素中使用**file**屬性。</span><span class="sxs-lookup"><span data-stu-id="1f262-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="1f262-134">這個屬性會指定提供其他設定的設定檔，或覆寫 **\<appSettings >** 元素中指定的設定。</span><span class="sxs-lookup"><span data-stu-id="1f262-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="1f262-135">**檔**屬性可用於原始檔控制小組開發案例，例如當使用者想要覆寫應用程式佈建檔中指定的專案設定時。</span><span class="sxs-lookup"><span data-stu-id="1f262-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="1f262-136">**檔**屬性所指定的設定檔，必須具有 **\<appSettings >** 的根節點，而不是 **\<設定 >** 。</span><span class="sxs-lookup"><span data-stu-id="1f262-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="1f262-137">範例</span><span class="sxs-lookup"><span data-stu-id="1f262-137">Example</span></span>

<span data-ttu-id="1f262-138">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="1f262-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="1f262-139">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="1f262-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="1f262-140">組態檔</span><span class="sxs-lookup"><span data-stu-id="1f262-140">Configuration file</span></span>

<span data-ttu-id="1f262-141">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="1f262-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f262-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f262-142">See also</span></span>

- [<span data-ttu-id="1f262-143">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="1f262-143">Configuration file schema for the .NET Framework</span></span>](../index.md)
