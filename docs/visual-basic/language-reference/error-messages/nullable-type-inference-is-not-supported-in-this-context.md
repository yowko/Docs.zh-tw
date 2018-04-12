---
title: 在此內容中不支援可為 Null 的類型推斷
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7a5450d812260d3916296dff56abee27b3d586c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="184f3-102">在此內容中不支援可為 Null 的類型推斷</span><span class="sxs-lookup"><span data-stu-id="184f3-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="184f3-103">實值類型和結構可以宣告為可為 null。</span><span class="sxs-lookup"><span data-stu-id="184f3-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="184f3-104">不過，您無法使用可為 null 的宣告型別推斷結合。</span><span class="sxs-lookup"><span data-stu-id="184f3-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="184f3-105">下列範例會造成這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="184f3-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="184f3-106">**錯誤 ID:** BC36629</span><span class="sxs-lookup"><span data-stu-id="184f3-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="184f3-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="184f3-107">To correct this error</span></span>  
  
-   <span data-ttu-id="184f3-108">使用`As`子句來宣告為可為 null 的變數。</span><span class="sxs-lookup"><span data-stu-id="184f3-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184f3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="184f3-109">See Also</span></span>  
 [<span data-ttu-id="184f3-110">可為 Null 的值類型</span><span class="sxs-lookup"><span data-stu-id="184f3-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="184f3-111">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="184f3-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
