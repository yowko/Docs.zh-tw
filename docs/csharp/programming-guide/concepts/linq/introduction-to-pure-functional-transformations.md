---
title: 純函數式轉換簡介 (C#)
description: '瞭解功能性轉換，包括 c # 中的基礎概念和語言結構。 這些資源會使用 XML 轉換來取得範例。'
ms.date: 07/20/2015
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
ms.openlocfilehash: 17f9dcb072b5f67521f668b1802d12a455f383fa
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165679"
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="70925-104">純函數式轉換簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="70925-104">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="70925-105">本節說明功能性轉換，包括基礎的概念與支援的語言建構。</span><span class="sxs-lookup"><span data-stu-id="70925-105">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="70925-106">其中包含程式設計的物件導向與功能性轉換方法，包括如何轉換到後者的建議。</span><span class="sxs-lookup"><span data-stu-id="70925-106">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="70925-107">雖然在許多程式設計案例中都可以使用功能性轉換，但是此處使用 XML 轉換做為具體範例。</span><span class="sxs-lookup"><span data-stu-id="70925-107">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
 <span data-ttu-id="70925-108">[教學課程：管理 WordprocessingML 文件中的內容 (C#)](./shape-of-wordprocessingml-documents.md) 教學課程提供一系列的範例，每個範例都是根據前一個範例所建置。</span><span class="sxs-lookup"><span data-stu-id="70925-108">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="70925-109">這些範例會示範純功能性轉換方法以管理 XML。</span><span class="sxs-lookup"><span data-stu-id="70925-109">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span> <span data-ttu-id="70925-110">本教學課程假設您具備 C# 的使用知識。</span><span class="sxs-lookup"><span data-stu-id="70925-110">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="70925-111">在此教學課程中不會提供語言建構的詳細語意，但是會適當地提供語言文件的連結。</span><span class="sxs-lookup"><span data-stu-id="70925-111">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="70925-112">同時也假設具備資訊科學基本概念與 XML (包括 XML 命名空間) 的實用知識。</span><span class="sxs-lookup"><span data-stu-id="70925-112">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70925-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="70925-113">In This Section</span></span>  
  
|<span data-ttu-id="70925-114">主題</span><span class="sxs-lookup"><span data-stu-id="70925-114">Topic</span></span>|<span data-ttu-id="70925-115">描述</span><span class="sxs-lookup"><span data-stu-id="70925-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="70925-116">概念和術語 (函數式轉換) (C#)</span><span class="sxs-lookup"><span data-stu-id="70925-116">Concepts and Terminology (Functional Transformation) (C#)</span></span>](./concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="70925-117">說明純功能性轉換的概念與術語。</span><span class="sxs-lookup"><span data-stu-id="70925-117">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="70925-118">功能程式設計與命令式程式設計的比較（c #）</span><span class="sxs-lookup"><span data-stu-id="70925-118">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)|<span data-ttu-id="70925-119">比較與對照功能性程式設計與更傳統的命令性 (程序性) 程式設計。</span><span class="sxs-lookup"><span data-stu-id="70925-119">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="70925-120">重構為純虛擬函式 (C#)</span><span class="sxs-lookup"><span data-stu-id="70925-120">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)|<span data-ttu-id="70925-121">說明純虛擬函式，並顯示純虛擬函式與非純虛擬函式的範例。</span><span class="sxs-lookup"><span data-stu-id="70925-121">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="70925-122">功能性轉換的適用性 (C#)</span><span class="sxs-lookup"><span data-stu-id="70925-122">Applicability of Functional Transformation (C#)</span></span>](./applicability-of-functional-transformation.md)|<span data-ttu-id="70925-123">描述功能性轉換的典型案例。</span><span class="sxs-lookup"><span data-stu-id="70925-123">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="70925-124">XML 函數式轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70925-124">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="70925-125">描述轉換 XML 樹狀內容中的功能性轉換。</span><span class="sxs-lookup"><span data-stu-id="70925-125">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  