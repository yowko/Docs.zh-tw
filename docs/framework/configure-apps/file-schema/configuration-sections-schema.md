---
title: 設定區段架構
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a17d30af9d7abc3eea6b87d5e8768ac49a7c05ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118922"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="5b74e-102">設定區段架構</span><span class="sxs-lookup"><span data-stu-id="5b74e-102">Configuration sections schema</span></span>

<span data-ttu-id="5b74e-103">設定區段架構包含的元素會定義設定檔案中的自訂設定。</span><span class="sxs-lookup"><span data-stu-id="5b74e-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="5b74e-104">如需設定檔案和架構的一般資訊，請參閱[.NET Framework 的設定檔架構](index.md)。</span><span class="sxs-lookup"><span data-stu-id="5b74e-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="5b74e-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5b74e-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="5b74e-106">[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="5b74e-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="5b74e-107">[ **\<清除 >** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="5b74e-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="5b74e-108">[ **\<移除 >** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="5b74e-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="5b74e-109">[ **\<區段 >** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="5b74e-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="5b74e-110"> **\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="5b74e-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="5b74e-111">描述</span><span class="sxs-lookup"><span data-stu-id="5b74e-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5b74e-112"> **\<清除** **\<configSections**的 > ></span><span class="sxs-lookup"><span data-stu-id="5b74e-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="5b74e-113">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="5b74e-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="5b74e-114"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="5b74e-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="5b74e-115">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="5b74e-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="5b74e-116"> **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="5b74e-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="5b74e-117">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="5b74e-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="5b74e-118"> **\<移除** **\<configSections**的 > ></span><span class="sxs-lookup"><span data-stu-id="5b74e-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="5b74e-119">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="5b74e-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="5b74e-120"> **\<configSections >** 和 **\<sectionGroup**的 **\<區段 >** ></span><span class="sxs-lookup"><span data-stu-id="5b74e-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="5b74e-121">包含設定區段宣告。</span><span class="sxs-lookup"><span data-stu-id="5b74e-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="5b74e-122"> **\<configSections**的 **\<sectionGroup >** ></span><span class="sxs-lookup"><span data-stu-id="5b74e-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="5b74e-123">定義設定區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="5b74e-123">Defines a namespace for configuration sections.</span></span> |
