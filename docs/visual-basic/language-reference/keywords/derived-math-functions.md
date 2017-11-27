---
title: "衍生的數學函式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5816fa4c8c384eca116fa1512950a3588c6e3392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="1bc7d-102">衍生的數學函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="1bc7d-103">下表顯示這些可以衍生自內建數學函式的非內建的數學函式<xref:System.Math?displayProperty=nameWithType>物件。</span><span class="sxs-lookup"><span data-stu-id="1bc7d-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="1bc7d-104">您可以存取內建數學函式加入`Imports System.Math`至您的檔案或專案。</span><span class="sxs-lookup"><span data-stu-id="1bc7d-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="1bc7d-105">函式</span><span class="sxs-lookup"><span data-stu-id="1bc7d-105">Function</span></span>|<span data-ttu-id="1bc7d-106">在衍生的對等項目</span><span class="sxs-lookup"><span data-stu-id="1bc7d-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="1bc7d-107">正割 (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-107">Secant (Sec(x))</span></span>|<span data-ttu-id="1bc7d-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="1bc7d-109">餘割 (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="1bc7d-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="1bc7d-111">餘切函數 (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="1bc7d-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="1bc7d-113">反正弦 (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="1bc7d-114">Atan (x / Sqrt (-x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-114">Atan(x / Sqrt(-x * x + 1))</span></span>|  
|<span data-ttu-id="1bc7d-115">反餘弦 (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="1bc7d-116">Atan (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="1bc7d-117">反向正割 (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="1bc7d-118">2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="1bc7d-119">數值的反餘割 (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="1bc7d-120">Atan(Sign(x) / Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-120">Atan(Sign(x) / Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="1bc7d-121">數值的反餘切函數 (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="1bc7d-122">2 * Atan(1)-Atan(x)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-122">2 * Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="1bc7d-123">雙曲線正弦函數 (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="1bc7d-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="1bc7d-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="1bc7d-125">雙曲線餘弦 (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="1bc7d-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="1bc7d-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="1bc7d-127">雙曲正切 (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="1bc7d-128">(Exp(x) – Exp(-x)) / （Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="1bc7d-129">雙曲正割 (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="1bc7d-130">2 / （Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="1bc7d-131">雙曲餘割 (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="1bc7d-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="1bc7d-133">雙曲餘切值 (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="1bc7d-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="1bc7d-135">反雙曲正弦 (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="1bc7d-136">記錄檔 (x + Sqrt (x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-136">Log(x + Sqrt(x * x + 1))</span></span>|  
|<span data-ttu-id="1bc7d-137">反雙曲線餘弦 (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="1bc7d-138">記錄檔 (x + Sqrt (x * x – 1))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-138">Log(x + Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="1bc7d-139">反雙曲正切 (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="1bc7d-140">記錄 ((1 + x) / (1-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="1bc7d-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="1bc7d-141">數值的反雙曲正割 (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="1bc7d-142">記錄檔 ((Sqrt (-x * x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-142">Log((Sqrt(-x * x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="1bc7d-143">數值的反雙曲餘割 (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="1bc7d-144">Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="1bc7d-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="1bc7d-145">數值的反雙曲餘切值 (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="1bc7d-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="1bc7d-146">記錄 ((x + 1) / (x – 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="1bc7d-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bc7d-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc7d-147">See Also</span></span>  
 [<span data-ttu-id="1bc7d-148">數學函式</span><span class="sxs-lookup"><span data-stu-id="1bc7d-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
