---
title: 應用程式設定結構描述
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215420"
---
# <a name="app-settings-schema"></a><span data-ttu-id="d5c92-102">應用程式設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d5c92-102">App Settings schema</span></span>

<span data-ttu-id="d5c92-103">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="d5c92-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="d5c92-104">元素</span><span class="sxs-lookup"><span data-stu-id="d5c92-104">Element</span></span> | <span data-ttu-id="d5c92-105">描述</span><span class="sxs-lookup"><span data-stu-id="d5c92-105">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="d5c92-106">包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 標記以控制應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="d5c92-106">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="d5c92-107">具有選擇性 **file** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-107">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="d5c92-108">定義設定。</span><span class="sxs-lookup"><span data-stu-id="d5c92-108">Defines a setting.</span></span> <span data-ttu-id="d5c92-109">的子系 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="d5c92-109">Child of **\<appSettings>**.</span></span> <span data-ttu-id="d5c92-110">需要 **key** 和 **value** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-110">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="d5c92-111">清除所有設定。</span><span class="sxs-lookup"><span data-stu-id="d5c92-111">Clears all settings.</span></span> <span data-ttu-id="d5c92-112">的子系 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="d5c92-112">Child of **\<appSettings>**.</span></span> <span data-ttu-id="d5c92-113">沒有任何屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-113">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="d5c92-114">移除設定。</span><span class="sxs-lookup"><span data-stu-id="d5c92-114">Removes a setting.</span></span> <span data-ttu-id="d5c92-115">的子系 **\<appSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="d5c92-115">Child of **\<appSettings>**.</span></span> <span data-ttu-id="d5c92-116">需要 **key** 屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-116">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="d5c92-117">\<appSettings> 項目</span><span class="sxs-lookup"><span data-stu-id="d5c92-117">\<appSettings> element</span></span>

<span data-ttu-id="d5c92-118">此元素包含 **\<add>** 、 **\<clear>** 和 **\<remove>** 標記，以控制應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="d5c92-118">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="d5c92-119">它會定義 **file** 的選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-119">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="d5c92-120">\<add> 項目</span><span class="sxs-lookup"><span data-stu-id="d5c92-120">\<add> element</span></span>

<span data-ttu-id="d5c92-121">新增自訂應用程式設定作為應用程式設定集合的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="d5c92-121">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="d5c92-122">它會定義 **key** 和 **value** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-122">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="d5c92-123">\<clear> 項目</span><span class="sxs-lookup"><span data-stu-id="d5c92-123">\<clear> element</span></span>

<span data-ttu-id="d5c92-124">移除繼承自訂應用程式設定的所有參考，並僅允許元素後面的專案所新增的參考 **\<add>** **\<clear>** 。</span><span class="sxs-lookup"><span data-stu-id="d5c92-124">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="d5c92-125">它不會定義任何屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-125">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="d5c92-126">\<remove> 項目</span><span class="sxs-lookup"><span data-stu-id="d5c92-126">\<remove> element</span></span>

<span data-ttu-id="d5c92-127">從應用程式設定集合移除所繼承之自訂應用程式設定的參考。</span><span class="sxs-lookup"><span data-stu-id="d5c92-127">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="d5c92-128">它會定義 **key** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="d5c92-128">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="d5c92-129">範例</span><span class="sxs-lookup"><span data-stu-id="d5c92-129">Example</span></span>

<span data-ttu-id="d5c92-130">下列範例會顯示定義自訂應用程式設定的外部應用程式設定檔 (*custom.config*)：</span><span class="sxs-lookup"><span data-stu-id="d5c92-130">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="d5c92-131">下列範例會顯示應用程式組態檔，該檔案會取用外部設定檔中的設定，並設定其專屬的應用程式設定：</span><span class="sxs-lookup"><span data-stu-id="d5c92-131">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d5c92-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5c92-132">See also</span></span>

- [<span data-ttu-id="d5c92-133">應用程式設定總覽</span><span class="sxs-lookup"><span data-stu-id="d5c92-133">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="d5c92-134">Application Settings Architecture</span><span class="sxs-lookup"><span data-stu-id="d5c92-134">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
