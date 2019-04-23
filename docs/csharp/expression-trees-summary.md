---
title: 運算式樹狀架構摘要
description: 概述如何使用運算式樹狀架構來建立動態程式，將程式碼解譯為資料，並建立以該程式碼為基礎的新功能。
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 99b9463df096d3aada19ed7995b04ef4bd41c179
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148625"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="1cb11-103">運算式樹狀架構摘要</span><span class="sxs-lookup"><span data-stu-id="1cb11-103">Expression Trees Summary</span></span>

[<span data-ttu-id="1cb11-104">上一個主題 -- 轉譯運算式</span><span class="sxs-lookup"><span data-stu-id="1cb11-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="1cb11-105">在本系列中，您已了解如何使用「運算式樹狀架構」來建立動態程式，將程式碼解譯為資料，並建立以該程式碼為基礎的新功能。</span><span class="sxs-lookup"><span data-stu-id="1cb11-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="1cb11-106">您可以查看運算式樹狀架構，以了解演算法的意圖。</span><span class="sxs-lookup"><span data-stu-id="1cb11-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="1cb11-107">不只是查看該程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cb11-107">You can not only examine that code.</span></span> <span data-ttu-id="1cb11-108">您可以建立表示原始程式碼修改版本的新運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="1cb11-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="1cb11-109">您也可以使用運算式樹狀架構來檢視演算法，並將該演算法轉譯至其他語言或環境。</span><span class="sxs-lookup"><span data-stu-id="1cb11-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="1cb11-110">限制</span><span class="sxs-lookup"><span data-stu-id="1cb11-110">Limitations</span></span>

<span data-ttu-id="1cb11-111">某些較新的 C# 語言項目無法正確轉譯為運算式樹狀架構。</span><span class="sxs-lookup"><span data-stu-id="1cb11-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="1cb11-112">運算式樹狀架構不能含有 `await` 運算式或 `async` Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="1cb11-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="1cb11-113">C# 6 版本中新增的許多功能，似乎與寫入運算式樹狀架構的功能不同。</span><span class="sxs-lookup"><span data-stu-id="1cb11-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="1cb11-114">相反地，較新的功能會以舊版的對等語法顯示於運算式樹狀架構中。</span><span class="sxs-lookup"><span data-stu-id="1cb11-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="1cb11-115">這可能不如您認為的是項限制。</span><span class="sxs-lookup"><span data-stu-id="1cb11-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="1cb11-116">事實上，這表示當引進新的語言功能時，解譯運算式樹狀架構的程式碼仍可能以相同方式運作。</span><span class="sxs-lookup"><span data-stu-id="1cb11-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="1cb11-117">即使有這些限制，運算式樹狀架構還是可讓您建立與解譯和修改程式碼 (以資料結構表示) 有關的動態演算法。</span><span class="sxs-lookup"><span data-stu-id="1cb11-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="1cb11-118">這是功能強大的工具，而且是 .NET 生態系統的其中一項功能，可讓 Entity Framework 等豐富的程式庫完成其功能。</span><span class="sxs-lookup"><span data-stu-id="1cb11-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
