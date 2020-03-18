---
title: 依賴項載入 - .NET 核心
description: .NET Core 中的託管和非託管依賴項載入概述
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416673"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="35a35-103">.NET 核心中的依賴項載入</span><span class="sxs-lookup"><span data-stu-id="35a35-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="35a35-104">每個 .NET 核心應用程式都有依賴關係。</span><span class="sxs-lookup"><span data-stu-id="35a35-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="35a35-105">即使是簡單的`hello world`應用程式也依賴于 .NET Core 類庫的某些部分。</span><span class="sxs-lookup"><span data-stu-id="35a35-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="35a35-106">瞭解 .NET 核心預設程式集載入邏輯有助於瞭解和調試典型的部署問題。</span><span class="sxs-lookup"><span data-stu-id="35a35-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="35a35-107">在某些應用程式中，依賴項在運行時動態確定。</span><span class="sxs-lookup"><span data-stu-id="35a35-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="35a35-108">在這些情況下，瞭解託管程式集和非託管依賴項的載入方式至關重要。</span><span class="sxs-lookup"><span data-stu-id="35a35-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="35a35-109">了解 AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="35a35-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="35a35-110">API<xref:System.Runtime.Loader.AssemblyLoadContext>是 .NET 核心載入設計的核心。</span><span class="sxs-lookup"><span data-stu-id="35a35-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="35a35-111">["瞭解程式集載入上下文"](understanding-assemblyloadcontext.md)一文提供了設計的概念概述。</span><span class="sxs-lookup"><span data-stu-id="35a35-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="35a35-112">載入詳細資料</span><span class="sxs-lookup"><span data-stu-id="35a35-112">Loading details</span></span>

<span data-ttu-id="35a35-113">載入演算法詳細資訊在以下幾篇文章中簡要介紹：</span><span class="sxs-lookup"><span data-stu-id="35a35-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="35a35-114">託管程式集載入演算法</span><span class="sxs-lookup"><span data-stu-id="35a35-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="35a35-115">衛星程式集載入演算法</span><span class="sxs-lookup"><span data-stu-id="35a35-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="35a35-116">非託管（本機）庫載入演算法</span><span class="sxs-lookup"><span data-stu-id="35a35-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="35a35-117">預設探測</span><span class="sxs-lookup"><span data-stu-id="35a35-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="35a35-118">建立具有外掛程式的 .NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="35a35-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="35a35-119">本教程[使用外掛程式創建 .NET Core 應用程式](../tutorials/creating-app-with-plugin-support.md)介紹如何創建自訂程式集 LoadCoNtext。</span><span class="sxs-lookup"><span data-stu-id="35a35-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="35a35-120">它使用<xref:System.Runtime.Loader.AssemblyDependencyResolver>解析外掛程式的依賴項。</span><span class="sxs-lookup"><span data-stu-id="35a35-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="35a35-121">本教程將外掛程式的依賴項與託管應用程式正確隔離。</span><span class="sxs-lookup"><span data-stu-id="35a35-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="35a35-122">如何使用 .NET Core 中的組件卸載功能及對其進行偵錯</span><span class="sxs-lookup"><span data-stu-id="35a35-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="35a35-123">在 .NET Core 文章中的["如何使用和偵錯工具集可卸載性](../../standard/assembly/unloadability.md)"是一個分步教程。</span><span class="sxs-lookup"><span data-stu-id="35a35-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="35a35-124">它演示如何載入 .NET Core 應用程式，執行，然後卸載它。</span><span class="sxs-lookup"><span data-stu-id="35a35-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="35a35-125">本文還提供調試提示。</span><span class="sxs-lookup"><span data-stu-id="35a35-125">The article also provides debugging tips.</span></span>
