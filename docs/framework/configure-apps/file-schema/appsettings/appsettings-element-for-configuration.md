---
title: <configuration> 的 <appSettings> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 66260d15768781b7fa3d9397b8e8a7d9ad68ab95
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009790"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="98432-102">\<configuration> 的 \<appSettings> 項目</span><span class="sxs-lookup"><span data-stu-id="98432-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="98432-103">包含自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="98432-103">Contains custom application settings.</span></span> <span data-ttu-id="98432-104">這是 .NET Framework 所提供的預先定義設定區段。</span><span class="sxs-lookup"><span data-stu-id="98432-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a><span data-ttu-id="98432-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="98432-105">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="98432-106">屬性</span><span class="sxs-lookup"><span data-stu-id="98432-106">Attribute</span></span>

|           | <span data-ttu-id="98432-107">描述</span><span class="sxs-lookup"><span data-stu-id="98432-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="98432-108">**file**</span><span class="sxs-lookup"><span data-stu-id="98432-108">**file**</span></span>  | <span data-ttu-id="98432-109">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="98432-109">Optional attribute.</span></span><br><br><span data-ttu-id="98432-110">指定包含自訂應用程式設定之外部檔案的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="98432-110">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="98432-111">指定的檔案包含在、和專案中所指定的相同類型設定， **\<add>** **\<remove>** **\<clear>** 並使用與這些專案相同的索引鍵/值組格式。</span><span class="sxs-lookup"><span data-stu-id="98432-111">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="98432-112">指定的路徑是相對於主要設定檔案。</span><span class="sxs-lookup"><span data-stu-id="98432-112">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="98432-113">對於 Windows Forms 應用程式，這是 (的二進位檔案夾，例如 */bin/debug*) ，而不是應用程式佈建檔的位置。</span><span class="sxs-lookup"><span data-stu-id="98432-113">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="98432-114">針對 Web Form 的應用程式，路徑會相對於應用程式根目錄（ *web.config* 檔案所在位置）。</span><span class="sxs-lookup"><span data-stu-id="98432-114">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="98432-115">如果找不到指定的檔案，則執行時間會忽略該屬性。</span><span class="sxs-lookup"><span data-stu-id="98432-115">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="98432-116">父元素</span><span class="sxs-lookup"><span data-stu-id="98432-116">Parent element</span></span>

|     | <span data-ttu-id="98432-117">描述</span><span class="sxs-lookup"><span data-stu-id="98432-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="98432-118">**\<configuration>** 元素</span><span class="sxs-lookup"><span data-stu-id="98432-118">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="98432-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="98432-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="98432-120">子元素</span><span class="sxs-lookup"><span data-stu-id="98432-120">Child elements</span></span>

|     | <span data-ttu-id="98432-121">描述</span><span class="sxs-lookup"><span data-stu-id="98432-121">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="98432-122">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="98432-122">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="98432-123">清除所有先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="98432-123">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="98432-124">移除先前定義的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="98432-124">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="98432-125">備註</span><span class="sxs-lookup"><span data-stu-id="98432-125">Remarks</span></span>

<span data-ttu-id="98432-126">專案會 **\<appSettings>** 儲存自訂的應用程式設定資訊，例如資料庫連接字串、檔案路徑、XML Web 服務 url，或應用程式的任何其他自訂設定資訊。</span><span class="sxs-lookup"><span data-stu-id="98432-126">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="98432-127">在專案中指定的索引鍵/值組 **\<appSettings>** ，會使用類別在程式碼中存取 <xref:System.Configuration.ConfigurationSettings> 。</span><span class="sxs-lookup"><span data-stu-id="98432-127">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="98432-128">您可以在 **\<appSettings>** *Web.config* 和應用程式佈建檔的元素中使用 file 屬性。</span><span class="sxs-lookup"><span data-stu-id="98432-128">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="98432-129">這個屬性會指定提供其他設定的設定檔，或覆寫在元素中指定的設定 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="98432-129">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="98432-130">**檔** 屬性可用於原始檔控制小組開發案例，例如，當使用者想要覆寫應用程式佈建檔中指定的專案設定時。</span><span class="sxs-lookup"><span data-stu-id="98432-130">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="98432-131">**檔** 屬性指定的設定檔必須具有的根節點， **\<appSettings>** 而不是 **\<configuration>** 。</span><span class="sxs-lookup"><span data-stu-id="98432-131">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="98432-132">範例</span><span class="sxs-lookup"><span data-stu-id="98432-132">Example</span></span>

<span data-ttu-id="98432-133">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="98432-133">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="98432-134">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="98432-134">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="98432-135">組態檔</span><span class="sxs-lookup"><span data-stu-id="98432-135">Configuration file</span></span>

<span data-ttu-id="98432-136">此元素可用於應用程式佈建檔、電腦設定檔 (*Machine.config*) ，以及不在應用程式目錄層級的 *Web.config* 檔案。</span><span class="sxs-lookup"><span data-stu-id="98432-136">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="98432-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="98432-137">See also</span></span>

- [<span data-ttu-id="98432-138">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="98432-138">Configuration file schema for the .NET Framework</span></span>](../index.md)
