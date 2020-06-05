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
ms.openlocfilehash: 611f3d8faf2148b8a983467d9ace4fd6c18b30e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373876"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="0e16c-102">衍生的數學函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e16c-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="0e16c-103">下表顯示的非內建數學函數，可以衍生自物件的內建數學函式 <xref:System.Math?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0e16c-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="0e16c-104">您可以藉由將加入至您的檔案或專案，來存取內建的數學函數 `Imports System.Math` 。</span><span class="sxs-lookup"><span data-stu-id="0e16c-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="0e16c-105">函式</span><span class="sxs-lookup"><span data-stu-id="0e16c-105">Function</span></span>|<span data-ttu-id="0e16c-106">衍生的對等專案</span><span class="sxs-lookup"><span data-stu-id="0e16c-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="0e16c-107">正割（秒（x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-107">Secant (Sec(x))</span></span>|<span data-ttu-id="0e16c-108">1/Cos （x）</span><span class="sxs-lookup"><span data-stu-id="0e16c-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="0e16c-109">余割（Csc （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="0e16c-110">1/Sin （x）</span><span class="sxs-lookup"><span data-stu-id="0e16c-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="0e16c-111">餘切（Ctan （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="0e16c-112">1/Tan （x）</span><span class="sxs-lookup"><span data-stu-id="0e16c-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="0e16c-113">反正弦函數（Asin （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="0e16c-114">Atan （x/Sqrt （-x \* x + 1））</span><span class="sxs-lookup"><span data-stu-id="0e16c-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="0e16c-115">反余弦函數（Acos （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="0e16c-116">Atan （-x/Sqrt （-x \* x + 1）） + 2 \* Atan （1）</span><span class="sxs-lookup"><span data-stu-id="0e16c-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="0e16c-117">反正割（Asec （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="0e16c-118">2 \* Atan （1）– Atan （Sign （x）/Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="0e16c-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="0e16c-119">反向余割（Acsc （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="0e16c-120">Atan （Sign （x）/Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="0e16c-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="0e16c-121">反向餘切（Acot （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="0e16c-122">2 \* Atan （1）-Atan （x）</span><span class="sxs-lookup"><span data-stu-id="0e16c-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="0e16c-123">雙曲正弦（Sinh （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="0e16c-124">（Exp （x）– Exp （-x））/2</span><span class="sxs-lookup"><span data-stu-id="0e16c-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="0e16c-125">雙曲余弦（Cosh （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="0e16c-126">（Exp （x） + Exp （-x））/2</span><span class="sxs-lookup"><span data-stu-id="0e16c-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="0e16c-127">雙曲正切函數（Tanh （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="0e16c-128">（Exp （x）– Exp （-x））/（Exp （x） + Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="0e16c-129">雙曲正割（Sech （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="0e16c-130">2/（Exp （x） + Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="0e16c-131">雙曲余割（Csch （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="0e16c-132">2/（Exp （x）– Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="0e16c-133">雙曲餘切（Coth （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="0e16c-134">（Exp （x） + Exp （-x））/（Exp （x）– Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="0e16c-135">反雙曲正弦（Asinh （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="0e16c-136">Log （x + Sqrt （x \* x + 1））</span><span class="sxs-lookup"><span data-stu-id="0e16c-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="0e16c-137">反雙曲余弦（Acosh （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="0e16c-138">Log （x + Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="0e16c-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="0e16c-139">反雙曲正切（Atanh （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="0e16c-140">Log （（1 + x）/（1– x））/2</span><span class="sxs-lookup"><span data-stu-id="0e16c-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="0e16c-141">反雙曲正割（AsecH （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="0e16c-142">Log （（Sqrt （-x \* x + 1） + 1）/x）</span><span class="sxs-lookup"><span data-stu-id="0e16c-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="0e16c-143">反雙曲余割（Acsch （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="0e16c-144">Log （（符號（x） \* Sqrt （x \* x + 1） + 1）/x）</span><span class="sxs-lookup"><span data-stu-id="0e16c-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="0e16c-145">反雙曲餘切（Acoth （x））</span><span class="sxs-lookup"><span data-stu-id="0e16c-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="0e16c-146">Log （（x + 1）/（x –1））/2</span><span class="sxs-lookup"><span data-stu-id="0e16c-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e16c-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e16c-147">See also</span></span>

- [<span data-ttu-id="0e16c-148">Math 函數</span><span class="sxs-lookup"><span data-stu-id="0e16c-148">Math Functions</span></span>](../functions/math-functions.md)
