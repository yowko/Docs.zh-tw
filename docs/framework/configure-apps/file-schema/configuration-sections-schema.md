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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674814"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="9c985-102">組態區段結構描述</span><span class="sxs-lookup"><span data-stu-id="9c985-102">Configuration sections schema</span></span>

<span data-ttu-id="9c985-103">組態區段結構描述包含在組態檔中定義自訂設定的項目。</span><span class="sxs-lookup"><span data-stu-id="9c985-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="9c985-104">如需組態檔和結構描述的一般資訊，請參閱[適用於.NET Framework 的組態檔結構描述](~/docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9c985-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="9c985-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9c985-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9c985-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="9c985-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="9c985-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="9c985-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="9c985-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="9c985-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="9c985-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="9c985-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="9c985-110">**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="9c985-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="9c985-111">描述</span><span class="sxs-lookup"><span data-stu-id="9c985-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9c985-112">**\<clear>** for **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="9c985-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="9c985-113">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="9c985-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="9c985-114">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="9c985-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="9c985-115">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="9c985-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="9c985-116">**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="9c985-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="9c985-117">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="9c985-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="9c985-118">**\<remove>** for **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="9c985-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="9c985-119">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="9c985-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="9c985-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="9c985-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="9c985-121">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="9c985-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="9c985-122">**\<sectionGroup>** for **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="9c985-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="9c985-123">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9c985-123">Defines a namespace for configuration sections.</span></span> |
