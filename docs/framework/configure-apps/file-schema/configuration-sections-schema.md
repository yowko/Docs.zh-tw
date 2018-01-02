---
title: "組態區段結構描述"
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da9af8fd24f1bf6e6effd411ad37490a4ee08804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="1662e-102">組態區段結構描述</span><span class="sxs-lookup"><span data-stu-id="1662e-102">Configuration sections schema</span></span>

<span data-ttu-id="1662e-103">組態區段結構描述包含在組態檔中定義自訂的設定項目。</span><span class="sxs-lookup"><span data-stu-id="1662e-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="1662e-104">如需組態檔和結構描述的一般資訊，請參閱[適用於.NET Framework 組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1662e-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="1662e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1662e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="1662e-106">[**\<c >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="1662e-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="1662e-107">[**\<清除 >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="1662e-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="1662e-108">[**\<移除 >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="1662e-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="1662e-109">[**\<區段 >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="1662e-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="1662e-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="1662e-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="1662e-111">描述</span><span class="sxs-lookup"><span data-stu-id="1662e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1662e-112">**\<清除 >**如** \<c >**</span><span class="sxs-lookup"><span data-stu-id="1662e-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="1662e-113">清除所有先前定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="1662e-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="1662e-114">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="1662e-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="1662e-115">清除所有先前定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="1662e-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="1662e-116">**\<c >**</span><span class="sxs-lookup"><span data-stu-id="1662e-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="1662e-117">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="1662e-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="1662e-118">**\<移除 >**如** \<c >**</span><span class="sxs-lookup"><span data-stu-id="1662e-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="1662e-119">預先定義的區段或區段群組中移除。</span><span class="sxs-lookup"><span data-stu-id="1662e-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="1662e-120">**\<區段 >**如** \<c >**和** \<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="1662e-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="1662e-121">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="1662e-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="1662e-122">**\<sectionGroup >**如** \<c >**</span><span class="sxs-lookup"><span data-stu-id="1662e-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="1662e-123">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1662e-123">Defines a namespace for configuration sections.</span></span> |
