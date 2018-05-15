---
title: 組態區段結構描述
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: edd2b2e11b02d69b7bba7c3cc7d8a9a0814e0c51
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="214a9-102">組態區段結構描述</span><span class="sxs-lookup"><span data-stu-id="214a9-102">Configuration sections schema</span></span>

<span data-ttu-id="214a9-103">組態區段結構描述包含在組態檔中定義自訂的設定項目。</span><span class="sxs-lookup"><span data-stu-id="214a9-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="214a9-104">如需組態檔和結構描述的一般資訊，請參閱[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="214a9-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="214a9-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="214a9-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="214a9-106">[**\<c >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="214a9-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="214a9-107">[**\<清除 >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="214a9-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="214a9-108">[**\<移除 >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="214a9-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="214a9-109">[**\<區段 >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="214a9-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="214a9-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="214a9-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="214a9-111">描述</span><span class="sxs-lookup"><span data-stu-id="214a9-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="214a9-112">**\<清除 >** 如 **\<c >**</span><span class="sxs-lookup"><span data-stu-id="214a9-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="214a9-113">清除所有先前定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="214a9-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="214a9-114">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="214a9-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="214a9-115">清除所有先前定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="214a9-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="214a9-116">**\<c >**</span><span class="sxs-lookup"><span data-stu-id="214a9-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="214a9-117">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="214a9-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="214a9-118">**\<移除 >** 如 **\<c >**</span><span class="sxs-lookup"><span data-stu-id="214a9-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="214a9-119">預先定義的區段或區段群組中移除。</span><span class="sxs-lookup"><span data-stu-id="214a9-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="214a9-120">**\<區段 >** 如 **\<c >** 和 **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="214a9-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="214a9-121">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="214a9-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="214a9-122">**\<sectionGroup >** 如 **\<c >**</span><span class="sxs-lookup"><span data-stu-id="214a9-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="214a9-123">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="214a9-123">Defines a namespace for configuration sections.</span></span> |
