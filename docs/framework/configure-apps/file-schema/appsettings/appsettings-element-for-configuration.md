---
title: <configuration> 的 <appSettings> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155527"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="ed233-102">\<用於\<配置>的應用設置>元素</span><span class="sxs-lookup"><span data-stu-id="ed233-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="ed233-103">包含自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="ed233-103">Contains custom application settings.</span></span> <span data-ttu-id="ed233-104">這是由 .NET 框架提供的預定義配置部分。</span><span class="sxs-lookup"><span data-stu-id="ed233-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="ed233-105">&nbsp; [\*\* \<配置>\*\*](../configuration-element.md)&nbsp;**應用設置>\<**</span><span class="sxs-lookup"><span data-stu-id="ed233-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ed233-106">語法</span><span class="sxs-lookup"><span data-stu-id="ed233-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="ed233-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ed233-107">Attribute</span></span>

|           | <span data-ttu-id="ed233-108">描述</span><span class="sxs-lookup"><span data-stu-id="ed233-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ed233-109">**檔**</span><span class="sxs-lookup"><span data-stu-id="ed233-109">**file**</span></span>  | <span data-ttu-id="ed233-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="ed233-110">Optional attribute.</span></span><br><br><span data-ttu-id="ed233-111">指定包含自訂應用程式佈建設置的外部檔的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="ed233-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="ed233-112">指定的檔包含在**\<添加>、\*\*\*\*\<刪除>** 和**\<清除>** 元素中指定的相同類型的設置，並使用與這些元素相同的鍵/值對格式。</span><span class="sxs-lookup"><span data-stu-id="ed233-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="ed233-113">指定的路徑與主設定檔相關。</span><span class="sxs-lookup"><span data-stu-id="ed233-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="ed233-114">對於 Windows 表單應用程式，這是二進位檔案夾（如 */bin/調試*），而不是應用程式佈建檔的位置。</span><span class="sxs-lookup"><span data-stu-id="ed233-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="ed233-115">對於 Web 表單應用程式，路徑相對於*Web.config*檔所在的應用程式根。</span><span class="sxs-lookup"><span data-stu-id="ed233-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="ed233-116">如果找不到指定的檔，運行時將忽略該屬性。</span><span class="sxs-lookup"><span data-stu-id="ed233-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ed233-117">父元素</span><span class="sxs-lookup"><span data-stu-id="ed233-117">Parent element</span></span>

|     | <span data-ttu-id="ed233-118">描述</span><span class="sxs-lookup"><span data-stu-id="ed233-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ed233-119">\*\* \<配置>\*\* 元素</span><span class="sxs-lookup"><span data-stu-id="ed233-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="ed233-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ed233-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ed233-121">子元素</span><span class="sxs-lookup"><span data-stu-id="ed233-121">Child elements</span></span>

|     | <span data-ttu-id="ed233-122">描述</span><span class="sxs-lookup"><span data-stu-id="ed233-122">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ed233-123">**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="ed233-123">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="ed233-124">添加自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="ed233-124">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="ed233-125">**\<明確>**</span><span class="sxs-lookup"><span data-stu-id="ed233-125">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="ed233-126">清除以前定義的所有應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="ed233-126">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="ed233-127">**\<刪除>**</span><span class="sxs-lookup"><span data-stu-id="ed233-127">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="ed233-128">刪除以前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="ed233-128">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ed233-129">備註</span><span class="sxs-lookup"><span data-stu-id="ed233-129">Remarks</span></span>

<span data-ttu-id="ed233-130">appSettings>元素存儲自訂應用程式佈建資訊，如資料庫連接字串、檔路徑、XML Web 服務 URL 或應用程式的任何其他自訂配置資訊。 \*\* \< \*\*</span><span class="sxs-lookup"><span data-stu-id="ed233-130">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="ed233-131">使用<xref:System.Configuration.ConfigurationSettings>類在代碼中訪問**\<appSettings>** 元素中指定的鍵/值對。</span><span class="sxs-lookup"><span data-stu-id="ed233-131">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="ed233-132">您可以在**\<AppSettings>** *Web.config*和應用程式佈建檔的元素中使用**檔**屬性。</span><span class="sxs-lookup"><span data-stu-id="ed233-132">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="ed233-133">此屬性指定提供其他設置或覆蓋**\<appSettings>** 元素中指定的設置的設定檔。</span><span class="sxs-lookup"><span data-stu-id="ed233-133">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="ed233-134">**檔**屬性可用於原始程式碼管理團隊開發方案，例如當使用者想要覆蓋應用程式佈建檔中指定的專案設置時。</span><span class="sxs-lookup"><span data-stu-id="ed233-134">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="ed233-135">**檔**屬性指定的設定檔必須具有**\<appSettings>** 的根節點，而不是**\<配置>。**</span><span class="sxs-lookup"><span data-stu-id="ed233-135">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="ed233-136">範例</span><span class="sxs-lookup"><span data-stu-id="ed233-136">Example</span></span>

<span data-ttu-id="ed233-137">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="ed233-137">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="ed233-138">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="ed233-138">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ed233-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="ed233-139">Configuration file</span></span>

<span data-ttu-id="ed233-140">此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。</span><span class="sxs-lookup"><span data-stu-id="ed233-140">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed233-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed233-141">See also</span></span>

- [<span data-ttu-id="ed233-142">.NET 框架的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="ed233-142">Configuration file schema for the .NET Framework</span></span>](../index.md)
