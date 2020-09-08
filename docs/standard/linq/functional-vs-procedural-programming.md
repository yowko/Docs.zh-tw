---
title: 功能性與程式性程式設計
description: LINQ to XML 支援功能結構和程式技術來建立 XML 應用程式。 功能結構是宣告式的方法。 程式技術支援 XML 樹狀結構的記憶體內部修改。
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552131"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a><span data-ttu-id="024f8-105">功能性與程式設計 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="024f8-105">Functional vs. procedural programming (LINQ to XML)</span></span>

<span data-ttu-id="024f8-106">XML 應用程式有很多種：</span><span class="sxs-lookup"><span data-stu-id="024f8-106">There are various types of XML applications:</span></span>

- <span data-ttu-id="024f8-107">有些應用程式會採用 XML 來源文件，然後以不同於來源文件的組織結構產生新的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="024f8-107">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>
- <span data-ttu-id="024f8-108">有些應用程式會採用 XML 來源文件，然後以完全不同的形式 (例如，HTML 或 CSV 文字檔)，產生結果文件。</span><span class="sxs-lookup"><span data-stu-id="024f8-108">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>
- <span data-ttu-id="024f8-109">有些應用程式會採用 XML 來源文件，然後將記錄插入到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="024f8-109">Some applications take source XML documents, and insert records into a database.</span></span>
- <span data-ttu-id="024f8-110">有些應用程式會從其他來源 (例如，資料庫) 取得資料，然後從其中建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="024f8-110">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>

<span data-ttu-id="024f8-111">這些都不是 XML 應用程式的所有類型，但這些都是 XML 程式設計人員必須執行的一組具代表性的功能。</span><span class="sxs-lookup"><span data-stu-id="024f8-111">These aren't all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>

<span data-ttu-id="024f8-112">利用所有這些應用程式類型，開發人員可以採用兩種明顯不同的方法：</span><span class="sxs-lookup"><span data-stu-id="024f8-112">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>

- <span data-ttu-id="024f8-113">使用宣告式方法的功能結構。</span><span class="sxs-lookup"><span data-stu-id="024f8-113">Functional construction using a declarative approach.</span></span>
- <span data-ttu-id="024f8-114">使用程序性程式碼進行記憶體中 XML 樹狀結構修改。</span><span class="sxs-lookup"><span data-stu-id="024f8-114">In-memory XML tree modification using procedural code.</span></span>

<span data-ttu-id="024f8-115">LINQ to XML 同時支援這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="024f8-115">LINQ to XML supports both approaches.</span></span>

<span data-ttu-id="024f8-116">使用功能性方法時，您可以撰寫採用來源文件的轉換，然後利用所需的組織結構產生全新的結果文件。</span><span class="sxs-lookup"><span data-stu-id="024f8-116">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>

<span data-ttu-id="024f8-117">就地修改 XML 樹狀結構時，您可以撰寫可在記憶體中 XML 樹狀結構內周遊與導覽程式碼的程式碼，藉以在必要時插入、刪除與修改程式碼。</span><span class="sxs-lookup"><span data-stu-id="024f8-117">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>

<span data-ttu-id="024f8-118">您可以搭配任一種方法使用 LINQ to XML。</span><span class="sxs-lookup"><span data-stu-id="024f8-118">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="024f8-119">您可以使用相同的類別，在某些情況下，也可以使用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="024f8-119">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="024f8-120">不過，這兩種方法的結構和目標並不相同。</span><span class="sxs-lookup"><span data-stu-id="024f8-120">However, the structure and goals of the two approaches are different.</span></span> <span data-ttu-id="024f8-121">例如，在不同的情況下，其中一種方法的效能通常會比較好，而且或多或少會使用到記憶體。</span><span class="sxs-lookup"><span data-stu-id="024f8-121">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="024f8-122">此外，其中一種方法會比較容易撰寫，並產生較容易維護的程式碼。</span><span class="sxs-lookup"><span data-stu-id="024f8-122">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>

<span data-ttu-id="024f8-123">若要查看這兩種方法的對比，請參閱 [記憶體中的 XML 樹狀結構修改與功能結構](in-memory-xml-tree-modification-vs-functional-construction.md)。</span><span class="sxs-lookup"><span data-stu-id="024f8-123">To see the two approaches contrasted, see [In-memory XML tree modification vs. functional construction](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

<span data-ttu-id="024f8-124">如需撰寫功能性轉換的教學課程，請參閱 [純功能性轉換簡介](introduction-pure-functional-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="024f8-124">For a tutorial on writing functional transformations, see [Introduction to pure functional transformations](introduction-pure-functional-transformations.md).</span></span>
