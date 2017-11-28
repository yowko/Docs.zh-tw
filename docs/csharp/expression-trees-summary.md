---
title: "運算式樹狀架構摘要"
description: "概述如何使用運算式樹狀架構來建立動態程式，將程式碼解譯為資料，並建立以該程式碼為基礎的新功能。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 8088ce0c138cdb05a6e4a4fb6467e43efd252ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees-summary"></a><span data-ttu-id="c1717-104">運算式樹狀架構摘要</span><span class="sxs-lookup"><span data-stu-id="c1717-104">Expression Trees Summary</span></span>

[<span data-ttu-id="c1717-105">上一個主題 -- 轉譯運算式</span><span class="sxs-lookup"><span data-stu-id="c1717-105">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="c1717-106">在本系列中，您已了解如何使用「運算式樹狀架構」來建立動態程式，將程式碼解譯為資料，並建立以該程式碼為基礎的新功能。</span><span class="sxs-lookup"><span data-stu-id="c1717-106">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="c1717-107">您可以查看運算式樹狀架構，以了解演算法的意圖。</span><span class="sxs-lookup"><span data-stu-id="c1717-107">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="c1717-108">不只是查看該程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1717-108">You can not only examine that code.</span></span> <span data-ttu-id="c1717-109">您可以建立表示原始程式碼修改版本的新運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c1717-109">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="c1717-110">您也可以使用運算式樹狀架構來檢視演算法，並將該演算法轉譯至其他語言或環境。</span><span class="sxs-lookup"><span data-stu-id="c1717-110">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="c1717-111">限制</span><span class="sxs-lookup"><span data-stu-id="c1717-111">Limitations</span></span>

<span data-ttu-id="c1717-112">某些較新的 C# 語言項目無法正確轉譯為運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="c1717-112">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="c1717-113">運算式樹狀架構不能含有 `await` 運算式或 `async` Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c1717-113">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="c1717-114">C# 6 版本中新增的許多功能，似乎與寫入運算式樹狀架構的功能不同。</span><span class="sxs-lookup"><span data-stu-id="c1717-114">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="c1717-115">相反地，較新的功能會以舊版的對等語法顯示於運算式樹狀架構中。</span><span class="sxs-lookup"><span data-stu-id="c1717-115">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="c1717-116">這可能不如您認為的是項限制。</span><span class="sxs-lookup"><span data-stu-id="c1717-116">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="c1717-117">事實上，這表示當引進新的語言功能時，解譯運算式樹狀架構的程式碼仍可能以相同方式運作。</span><span class="sxs-lookup"><span data-stu-id="c1717-117">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="c1717-118">即使有這些限制，運算式樹狀架構還是可讓您建立與解譯和修改程式碼 (以資料結構表示) 有關的動態演算法。</span><span class="sxs-lookup"><span data-stu-id="c1717-118">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represetned as a data structure.</span></span> <span data-ttu-id="c1717-119">這是功能強大的工具，而且是 .NET 生態系統的其中一項功能，可讓 Entity Framework 等豐富的程式庫完成其功能。</span><span class="sxs-lookup"><span data-stu-id="c1717-119">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>

