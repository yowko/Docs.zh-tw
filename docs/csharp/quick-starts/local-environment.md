---
title: 本機環境教學課程 - C# 本機快速入門
description: 本快速入門提供於本機執行快速入門的基本概念
ms.date: 12/07/2017
ms.custom: mvc
ms.openlocfilehash: ad8405bf9d453bd2cc5fad8af4b7897654368a9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350149"
---
# <a name="local-environment"></a><span data-ttu-id="8f643-103">本機環境</span><span class="sxs-lookup"><span data-stu-id="8f643-103">Local environment</span></span>

<span data-ttu-id="8f643-104">嘗試於本機執行快速入門的第一個步驟，便是在本機電腦上設定開發環境。</span><span class="sxs-lookup"><span data-stu-id="8f643-104">The first step to trying a quickstart locally is to setup a development environment on your local machine.</span></span>
<span data-ttu-id="8f643-105">.NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="8f643-105">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

<span data-ttu-id="8f643-106">或者，您可以安裝 [.NET Core SDK](http://dot.net/core) \(英文\) 和 [Visual Studio Code](https://code.visualstudio.com/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="8f643-106">Alternatively, you can install the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span>

## <a name="basic-application-development-flow"></a><span data-ttu-id="8f643-107">基本應用程式開發流程</span><span class="sxs-lookup"><span data-stu-id="8f643-107">Basic application development flow</span></span>

<span data-ttu-id="8f643-108">您會使用 [`dotnet new`](../../core/tools/dotnet-new.md) 命令建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="8f643-108">You'll create applications using the [`dotnet new`](../../core/tools/dotnet-new.md) command.</span></span> <span data-ttu-id="8f643-109">此命令會產生應用程式所需的檔案和資產。</span><span class="sxs-lookup"><span data-stu-id="8f643-109">This command generates the files and assets necessary for your application.</span></span> <span data-ttu-id="8f643-110">快速入門全都會使用 `console` 應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="8f643-110">The quickstarts all use the `console` application type.</span></span>

<span data-ttu-id="8f643-111">其他會用到的命令為用來建置可執行檔的 [`dotnet build`](../../core/tools/dotnet-build.md)，以及用來執行可執行檔的 [`dotnet run`](../../core/tools/dotnet-run.md)。</span><span class="sxs-lookup"><span data-stu-id="8f643-111">The other commands you'll use are [`dotnet build`](../../core/tools/dotnet-build.md) to build the executable, and [`dotnet run`](../../core/tools/dotnet-run.md) to run the executable.</span></span>

## <a name="pick-your-quickstart"></a><span data-ttu-id="8f643-112">挑選快速入門</span><span class="sxs-lookup"><span data-stu-id="8f643-112">Pick your quickstart</span></span>

<span data-ttu-id="8f643-113">您可以從下列任何一個快速入門開始：</span><span class="sxs-lookup"><span data-stu-id="8f643-113">You can start with any of the following quickstarts:</span></span>

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[<span data-ttu-id="8f643-114">C# 中的數字</span><span class="sxs-lookup"><span data-stu-id="8f643-114">Numbers in C#</span></span>](numbers-in-csharp-local.md)

<span data-ttu-id="8f643-115">在 [C# 中的數字](numbers-in-csharp-local.md)快速入門中，您將會學習電腦儲存數字的方式，以及如何使用不同的數值型別來執行計算。</span><span class="sxs-lookup"><span data-stu-id="8f643-115">In the [Numbers in C#](numbers-in-csharp-local.md) quickstart, you'll learn how computers store numbers and how to perform calculations with different numeric types.</span></span> <span data-ttu-id="8f643-116">您將會學習進位的基本概念，以及如何使用 C# 執行數學計算。</span><span class="sxs-lookup"><span data-stu-id="8f643-116">You'll learn the basics of rounding, and how to perform mathematical calculations using C#.</span></span> 

<span data-ttu-id="8f643-117">本快速入門假設您已完成 [Hello World](hello-world.yml) 課程。</span><span class="sxs-lookup"><span data-stu-id="8f643-117">This quickstart assumes that you have finished the [Hello world](hello-world.yml) lesson.</span></span>

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[<span data-ttu-id="8f643-118">分支和迴圈</span><span class="sxs-lookup"><span data-stu-id="8f643-118">Branches and loops</span></span>](branches-and-loops-local.md)

<span data-ttu-id="8f643-119">[分支和迴圈](branches-and-loops-local.md)快速入門會指導您如何根據儲存在變數中的值，以選取不同程式碼執行路徑的基本概念。</span><span class="sxs-lookup"><span data-stu-id="8f643-119">The [Branches and loops](branches-and-loops-local.md) quickstart teaches the basics of selecting different paths of code execution based on the values stored in variables.</span></span> <span data-ttu-id="8f643-120">您將會學習控制流程的基本概念，也就是程式做出決定並選擇不同動作的基礎機制。</span><span class="sxs-lookup"><span data-stu-id="8f643-120">You'll learn the basics of control flow, which is the basis of how programs make decisions and choose different actions.</span></span> 

<span data-ttu-id="8f643-121">本快速入門假設您已完成 [Hello World](hello-world.yml) 和 [C# 中的數字](numbers-in-csharp-local.md)課程。</span><span class="sxs-lookup"><span data-stu-id="8f643-121">This quickstart assumes that you have finished the [Hello world](hello-world.yml) and [Numbers in C#](numbers-in-csharp-local.md) lessons.</span></span>

## <a name="string-interpolationinterpolated-strings-localmd"></a>[<span data-ttu-id="8f643-122">字串內插補點</span><span class="sxs-lookup"><span data-stu-id="8f643-122">String interpolation</span></span>](interpolated-strings-local.md)

<span data-ttu-id="8f643-123">[字串內插補點](interpolated-strings-local.md)快速入門示範如何在字串中插入值。</span><span class="sxs-lookup"><span data-stu-id="8f643-123">The [String interpolation](interpolated-strings-local.md) quickstart shows you how to insert values into a string.</span></span> <span data-ttu-id="8f643-124">您會學到如何使用內嵌 C# 運算式建立插入字串，以及如何控制結果字串中運算式結果的文字外觀。</span><span class="sxs-lookup"><span data-stu-id="8f643-124">You'll learn how to create an interpolated string with embedded C# expressions and how to control the text appearance of the expression results in the result string.</span></span>

<span data-ttu-id="8f643-125">本快速入門假設您已完成 [Hello World](hello-world.yml)、[C# 中的數字](numbers-in-csharp-local.md)和[分支和迴圈](branches-and-loops-local.md)課程。</span><span class="sxs-lookup"><span data-stu-id="8f643-125">This quickstart assumes that you have finished the [Hello world](hello-world.yml), [Numbers in C#](numbers-in-csharp-local.md), and [Branches and loops](branches-and-loops-local.md) lessons.</span></span>

## <a name="list-collectionarrays-and-collectionsmd"></a>[<span data-ttu-id="8f643-126">List 集合</span><span class="sxs-lookup"><span data-stu-id="8f643-126">List collection</span></span>](arrays-and-collections.md)

<span data-ttu-id="8f643-127">[List 集合](arrays-and-collections.md)課程會為您說明可儲存資料序列的「List 集合」類型。</span><span class="sxs-lookup"><span data-stu-id="8f643-127">The [List collection](arrays-and-collections.md) lesson gives you a tour of the List collection type that stores sequences of data.</span></span> <span data-ttu-id="8f643-128">您將會學習如何新增及移除項目、搜尋項目，以及對清單進行排序。</span><span class="sxs-lookup"><span data-stu-id="8f643-128">You'll learn how to add and remove items, search for items, and sort the lists.</span></span> <span data-ttu-id="8f643-129">您會探索各種不同的清單。</span><span class="sxs-lookup"><span data-stu-id="8f643-129">You'll explore different kinds of lists.</span></span> 

<span data-ttu-id="8f643-130">本快速入門假設您已完成上述的課程。</span><span class="sxs-lookup"><span data-stu-id="8f643-130">This quickstart assumes that you have finished the lessons listed above.</span></span>

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[<span data-ttu-id="8f643-131">類別簡介</span><span class="sxs-lookup"><span data-stu-id="8f643-131">Introduction to classes</span></span>](introduction-to-classes.md)

<span data-ttu-id="8f643-132">這個最後的快速入門只能在您的電腦上執行，並使用您自己的本機開發環境和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="8f643-132">This final quickstart is only available to run on your machine, using your own local development environment and .NET Core.</span></span>
<span data-ttu-id="8f643-133">您會建置一個主控台應用程式，並了解 C# 語言的基本物件導向功能。</span><span class="sxs-lookup"><span data-stu-id="8f643-133">You'll build a console application and see the basic object-oriented features that are part of the C# language.</span></span>
