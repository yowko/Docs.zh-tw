---
title: 在此內容中不支援可為 Null 的類型推斷
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409383"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="7eff2-102">在此內容中不支援可為 Null 的類型推斷</span><span class="sxs-lookup"><span data-stu-id="7eff2-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="7eff2-103">實數值型別和結構可以宣告為可為 null。</span><span class="sxs-lookup"><span data-stu-id="7eff2-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="7eff2-104">不過，您不能將可為 null 的宣告與型別推斷搭配使用。</span><span class="sxs-lookup"><span data-stu-id="7eff2-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="7eff2-105">下列範例會造成此錯誤。</span><span class="sxs-lookup"><span data-stu-id="7eff2-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="7eff2-106">**錯誤識別碼：** BC36629</span><span class="sxs-lookup"><span data-stu-id="7eff2-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7eff2-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7eff2-107">To correct this error</span></span>  
  
- <span data-ttu-id="7eff2-108">使用 `As` 子句，將變數宣告為可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="7eff2-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eff2-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eff2-109">See also</span></span>

- [<span data-ttu-id="7eff2-110">可為 null 的實數值型別</span><span class="sxs-lookup"><span data-stu-id="7eff2-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="7eff2-111">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="7eff2-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
