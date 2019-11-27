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
ms.openlocfilehash: 73cf56dd72f2baac0474d6f5c4e88228a1fe38cf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349843"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="bda29-102">衍生的數學函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bda29-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="bda29-103">下表顯示的非內建數學函數，可以衍生自 <xref:System.Math?displayProperty=nameWithType> 物件的內建數學函式。</span><span class="sxs-lookup"><span data-stu-id="bda29-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="bda29-104">您可以藉由將 `Imports System.Math` 新增至檔案或專案，來存取內建數學函數。</span><span class="sxs-lookup"><span data-stu-id="bda29-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="bda29-105">函式</span><span class="sxs-lookup"><span data-stu-id="bda29-105">Function</span></span>|<span data-ttu-id="bda29-106">衍生的對等專案</span><span class="sxs-lookup"><span data-stu-id="bda29-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="bda29-107">正割（秒（x））</span><span class="sxs-lookup"><span data-stu-id="bda29-107">Secant (Sec(x))</span></span>|<span data-ttu-id="bda29-108">1/Cos （x）</span><span class="sxs-lookup"><span data-stu-id="bda29-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="bda29-109">余割（Csc （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="bda29-110">1/Sin （x）</span><span class="sxs-lookup"><span data-stu-id="bda29-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="bda29-111">餘切（Ctan （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="bda29-112">1/Tan （x）</span><span class="sxs-lookup"><span data-stu-id="bda29-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="bda29-113">反正弦函數（Asin （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="bda29-114">Atan （x/Sqrt （-x \* x + 1））</span><span class="sxs-lookup"><span data-stu-id="bda29-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="bda29-115">反余弦函數（Acos （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="bda29-116">Atan （-x/Sqrt （-x \* x + 1）） + 2 \* Atan （1）</span><span class="sxs-lookup"><span data-stu-id="bda29-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="bda29-117">反正割（Asec （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="bda29-118">2 \* Atan （1）– Atan （Sign （x）/Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="bda29-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="bda29-119">反向余割（Acsc （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="bda29-120">Atan （Sign （x）/Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="bda29-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="bda29-121">反向餘切（Acot （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="bda29-122">2 \* Atan （1）-Atan （x）</span><span class="sxs-lookup"><span data-stu-id="bda29-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="bda29-123">雙曲正弦（Sinh （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="bda29-124">（Exp （x）– Exp （-x））/2</span><span class="sxs-lookup"><span data-stu-id="bda29-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="bda29-125">雙曲余弦（Cosh （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="bda29-126">（Exp （x） + Exp （-x））/2</span><span class="sxs-lookup"><span data-stu-id="bda29-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="bda29-127">雙曲正切函數（Tanh （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="bda29-128">（Exp （x）– Exp （-x））/（Exp （x） + Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="bda29-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="bda29-129">雙曲正割（Sech （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="bda29-130">2/（Exp （x） + Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="bda29-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="bda29-131">雙曲余割（Csch （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="bda29-132">2/（Exp （x）– Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="bda29-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="bda29-133">雙曲餘切（Coth （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="bda29-134">（Exp （x） + Exp （-x））/（Exp （x）– Exp （-x））</span><span class="sxs-lookup"><span data-stu-id="bda29-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="bda29-135">反雙曲正弦（Asinh （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="bda29-136">Log （x + Sqrt （x \* x + 1））</span><span class="sxs-lookup"><span data-stu-id="bda29-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="bda29-137">反雙曲余弦（Acosh （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="bda29-138">Log （x + Sqrt （x \* x –1））</span><span class="sxs-lookup"><span data-stu-id="bda29-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="bda29-139">反雙曲正切（Atanh （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="bda29-140">Log （（1 + x）/（1– x））/2</span><span class="sxs-lookup"><span data-stu-id="bda29-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="bda29-141">反雙曲正割（AsecH （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="bda29-142">Log （（Sqrt （-x \* x + 1） + 1）/x）</span><span class="sxs-lookup"><span data-stu-id="bda29-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="bda29-143">反雙曲余割（Acsch （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="bda29-144">Log （（符號（x） \* Sqrt （x \* x + 1） + 1）/x）</span><span class="sxs-lookup"><span data-stu-id="bda29-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="bda29-145">反雙曲餘切（Acoth （x））</span><span class="sxs-lookup"><span data-stu-id="bda29-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="bda29-146">Log （（x + 1）/（x –1））/2</span><span class="sxs-lookup"><span data-stu-id="bda29-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bda29-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="bda29-147">See also</span></span>

- [<span data-ttu-id="bda29-148">數學函式</span><span class="sxs-lookup"><span data-stu-id="bda29-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
