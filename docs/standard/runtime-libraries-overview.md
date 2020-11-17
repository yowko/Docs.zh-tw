---
title: 執行時間程式庫總覽
description: 瞭解 [內容] 的 [執行時間程式庫] 區段中包含的內容。
author: tdykstra
ms.date: 11/12/2020
ms.openlocfilehash: 5a8f888e1778553e2968277738cfef5134f11589
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687891"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="776d4-103">執行時間程式庫總覽</span><span class="sxs-lookup"><span data-stu-id="776d4-103">Runtime libraries overview</span></span>

<span data-ttu-id="776d4-104">[.Net 運行](../core/introduction.md#sdk-and-runtimes)時間（安裝在電腦上以供與[framework 相依的應用程式](../core/introduction.md#deployment-models)使用）有一組廣泛的標準類別庫，也稱為[運行](glossary.md#runtime)時間程式庫、[架構程式庫](glossary.md#framework-libraries)，或[ (BCL) 的基類庫](glossary.md#bcl)。</span><span class="sxs-lookup"><span data-stu-id="776d4-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries, known as [runtime libraries](glossary.md#runtime), [framework libraries](glossary.md#framework-libraries), or the [base class library (BCL)](glossary.md#bcl).</span></span> <span data-ttu-id="776d4-105">此外，NuGet 套件中提供執行時間程式庫的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="776d4-105">In addition, there are extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="776d4-106">這些程式庫提供許多一般和應用程式特定類型、演算法和公用程式功能的執行方式。</span><span class="sxs-lookup"><span data-stu-id="776d4-106">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="776d4-107">執行階段程式庫</span><span class="sxs-lookup"><span data-stu-id="776d4-107">Runtime libraries</span></span>

<span data-ttu-id="776d4-108">這些程式庫提供基礎類型和公用程式功能，而且是所有其他 .NET 類別庫的基底。</span><span class="sxs-lookup"><span data-stu-id="776d4-108">These libraries provide the foundational types and utility functionality and are the base of all other .NET class libraries.</span></span> <span data-ttu-id="776d4-109">例如 <xref:System.String?displayProperty=nameWithType> ，類別可提供用來處理字串的 api。</span><span class="sxs-lookup"><span data-stu-id="776d4-109">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span> <span data-ttu-id="776d4-110">另一個範例是 [序列化程式庫](serialization/index.md)。</span><span class="sxs-lookup"><span data-stu-id="776d4-110">Another example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="776d4-111">執行時間程式庫的延伸模組</span><span class="sxs-lookup"><span data-stu-id="776d4-111">Extensions to the runtime libraries</span></span>

<span data-ttu-id="776d4-112">某些程式庫是在 NuGet 套件中提供，而不是包含在執行時間的 [共用架構](glossary.md#shared-framework)中。</span><span class="sxs-lookup"><span data-stu-id="776d4-112">Some libraries are provided in NuGet packages rather than included in the runtime's [shared framework](glossary.md#shared-framework).</span></span> <span data-ttu-id="776d4-113">例如：</span><span class="sxs-lookup"><span data-stu-id="776d4-113">For example:</span></span>

* [<span data-ttu-id="776d4-114">Logging</span><span class="sxs-lookup"><span data-stu-id="776d4-114">Logging</span></span>](../core/extensions/logging.md)
* [<span data-ttu-id="776d4-115">相依性插入</span><span class="sxs-lookup"><span data-stu-id="776d4-115">Dependency injection</span></span>](../core/extensions/dependency-injection.md)
* [<span data-ttu-id="776d4-116">設定</span><span class="sxs-lookup"><span data-stu-id="776d4-116">Configuration</span></span>](../core/extensions/configuration.md)

## <a name="see-also"></a><span data-ttu-id="776d4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="776d4-117">See also</span></span>

* [<span data-ttu-id="776d4-118">.NET 簡介</span><span class="sxs-lookup"><span data-stu-id="776d4-118">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="776d4-119">安裝 .NET SDK 或執行時間</span><span class="sxs-lookup"><span data-stu-id="776d4-119">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="776d4-120">選取要使用的已安裝 .NET SDK 或執行階段版本</span><span class="sxs-lookup"><span data-stu-id="776d4-120">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="776d4-121">發佈與 framework 相依的應用程式</span><span class="sxs-lookup"><span data-stu-id="776d4-121">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
