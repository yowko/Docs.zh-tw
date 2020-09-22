---
title: 衍生的數學函式
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: f84b1ef18ef2a924bb2e47da85ecbb51f982873a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869018"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="90093-102">衍生的數學函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90093-102">Derived Math Functions (Visual Basic)</span></span>

<span data-ttu-id="90093-103">下表顯示的非內建數學函數，可以衍生自物件的內建數學函數 <xref:System.Math?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="90093-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="90093-104">您可以藉由加入至您的檔案 `Imports System.Math` 或專案來存取內建數學函數。</span><span class="sxs-lookup"><span data-stu-id="90093-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="90093-105">函式</span><span class="sxs-lookup"><span data-stu-id="90093-105">Function</span></span>|<span data-ttu-id="90093-106">衍生的對應專案</span><span class="sxs-lookup"><span data-stu-id="90093-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="90093-107">正割 (Sec (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-107">Secant (Sec(x))</span></span>|<span data-ttu-id="90093-108">1/Cos (x) </span><span class="sxs-lookup"><span data-stu-id="90093-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="90093-109"> (Csc (x) # A3 的余割</span><span class="sxs-lookup"><span data-stu-id="90093-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="90093-110">1/Sin (x) </span><span class="sxs-lookup"><span data-stu-id="90093-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="90093-111">餘切 (Ctan (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="90093-112">1/Tan (x) </span><span class="sxs-lookup"><span data-stu-id="90093-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="90093-113">反向正弦 (Asin (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="90093-114">Atan (x/Sqrt (-x \* x + 1) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="90093-115">反向余弦 (Acos (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="90093-116">Atan (-x/Sqrt (-x \* x + 1) # A3 + 2 \* Atan (1) </span><span class="sxs-lookup"><span data-stu-id="90093-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="90093-117">反向正向 (Asec (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="90093-118">2 \* Atan (1) – Atan (Sign (x) /Sqrt (x \* x – 1) # A7</span><span class="sxs-lookup"><span data-stu-id="90093-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="90093-119">反向余割 (Acsc (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="90093-120">Atan (Sign (x) /Sqrt (x \* x – 1) # A5</span><span class="sxs-lookup"><span data-stu-id="90093-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="90093-121">反向餘切 (Acot (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="90093-122">2 \* Atan (1) -Atan (x) </span><span class="sxs-lookup"><span data-stu-id="90093-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="90093-123">雙曲正弦 (Sinh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="90093-124"> (Exp (x) – Exp (-x) # A5/2</span><span class="sxs-lookup"><span data-stu-id="90093-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="90093-125">雙曲余弦 (Cosh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="90093-126"> (Exp (x) + Exp (-x) # A5/2</span><span class="sxs-lookup"><span data-stu-id="90093-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="90093-127">雙曲正切函數 (Tanh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="90093-128"> (Exp (x) – Exp (-x) # A5/ (Exp (x) + Exp (-x) # A11</span><span class="sxs-lookup"><span data-stu-id="90093-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="90093-129">雙曲正割 (Sech (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="90093-130">2/ (Exp (x) + Exp (-x) # A5</span><span class="sxs-lookup"><span data-stu-id="90093-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="90093-131">雙曲余割 (Csch (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="90093-132">2/ (Exp (x) – Exp (-x) # A5</span><span class="sxs-lookup"><span data-stu-id="90093-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="90093-133">雙曲餘切 (Coth (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="90093-134"> (Exp (x) + Exp (-x) # A5/ (Exp (x) – Exp (-x) # A11</span><span class="sxs-lookup"><span data-stu-id="90093-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="90093-135">反向雙曲正弦 (Asinh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="90093-136">Log (x + Sqrt (x \* x + 1) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="90093-137">反向雙曲余弦 (Acosh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="90093-138">Log (x + Sqrt (x \* x – 1) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="90093-139">反向雙曲正切函數 (Atanh (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="90093-140">Log ( # B1 1 + x) / (1 – x) # A5/2</span><span class="sxs-lookup"><span data-stu-id="90093-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="90093-141">反向雙曲正割 (AsecH (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="90093-142">Log ( # B1 Sqrt (-x \* x + 1) + 1) /x) </span><span class="sxs-lookup"><span data-stu-id="90093-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="90093-143">反向雙曲余割 (Acsch (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="90093-144">Log ( # B1 Sign (x) \* Sqrt (x \* x + 1) + 1) /x) </span><span class="sxs-lookup"><span data-stu-id="90093-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="90093-145">反向雙曲餘切 (Acoth (x) # A3</span><span class="sxs-lookup"><span data-stu-id="90093-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="90093-146">Log ( # B1 x + 1) / (x – 1) # A5/2</span><span class="sxs-lookup"><span data-stu-id="90093-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90093-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90093-147">See also</span></span>

- [<span data-ttu-id="90093-148">數學函式</span><span class="sxs-lookup"><span data-stu-id="90093-148">Math Functions</span></span>](../functions/math-functions.md)
