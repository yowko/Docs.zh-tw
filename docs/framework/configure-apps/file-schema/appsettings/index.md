---
title: 應用程式設定結構描述
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd836f9ebd4d22ad6542c1fadc204b1ea67d1c26
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300773"
---
# <a name="app-settings-schema"></a><span data-ttu-id="fc576-102">應用程式設定結構描述</span><span class="sxs-lookup"><span data-stu-id="fc576-102">App Settings schema</span></span>

<span data-ttu-id="fc576-103">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="fc576-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="fc576-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="fc576-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="fc576-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="fc576-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="fc576-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="fc576-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="fc576-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear>** ](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="fc576-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="fc576-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<remove>** ](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="fc576-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="fc576-109">項目</span><span class="sxs-lookup"><span data-stu-id="fc576-109">Element</span></span> | <span data-ttu-id="fc576-110">描述</span><span class="sxs-lookup"><span data-stu-id="fc576-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="fc576-111"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="fc576-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="fc576-112">包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 標記以控制應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="fc576-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="fc576-113">具有選擇性 **file** 屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="fc576-114"> *\*\<add>** </span><span class="sxs-lookup"><span data-stu-id="fc576-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="fc576-115">定義設定。</span><span class="sxs-lookup"><span data-stu-id="fc576-115">Defines a setting.</span></span> <span data-ttu-id="fc576-116">**\<appSettings>** 的子系。</span><span class="sxs-lookup"><span data-stu-id="fc576-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fc576-117">需要 **key** 和 **value** 屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="fc576-118"> *\*\<clear>** </span><span class="sxs-lookup"><span data-stu-id="fc576-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="fc576-119">清除所有設定。</span><span class="sxs-lookup"><span data-stu-id="fc576-119">Clears all settings.</span></span> <span data-ttu-id="fc576-120">**\<appSettings>** 的子系。</span><span class="sxs-lookup"><span data-stu-id="fc576-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fc576-121">沒有任何屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-121">Has no attributes.</span></span> |
| [<span data-ttu-id="fc576-122"> *\*\<remove>** </span><span class="sxs-lookup"><span data-stu-id="fc576-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="fc576-123">移除設定。</span><span class="sxs-lookup"><span data-stu-id="fc576-123">Removes a setting.</span></span> <span data-ttu-id="fc576-124">**\<appSettings>** 的子系。</span><span class="sxs-lookup"><span data-stu-id="fc576-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="fc576-125">需要 **key** 屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="fc576-126">\<appSettings> 項目</span><span class="sxs-lookup"><span data-stu-id="fc576-126">\<appSettings> element</span></span>

<span data-ttu-id="fc576-127">此項目包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 標記以控制應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="fc576-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="fc576-128">它會定義 **file** 的選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="fc576-129">\<add> 項目</span><span class="sxs-lookup"><span data-stu-id="fc576-129">\<add> element</span></span>

<span data-ttu-id="fc576-130">新增自訂應用程式設定作為應用程式設定集合的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="fc576-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="fc576-131">它會定義 **key** 和 **value** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="fc576-132">\<clear> 項目</span><span class="sxs-lookup"><span data-stu-id="fc576-132">\<clear> element</span></span>

<span data-ttu-id="fc576-133">移除所繼承之自訂應用程式設定的所有參考，只允許 **\<clear>** 項目之後由 **\<add>** 項目新增的參考。</span><span class="sxs-lookup"><span data-stu-id="fc576-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="fc576-134">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="fc576-135">\<remove> 項目</span><span class="sxs-lookup"><span data-stu-id="fc576-135">\<remove> element</span></span>

<span data-ttu-id="fc576-136">從應用程式設定集合移除所繼承之自訂應用程式設定的參考。</span><span class="sxs-lookup"><span data-stu-id="fc576-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="fc576-137">它會定義 **key** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="fc576-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="fc576-138">範例</span><span class="sxs-lookup"><span data-stu-id="fc576-138">Example</span></span>

<span data-ttu-id="fc576-139">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="fc576-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="fc576-140">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="fc576-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="fc576-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc576-141">See also</span></span>

- [<span data-ttu-id="fc576-142">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="fc576-142">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="fc576-143">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="fc576-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
