---
title: "本機環境教學課程 - C# 本機快速入門"
description: "本快速入門提供於本機執行快速入門的基本概念"
author: billwagner
ms.topic: article
ms.date: 12/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9957f524e04f8ff64d4f640cf085b16cf9a2c0c6
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="local-environment"></a><span data-ttu-id="d20bb-103">本機環境</span><span class="sxs-lookup"><span data-stu-id="d20bb-103">Local environment</span></span>

<span data-ttu-id="d20bb-104">嘗試於本機執行快速入門的第一個步驟，便是在本機電腦上設定開發環境。</span><span class="sxs-lookup"><span data-stu-id="d20bb-104">The first step to trying a quickstart locally is to setup a development environment on your local machine.</span></span>
<span data-ttu-id="d20bb-105">.NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="d20bb-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

<span data-ttu-id="d20bb-106">或者，您可以安裝 [.NET Core SDK](http://dot.net/core) \(英文\) 和 [Visual Studio Code](https://code.visualstudio.com/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="d20bb-106">Alternatively, you can install the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="d20bb-107">基本應用程式開發流程</span><span class="sxs-lookup"><span data-stu-id="d20bb-107">Basic application development flow</span></span>

<span data-ttu-id="d20bb-108">您會使用 [`dotnet new`](../../core/tools/dotnet-new.md) 命令建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="d20bb-108">You'll create applications using the [`dotnet new`](../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="d20bb-109">此命令會產生應用程式所需的檔案和資產。</span><span class="sxs-lookup"><span data-stu-id="d20bb-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="d20bb-110">快速入門全都會使用 `console` 應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="d20bb-110">The quickstarts all use the `console` application type.</span></span>

<span data-ttu-id="d20bb-111">其他會用到的命令為用來建置可執行檔的 [`dotnet build`](../../core/tools/dotnet-build.md)，以及用來執行可執行檔的 [`dotnet run`](../../core/tools/dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="d20bb-111">The other commands you'll use are [`dotnet build`](../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-quickstart"></a><span data-ttu-id="d20bb-112">挑選快速入門</span><span class="sxs-lookup"><span data-stu-id="d20bb-112">Pick your quickstart</span></span>

<span data-ttu-id="d20bb-113">您可以從下列任何一個快速入門開始：</span><span class="sxs-lookup"><span data-stu-id="d20bb-113">You can start with any of the following quickstarts:</span></span>

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[<span data-ttu-id="d20bb-114">C# 中的數字</span><span class="sxs-lookup"><span data-stu-id="d20bb-114">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="d20bb-115">在 [C# 中的數字](numbers-in-csharp-local.md)快速入門中，您將會學習電腦儲存數字的方式，以及如何使用不同的數值型別來執行計算。</span><span class="sxs-lookup"><span data-stu-id="d20bb-115">In the [Numbers in C#](numbers-in-csharp-local.md) quickstart, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="d20bb-116">您將會學習進位的基本概念，以及如何使用 C# 執行數學計算。</span><span class="sxs-lookup"><span data-stu-id="d20bb-116">You'll learn the basics of rounding, and how to perform mathematical calculations using C#.</span></span> 

<span data-ttu-id="d20bb-117">此快速入門假設您已完成 [Hello World](hello-world.yml) 教學課程。</span><span class="sxs-lookup"><span data-stu-id="d20bb-117">This quickstart assumes that you have finished the [Hello world](hello-world.yml) tutorial.</span></span>

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[<span data-ttu-id="d20bb-118">分支和迴圈</span><span class="sxs-lookup"><span data-stu-id="d20bb-118">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="d20bb-119">[分支和迴圈](branches-and-loops-local.md)快速入門會指導您如何根據儲存在變數中的值，以選取不同程式碼執行路徑的基本概念。</span><span class="sxs-lookup"><span data-stu-id="d20bb-119">The [Branches and loops](branches-and-loops-local.md) quickstart teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="d20bb-120">您將會學習控制流程的基本概念，也就是程式做出決定並選擇不同動作的基礎機制。</span><span class="sxs-lookup"><span data-stu-id="d20bb-120">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span> 

<span data-ttu-id="d20bb-121">此入門課程假設您已經完成 [Hello World](hello-world.yml) 和 [C# 中的數字](numbers-in-csharp-local.md)課程。</span><span class="sxs-lookup"><span data-stu-id="d20bb-121">This beginning lesson assumes that you have finished the [Hello World](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="list-collectionarrays-and-collectionsmd"></a>[<span data-ttu-id="d20bb-122">List 集合</span><span class="sxs-lookup"><span data-stu-id="d20bb-122">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="d20bb-123">[List 集合](arrays-and-collections.md)課程會為您說明可儲存資料序列的「List 集合」類型。</span><span class="sxs-lookup"><span data-stu-id="d20bb-123">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="d20bb-124">您將會學習如何新增及移除項目、搜尋項目，以及對清單進行排序。</span><span class="sxs-lookup"><span data-stu-id="d20bb-124">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="d20bb-125">您會探索各種不同的清單。</span><span class="sxs-lookup"><span data-stu-id="d20bb-125">You'll explore different kinds of lists.</span></span> 

<span data-ttu-id="d20bb-126">此快速入門假設您已經完成上述快速入門。</span><span class="sxs-lookup"><span data-stu-id="d20bb-126">This beginning quickstart assumes that you have finished the quickstarts listed above.</span></span>

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[<span data-ttu-id="d20bb-127">類別簡介</span><span class="sxs-lookup"><span data-stu-id="d20bb-127">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="d20bb-128">這個最後的快速入門只能在您的電腦上執行，並使用您自己的本機開發環境和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d20bb-128">This final quickstart is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="d20bb-129">您會建置一個主控台應用程式，並了解 C# 語言的基本物件導向功能。</span><span class="sxs-lookup"><span data-stu-id="d20bb-129">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
