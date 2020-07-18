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
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441657"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="e56e3-102">設定區段架構</span><span class="sxs-lookup"><span data-stu-id="e56e3-102">Configuration sections schema</span></span>

<span data-ttu-id="e56e3-103">設定區段架構包含的元素會定義設定檔案中的自訂設定。</span><span class="sxs-lookup"><span data-stu-id="e56e3-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="e56e3-104">如需設定檔案和架構的一般資訊，請參閱[.NET Framework 的設定檔架構](index.md)。</span><span class="sxs-lookup"><span data-stu-id="e56e3-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="e56e3-105">描述</span><span class="sxs-lookup"><span data-stu-id="e56e3-105">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="e56e3-106">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="e56e3-106">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="e56e3-107">**\<section>** 針對 **\<configSections>** 和**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="e56e3-107">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="e56e3-108">包含設定區段宣告。</span><span class="sxs-lookup"><span data-stu-id="e56e3-108">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="e56e3-109">**\<sectionGroup>** 對於**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="e56e3-109">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="e56e3-110">定義設定區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e56e3-110">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="e56e3-111">未實現的元素</span><span class="sxs-lookup"><span data-stu-id="e56e3-111">Unimplemented elements</span></span>

<span data-ttu-id="e56e3-112">下列元素不會有任何影響，因此不應使用：</span><span class="sxs-lookup"><span data-stu-id="e56e3-112">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
