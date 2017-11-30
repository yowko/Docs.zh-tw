---
title: "這 &#39; 第一個陳述式新的子 &#39;必須呼叫 &#39;MyBase.New &#39;或 &#39;MyClass.New &#39;（沒有可存取建構函式不含參數）"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords: BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1065643e1f6c868092fbad839af0dbbd33afaf01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="c8192-102">這 &#39; 第一個陳述式新的子 &#39;必須呼叫 &#39;MyBase.New &#39;或 &#39;MyClass.New &#39;（沒有可存取建構函式不含參數）</span><span class="sxs-lookup"><span data-stu-id="c8192-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="c8192-103">這個 'Sub New' 的第一個陳述式必須呼叫 'MyBase.New' 或 'MyClass.New'，因為基底類別\<basename >' 的'\<derivedname >' 沒有可存取 ' Sub New' 可呼叫沒有引數。</span><span class="sxs-lookup"><span data-stu-id="c8192-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="c8192-104">在衍生類別中，每個建構函式必須呼叫基底類別建構函式 (`MyBase.New`)。</span><span class="sxs-lookup"><span data-stu-id="c8192-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="c8192-105">如果基底類別的建構函式不含任何參數是在衍生類別，可存取`MyBase.New`可以自動呼叫。</span><span class="sxs-lookup"><span data-stu-id="c8192-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="c8192-106">如果不是，呼叫基底類別建構函式必須有參數，並無法自動完成。</span><span class="sxs-lookup"><span data-stu-id="c8192-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="c8192-107">在此情況下，每個衍生的類別建構函式的第一個陳述式必須呼叫基底類別中，參數化建構函式或呼叫其他建構函式呼叫的基底類別建構函式可讓衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="c8192-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="c8192-108">**錯誤 ID:** BC30148</span><span class="sxs-lookup"><span data-stu-id="c8192-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8192-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c8192-109">To correct this error</span></span>  
  
-   <span data-ttu-id="c8192-110">呼叫`MyBase.New`提供必要的參數，或呼叫這類呼叫的對等建構函式。</span><span class="sxs-lookup"><span data-stu-id="c8192-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="c8192-111">例如，如果基底類別建構函式宣告為`Public Sub New(ByVal index as Integer)`、 第一個陳述式在衍生類別建構函式可能`MyBase.New(100)`。</span><span class="sxs-lookup"><span data-stu-id="c8192-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8192-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8192-112">See Also</span></span>  
 [<span data-ttu-id="c8192-113">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="c8192-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
