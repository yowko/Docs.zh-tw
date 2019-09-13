---
title: 相依性載入-.NET Core
description: .NET Core 中的 managed 和非受控相依性載入總覽
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 0388bd1fa29ce1caad93c917503dac9eed8974e1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926399"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="c6610-103">.NET Core 中的相依性載入</span><span class="sxs-lookup"><span data-stu-id="c6610-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="c6610-104">每個 .NET Core 應用程式都有相依性。</span><span class="sxs-lookup"><span data-stu-id="c6610-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="c6610-105">即使是簡單`hello world`的應用程式也會相依于 .net Core 類別庫的某些部分。</span><span class="sxs-lookup"><span data-stu-id="c6610-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="c6610-106">瞭解 .NET Core 預設元件載入邏輯有助於瞭解和偵測一般的部署問題。</span><span class="sxs-lookup"><span data-stu-id="c6610-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="c6610-107">在某些應用程式中，相依性會在執行時間以動態方式決定。</span><span class="sxs-lookup"><span data-stu-id="c6610-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="c6610-108">在這些情況下，請務必瞭解如何載入 managed 元件和非受控相依性。</span><span class="sxs-lookup"><span data-stu-id="c6610-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="c6610-109">了解 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="c6610-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="c6610-110"><xref:System.Runtime.Loader.AssemblyLoadContext> API 是 .net Core 載入設計的核心。</span><span class="sxs-lookup"><span data-stu-id="c6610-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="c6610-111">[瞭解 AssemblyLoadCoNtext](understanding-assemblyloadcontext.md)一文提供設計的概念總覽。</span><span class="sxs-lookup"><span data-stu-id="c6610-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="c6610-112">載入詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6610-112">Loading details</span></span>

<span data-ttu-id="c6610-113">下列幾篇文章會簡要說明載入演算法的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="c6610-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="c6610-114">Managed 元件載入演算法</span><span class="sxs-lookup"><span data-stu-id="c6610-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="c6610-115">附屬元件載入演算法</span><span class="sxs-lookup"><span data-stu-id="c6610-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="c6610-116">非受控（原生）程式庫載入演算法</span><span class="sxs-lookup"><span data-stu-id="c6610-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="c6610-117">預設探查</span><span class="sxs-lookup"><span data-stu-id="c6610-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="c6610-118">建立具有外掛程式的 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6610-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="c6610-119">[使用外掛程式建立 .Net Core 應用程式](../tutorials/creating-app-with-plugin-support.md)教學課程說明如何建立自訂 AssemblyLoadCoNtext。</span><span class="sxs-lookup"><span data-stu-id="c6610-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="c6610-120">它會使用<xref:System.Runtime.Loader.AssemblyDependencyResolver>來解析外掛程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="c6610-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="c6610-121">本教學課程會正確地隔離外掛程式與主控應用程式的相依性。</span><span class="sxs-lookup"><span data-stu-id="c6610-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="c6610-122">如何使用 .NET Core 中的組件卸載功能及對其進行偵錯</span><span class="sxs-lookup"><span data-stu-id="c6610-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="c6610-123">[如何在 .Net Core 中使用和 debug 元件卸載功能](../../standard/assembly/unloadability-howto.md)一文是逐步教學課程。</span><span class="sxs-lookup"><span data-stu-id="c6610-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability-howto.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="c6610-124">它會顯示如何載入 .NET Core 應用程式、執行，然後將它卸載。</span><span class="sxs-lookup"><span data-stu-id="c6610-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="c6610-125">本文也提供調試秘訣。</span><span class="sxs-lookup"><span data-stu-id="c6610-125">The article also provides debugging tips.</span></span>
