---
title: Visual Basic 中的控制流程
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control flow [Visual Basic]
- control structures [Visual Basic]
- structures [Visual Basic], control
- conditional statements [Visual Basic], control flow
ms.assetid: 5623ef47-52b1-4202-befd-9af36422ec6f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce0cb7cba8f05b488d47f99da51b0b5de75eb15
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="control-flow-in-visual-basic"></a><span data-ttu-id="a268b-102">Visual Basic 中的控制流程</span><span class="sxs-lookup"><span data-stu-id="a268b-102">Control Flow in Visual Basic</span></span>
<span data-ttu-id="a268b-103">如果處於不受控制的狀態，則程式會從頭到尾執行其陳述式。</span><span class="sxs-lookup"><span data-stu-id="a268b-103">Left unregulated, a program proceeds through its statements from beginning to end.</span></span> <span data-ttu-id="a268b-104">只要使用這種單向流程，就可以撰寫一些極簡單的程式。</span><span class="sxs-lookup"><span data-stu-id="a268b-104">Some very simple programs can be written with only this unidirectional flow.</span></span> <span data-ttu-id="a268b-105">不過，任何程式設計語言的大部分功能和效用都是來自於它們能夠使用控制陳述式和迴圈來變更執行順序。</span><span class="sxs-lookup"><span data-stu-id="a268b-105">However, much of the power and utility of any programming language comes from the ability to change execution order with control statements and loops.</span></span>  
  
 <span data-ttu-id="a268b-106">控制結構可讓您規範程式的執行流程。</span><span class="sxs-lookup"><span data-stu-id="a268b-106">Control structures allow you to regulate the flow of your program's execution.</span></span> <span data-ttu-id="a268b-107">使用控制結構，您可以撰寫用於進行決策或重複動作的 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a268b-107">Using control structures, you can write [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code that makes decisions or that repeats actions.</span></span> <span data-ttu-id="a268b-108">其他控制結構可讓您確保資源的處置，或在相同的物件參考上執行一系列的陳述式。</span><span class="sxs-lookup"><span data-stu-id="a268b-108">Other control structures let you guarantee disposal of a resource or run a series of statements on the same object reference.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a268b-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="a268b-109">In This Section</span></span>  
 [<span data-ttu-id="a268b-110">決策結構</span><span class="sxs-lookup"><span data-stu-id="a268b-110">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 <span data-ttu-id="a268b-111">描述用於分支的控制結構。</span><span class="sxs-lookup"><span data-stu-id="a268b-111">Describes control structures used for branching.</span></span>  
  
 [<span data-ttu-id="a268b-112">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="a268b-112">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 <span data-ttu-id="a268b-113">討論用來重複程序的控制結構。</span><span class="sxs-lookup"><span data-stu-id="a268b-113">Discusses control structures used to repeat processes.</span></span>  
  
 [<span data-ttu-id="a268b-114">其他控制結構</span><span class="sxs-lookup"><span data-stu-id="a268b-114">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 <span data-ttu-id="a268b-115">描述用於資源處置和物件存取的控制結構。</span><span class="sxs-lookup"><span data-stu-id="a268b-115">Describes control structures used for resource disposal and object access.</span></span>  
  
 [<span data-ttu-id="a268b-116">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="a268b-116">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 <span data-ttu-id="a268b-117">將控制結構涵蓋在其他控制結構內。</span><span class="sxs-lookup"><span data-stu-id="a268b-117">Covers control structures inside other control structures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a268b-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="a268b-118">Related Sections</span></span>  
 [<span data-ttu-id="a268b-119">控制流程摘要</span><span class="sxs-lookup"><span data-stu-id="a268b-119">Control Flow Summary</span></span>](../../../../visual-basic/language-reference/keywords/control-flow-summary.md)  
 <span data-ttu-id="a268b-120">提供此主題上語言參考頁面的連結。</span><span class="sxs-lookup"><span data-stu-id="a268b-120">Provides links to language reference pages on this subject.</span></span>
