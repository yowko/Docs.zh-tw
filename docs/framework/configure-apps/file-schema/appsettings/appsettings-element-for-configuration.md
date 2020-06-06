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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155527"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="6c995-102">\<configuration> 的 \<appSettings> 項目</span><span class="sxs-lookup"><span data-stu-id="6c995-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="6c995-103">包含自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="6c995-103">Contains custom application settings.</span></span> <span data-ttu-id="6c995-104">這是 .NET Framework 所提供的預先定義設定區段。</span><span class="sxs-lookup"><span data-stu-id="6c995-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="6c995-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="6c995-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6c995-106">語法</span><span class="sxs-lookup"><span data-stu-id="6c995-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="6c995-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6c995-107">Attribute</span></span>

|           | <span data-ttu-id="6c995-108">描述</span><span class="sxs-lookup"><span data-stu-id="6c995-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="6c995-109">**文字檔**</span><span class="sxs-lookup"><span data-stu-id="6c995-109">**file**</span></span>  | <span data-ttu-id="6c995-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="6c995-110">Optional attribute.</span></span><br><br><span data-ttu-id="6c995-111">指定包含自訂應用程式設定之外部檔案的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="6c995-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="6c995-112">指定的檔案包含在、和專案中指定的相同類型設定 **\<add>** ， **\<remove>** **\<clear>** 並使用與這些元素相同的索引鍵/值組格式。</span><span class="sxs-lookup"><span data-stu-id="6c995-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="6c995-113">指定的路徑是相對於主要設定檔。</span><span class="sxs-lookup"><span data-stu-id="6c995-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="6c995-114">對於 Windows Forms 應用程式，這是二進位檔案夾（例如 */bin/debug*），而不是應用程式佈建檔的位置。</span><span class="sxs-lookup"><span data-stu-id="6c995-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="6c995-115">若是 Web Forms 應用程式，路徑會相對於*web.config*檔案所在的應用程式根目錄。</span><span class="sxs-lookup"><span data-stu-id="6c995-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="6c995-116">如果找不到指定的檔案，執行時間會忽略屬性。</span><span class="sxs-lookup"><span data-stu-id="6c995-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="6c995-117">父元素</span><span class="sxs-lookup"><span data-stu-id="6c995-117">Parent element</span></span>

|     | <span data-ttu-id="6c995-118">描述</span><span class="sxs-lookup"><span data-stu-id="6c995-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6c995-119">**\<configuration>** 元素</span><span class="sxs-lookup"><span data-stu-id="6c995-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="6c995-120">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6c995-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="6c995-121">子元素</span><span class="sxs-lookup"><span data-stu-id="6c995-121">Child elements</span></span>

|     | <span data-ttu-id="6c995-122">描述</span><span class="sxs-lookup"><span data-stu-id="6c995-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="6c995-123">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="6c995-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="6c995-124">清除所有先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="6c995-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="6c995-125">移除先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="6c995-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6c995-126">備註</span><span class="sxs-lookup"><span data-stu-id="6c995-126">Remarks</span></span>

<span data-ttu-id="6c995-127">**\<appSettings>** 元素會儲存自訂的應用程式設定資訊，例如資料庫連接字串、檔案路徑、XML Web Service url，或應用程式的任何其他自訂設定資訊。</span><span class="sxs-lookup"><span data-stu-id="6c995-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="6c995-128">專案中所指定的索引鍵/值組， **\<appSettings>** 會在程式碼中使用類別來存取 <xref:System.Configuration.ConfigurationSettings> 。</span><span class="sxs-lookup"><span data-stu-id="6c995-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="6c995-129">您可以在 web.config **file** **\<appSettings>** 和應用程式佈建檔的元素*Web.config*中使用 file 屬性。</span><span class="sxs-lookup"><span data-stu-id="6c995-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="6c995-130">這個屬性會指定提供其他設定的設定檔，或覆寫在元素中指定的設定 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="6c995-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="6c995-131">**檔**屬性可用於原始檔控制小組開發案例，例如當使用者想要覆寫應用程式佈建檔中指定的專案設定時。</span><span class="sxs-lookup"><span data-stu-id="6c995-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="6c995-132">**檔**屬性所指定的設定檔，必須具有的根節點， **\<appSettings>** 而不是 **\<configuration>** 。</span><span class="sxs-lookup"><span data-stu-id="6c995-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="6c995-133">範例</span><span class="sxs-lookup"><span data-stu-id="6c995-133">Example</span></span>

<span data-ttu-id="6c995-134">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="6c995-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="6c995-135">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="6c995-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="6c995-136">組態檔</span><span class="sxs-lookup"><span data-stu-id="6c995-136">Configuration file</span></span>

<span data-ttu-id="6c995-137">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="6c995-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c995-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c995-138">See also</span></span>

- [<span data-ttu-id="6c995-139">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="6c995-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
