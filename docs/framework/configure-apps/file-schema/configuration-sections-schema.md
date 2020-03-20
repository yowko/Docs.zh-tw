---
title: 配置部分架構
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: 28f936e6fd7c9e7f6f895396df8e8b8d36ab9139
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155319"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="c8cde-102">配置部分架構</span><span class="sxs-lookup"><span data-stu-id="c8cde-102">Configuration sections schema</span></span>

<span data-ttu-id="c8cde-103">配置部分架構包含在設定檔中定義自訂設置的元素。</span><span class="sxs-lookup"><span data-stu-id="c8cde-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="c8cde-104">有關設定檔和架構的一般資訊，請參閱[.NET 框架的設定檔架構](index.md)。</span><span class="sxs-lookup"><span data-stu-id="c8cde-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="c8cde-105">[**\<配置>**](configuration-element.md)

[**配置\<>**](configsections-element-for-configuration.md)

[**清除>\<刪除**](remove-element-for-configsections.md)[**>\<節**](section-element.md)>
[**部分\<組>**](sectiongroup-element-for-configsections.md) [\*\* \< \*\*](clear-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="c8cde-105">[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<clear>**](clear-element-for-configsections.md)
[**\<remove>**](remove-element-for-configsections.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>

|     | <span data-ttu-id="c8cde-106">描述</span><span class="sxs-lookup"><span data-stu-id="c8cde-106">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c8cde-107">用於配置>的透明>\*\* \< \*\* \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="c8cde-107">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="c8cde-108">清除以前定義的所有節和節組。</span><span class="sxs-lookup"><span data-stu-id="c8cde-108">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="c8cde-109">**\<明確>**</span><span class="sxs-lookup"><span data-stu-id="c8cde-109">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="c8cde-110">清除以前定義的所有節和節組。</span><span class="sxs-lookup"><span data-stu-id="c8cde-110">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="c8cde-111">**\<配置部分>**</span><span class="sxs-lookup"><span data-stu-id="c8cde-111">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="c8cde-112">包含配置部分和命名空間聲明。</span><span class="sxs-lookup"><span data-stu-id="c8cde-112">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="c8cde-113">\*\* \<刪除\*\*\*\*配置\<>>\*\*</span><span class="sxs-lookup"><span data-stu-id="c8cde-113">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="c8cde-114">刪除預定義的節或節組。</span><span class="sxs-lookup"><span data-stu-id="c8cde-114">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="c8cde-115">>**和\<部分組**>**\<的配置部分**>\*\* \< \*\*</span><span class="sxs-lookup"><span data-stu-id="c8cde-115">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="c8cde-116">包含配置部分聲明。</span><span class="sxs-lookup"><span data-stu-id="c8cde-116">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="c8cde-117">部分組>，用於**\<\*\*\*\*\<配置>**</span><span class="sxs-lookup"><span data-stu-id="c8cde-117">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c8cde-118">為配置部分定義命名空間。</span><span class="sxs-lookup"><span data-stu-id="c8cde-118">Defines a namespace for configuration sections.</span></span> |
