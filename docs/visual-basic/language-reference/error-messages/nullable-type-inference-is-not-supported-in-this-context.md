---
title: 在此內容中不支援可為 Null 的類型推斷
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249496"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="017a4-102">在此內容中不支援可為 Null 的類型推斷</span><span class="sxs-lookup"><span data-stu-id="017a4-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="017a4-103">數值型別和結構可以聲明為空。</span><span class="sxs-lookup"><span data-stu-id="017a4-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="017a4-104">但是，不能將可無效聲明與型別推斷結合使用。</span><span class="sxs-lookup"><span data-stu-id="017a4-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="017a4-105">以下示例導致此錯誤。</span><span class="sxs-lookup"><span data-stu-id="017a4-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="017a4-106">**錯誤 ID：** BC36629</span><span class="sxs-lookup"><span data-stu-id="017a4-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="017a4-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="017a4-107">To correct this error</span></span>  
  
- <span data-ttu-id="017a4-108">使用`As`子句將變數聲明為空數值型別。</span><span class="sxs-lookup"><span data-stu-id="017a4-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017a4-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="017a4-109">See also</span></span>

- [<span data-ttu-id="017a4-110">空數值型別</span><span class="sxs-lookup"><span data-stu-id="017a4-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="017a4-111">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="017a4-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
