---
title: "Boolean 資料類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f7376b-4b11-4b35-98a9-780382053ceb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3a11b4dfde2afcf738f125a1fd7324ceff74669
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="boolean-data-types"></a><span data-ttu-id="de17c-102">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="de17c-102">Boolean Data Types</span></span>
<span data-ttu-id="de17c-103">除了不會轉譯最少運算行為以外，在 Common Language Runtime (CLR) 中布林運算子會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="de17c-103">Boolean operators work as expected in the common language runtime (CLR), except that short-circuiting behavior is not translated.</span></span> <span data-ttu-id="de17c-104">例如，Visual Basic `AndAlso` 運算子的行為方式如同 `And` 運算子。</span><span class="sxs-lookup"><span data-stu-id="de17c-104">For example, the Visual Basic `AndAlso` operator behaves like the `And` operator.</span></span> <span data-ttu-id="de17c-105">而 C# `&&` 運算子的行為方式則如同 `&` 運算子。</span><span class="sxs-lookup"><span data-stu-id="de17c-105">The C# `&&` operator behaves like the `&` operator.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="de17c-106"> 支援下列運算子。</span><span class="sxs-lookup"><span data-stu-id="de17c-106"> supports the following operators.</span></span>  
  
|<span data-ttu-id="de17c-107">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de17c-107">Visual Basic</span></span>|<span data-ttu-id="de17c-108">C#</span><span class="sxs-lookup"><span data-stu-id="de17c-108">C#</span></span>|  
|------------------|---------|  
|[<span data-ttu-id="de17c-109">And 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-109">And Operator</span></span>](~/docs/visual-basic/language-reference/operators/and-operator.md)|[<span data-ttu-id="de17c-110">& 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-110">& Operator</span></span>](~/docs/csharp/language-reference/operators/and-operator.md)|  
|[<span data-ttu-id="de17c-111">AndAlso 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-111">AndAlso Operator</span></span>](~/docs/visual-basic/language-reference/operators/andalso-operator.md)|[<span data-ttu-id="de17c-112">&& 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-112">&& Operator</span></span>](~/docs/csharp/language-reference/operators/conditional-and-operator.md)|  
|[<span data-ttu-id="de17c-113">Or 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-113">Or Operator</span></span>](~/docs/visual-basic/language-reference/operators/or-operator.md)|[<span data-ttu-id="de17c-114">&#124; Operator</span><span class="sxs-lookup"><span data-stu-id="de17c-114">&#124; Operator</span></span>](~/docs/csharp/language-reference/operators/or-operator.md)|  
|[<span data-ttu-id="de17c-115">OrElse 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-115">OrElse Operator</span></span>](~/docs/visual-basic/language-reference/operators/orelse-operator.md)|[<span data-ttu-id="de17c-116">&#124;&#124; Operator</span><span class="sxs-lookup"><span data-stu-id="de17c-116">&#124;&#124; Operator</span></span>](~/docs/csharp/language-reference/operators/conditional-or-operator.md)|  
|[<span data-ttu-id="de17c-117">Xor 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-117">Xor Operator</span></span>](~/docs/visual-basic/language-reference/operators/xor-operator.md)|[<span data-ttu-id="de17c-118">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-118">^ Operator</span></span>](~/docs/csharp/language-reference/operators/xor-operator.md)|  
|[<span data-ttu-id="de17c-119">Not 運算子</span><span class="sxs-lookup"><span data-stu-id="de17c-119">Not Operator</span></span>](~/docs/visual-basic/language-reference/operators/not-operator.md)|[!運算子]<span data-ttu-id="de17c-120">(~/docs/csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="de17c-120">(~/docs/csharp/language-reference/operators/logical-negation-operator.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de17c-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="de17c-121">See Also</span></span>  
 [<span data-ttu-id="de17c-122">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="de17c-122">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
