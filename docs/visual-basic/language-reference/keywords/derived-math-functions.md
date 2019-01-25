---
title: 衍生的數學函式 (Visual Basic)
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
ms.openlocfilehash: 1273871faf65afdd1a894c03f13a2c93507c1b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505857"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="168d9-102">衍生的數學函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="168d9-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="168d9-103">下表顯示可以衍生自的內建數學函式的非內建的數學函式<xref:System.Math?displayProperty=nameWithType>物件。</span><span class="sxs-lookup"><span data-stu-id="168d9-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="168d9-104">您可以存取內建數學函式，藉由新增`Imports System.Math`至您的檔案或專案。</span><span class="sxs-lookup"><span data-stu-id="168d9-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="168d9-105">功能</span><span class="sxs-lookup"><span data-stu-id="168d9-105">Function</span></span>|<span data-ttu-id="168d9-106">衍生對等項目</span><span class="sxs-lookup"><span data-stu-id="168d9-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="168d9-107">正割 (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-107">Secant (Sec(x))</span></span>|<span data-ttu-id="168d9-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="168d9-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="168d9-109">餘割 (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="168d9-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="168d9-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="168d9-111">餘切值 (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="168d9-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="168d9-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="168d9-113">反正弦 (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="168d9-114">Atan (x / Sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="168d9-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="168d9-115">反餘弦 (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="168d9-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="168d9-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="168d9-117">反向的正割 (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="168d9-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="168d9-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="168d9-119">反餘割 (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="168d9-120">Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="168d9-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="168d9-121">反餘切 (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="168d9-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="168d9-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="168d9-123">雙曲正弦值 (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="168d9-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="168d9-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="168d9-125">雙曲餘弦值 (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="168d9-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="168d9-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="168d9-127">雙曲正切 (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="168d9-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="168d9-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="168d9-129">雙曲正割 (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="168d9-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="168d9-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="168d9-131">雙曲餘割 (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="168d9-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="168d9-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="168d9-133">雙曲餘切值 (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="168d9-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="168d9-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="168d9-135">反雙曲正弦 (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="168d9-136">記錄檔 (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="168d9-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="168d9-137">反雙曲餘弦 (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="168d9-138">記錄檔 (x + Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="168d9-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="168d9-139">反雙曲正切 (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="168d9-140">記錄 ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="168d9-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="168d9-141">數值的反雙曲正割 (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="168d9-142">Log ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="168d9-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="168d9-143">數值的反雙曲餘割 (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="168d9-144">Log((Sign(x) \* Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="168d9-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="168d9-145">數值的反雙曲餘切值 (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="168d9-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="168d9-146">記錄 ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="168d9-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="168d9-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="168d9-147">See also</span></span>
- [<span data-ttu-id="168d9-148">數學函式</span><span class="sxs-lookup"><span data-stu-id="168d9-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
