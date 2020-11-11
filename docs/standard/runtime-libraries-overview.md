---
title: 執行時間程式庫總覽
description: 瞭解 [內容] 的 [執行時間程式庫] 區段中包含的內容。
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507606"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="d1349-103">執行時間程式庫總覽</span><span class="sxs-lookup"><span data-stu-id="d1349-103">Runtime libraries overview</span></span>

<span data-ttu-id="d1349-104">[.Net 運行](../core/introduction.md#sdk-and-runtimes)時間（安裝在電腦上以供與[framework 相依的應用程式](../core/introduction.md#deployment-models)使用）有一組廣泛的標準類別庫：</span><span class="sxs-lookup"><span data-stu-id="d1349-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries:</span></span>

* <span data-ttu-id="d1349-105">包含在執行時間中的核心集，也稱為 [基類程式庫 (BCL) ](glossary.md#bcl)。</span><span class="sxs-lookup"><span data-stu-id="d1349-105">The core set, included in the runtime and known as the [base class libraries (BCL)](glossary.md#bcl).</span></span>
* <span data-ttu-id="d1349-106">包含在執行時間中的完整集合，也稱為 [運行](glossary.md#runtime) 時間程式庫或 [架構程式庫](glossary.md#framework)。</span><span class="sxs-lookup"><span data-stu-id="d1349-106">The complete set, included in the runtime and known as the [runtime libraries](glossary.md#runtime) or [framework libraries](glossary.md#framework).</span></span>
* <span data-ttu-id="d1349-107">NuGet 套件中提供的執行時間程式庫延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d1349-107">Extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="d1349-108">這些程式庫提供許多一般和應用程式特定類型、演算法和公用程式功能的執行方式。</span><span class="sxs-lookup"><span data-stu-id="d1349-108">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="base-class-libraries"></a><span data-ttu-id="d1349-109">基類庫</span><span class="sxs-lookup"><span data-stu-id="d1349-109">Base class libraries</span></span>

<span data-ttu-id="d1349-110">BCL 提供基礎類型和公用程式功能，而且是所有其他 .NET 類別庫的基底。</span><span class="sxs-lookup"><span data-stu-id="d1349-110">The BCL provides the foundational types and utility functionality and is the base of all other .NET class libraries.</span></span> <span data-ttu-id="d1349-111">例如 <xref:System.String?displayProperty=nameWithType> ，類別可提供用來處理字串的 api。</span><span class="sxs-lookup"><span data-stu-id="d1349-111">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="d1349-112">執行階段程式庫</span><span class="sxs-lookup"><span data-stu-id="d1349-112">Runtime libraries</span></span>

<span data-ttu-id="d1349-113">也稱為架構程式庫，執行時間程式庫建基於 BCL，以提供公用程式 Api 來進行一般工作。</span><span class="sxs-lookup"><span data-stu-id="d1349-113">Also known as the framework libraries, the runtime libraries build on the BCL to provide utility APIs for common tasks.</span></span> <span data-ttu-id="d1349-114">例如，序列化連結 [庫](serialization/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d1349-114">An example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="d1349-115">執行時間程式庫的延伸模組</span><span class="sxs-lookup"><span data-stu-id="d1349-115">Extensions to the runtime libraries</span></span>

<span data-ttu-id="d1349-116">部分執行時間程式庫會在 NuGet 套件中提供，而不是內建至針對與 framework 相依的應用程式所安裝的執行時間。</span><span class="sxs-lookup"><span data-stu-id="d1349-116">Some of the runtime libraries are provided in NuGet packages rather than built-in to the runtime that is installed for framework-dependent apps.</span></span> <span data-ttu-id="d1349-117">例如， [.Net 記錄 API](../core/extensions/logging.md)。</span><span class="sxs-lookup"><span data-stu-id="d1349-117">An example is the [.NET Logging API](../core/extensions/logging.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1349-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1349-118">See also</span></span>

* [<span data-ttu-id="d1349-119">.NET 簡介</span><span class="sxs-lookup"><span data-stu-id="d1349-119">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="d1349-120">安裝 .NET SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="d1349-120">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="d1349-121">選取要使用的已安裝 .NET SDK 或執行階段版本</span><span class="sxs-lookup"><span data-stu-id="d1349-121">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="d1349-122">發佈與 framework 相依的應用程式</span><span class="sxs-lookup"><span data-stu-id="d1349-122">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
