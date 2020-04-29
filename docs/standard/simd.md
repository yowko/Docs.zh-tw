---
title: .NET 中的 SIMD 加速類型
description: '本文說明 .NET 中的 SIMD 啟用類型，並示範如何在 c # 和 .NET 中使用硬體 SIMD 作業。'
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 27263931ff0338e194c8fd3d9ec5ba59bfafd9fe
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507779"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="535b3-103">使用 SIMD 加速數數值型別</span><span class="sxs-lookup"><span data-stu-id="535b3-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="535b3-104">SIMD （單一指令、多個資料）會使用單一指令，以平行方式對多個資料片段執行作業提供硬體支援。</span><span class="sxs-lookup"><span data-stu-id="535b3-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="535b3-105">在 .NET 中， <xref:System.Numerics>命名空間下有一組 SIMD 加速類型。</span><span class="sxs-lookup"><span data-stu-id="535b3-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="535b3-106">SIMD 作業可以在硬體層級平行處理。</span><span class="sxs-lookup"><span data-stu-id="535b3-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="535b3-107">這能提升向量化運算 (常見於數學、科學及圖形應用程式中) 的輸送量。</span><span class="sxs-lookup"><span data-stu-id="535b3-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="535b3-108">.NET SIMD-加速類型</span><span class="sxs-lookup"><span data-stu-id="535b3-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="535b3-109">.NET SIMD-加速類型包含下列類型：</span><span class="sxs-lookup"><span data-stu-id="535b3-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="535b3-110"><xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3> 及 <xref:System.Numerics.Vector4> 類型，其代表具有 2、3 及 4 <xref:System.Single> 值的向量。</span><span class="sxs-lookup"><span data-stu-id="535b3-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="535b3-111">兩個矩陣類型<xref:System.Numerics.Matrix3x2>（代表3x2 矩陣）和<xref:System.Numerics.Matrix4x4>（表示<xref:System.Single>值的4x4 矩陣）。</span><span class="sxs-lookup"><span data-stu-id="535b3-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="535b3-112"><xref:System.Numerics.Plane>類型，表示使用<xref:System.Single>值的3d 空間中的平面。</span><span class="sxs-lookup"><span data-stu-id="535b3-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="535b3-113"><xref:System.Numerics.Quaternion>類型，表示用來編碼三維實體旋轉使用<xref:System.Single>值的向量。</span><span class="sxs-lookup"><span data-stu-id="535b3-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="535b3-114"><xref:System.Numerics.Vector%601> 類型，其代表指定數值類型的向量，並能提供一組受益於 SIMD 支援的廣泛運算子。</span><span class="sxs-lookup"><span data-stu-id="535b3-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="535b3-115">在應用程式的<xref:System.Numerics.Vector%601>存留期內，實例的計數是固定的，但其<xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType>值取決於執行程式碼之電腦的 CPU。</span><span class="sxs-lookup"><span data-stu-id="535b3-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="535b3-116">此<xref:System.Numerics.Vector%601>類型不包含在 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="535b3-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="535b3-117">您必須安裝 [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) \(英文\) NuGet 套件以存取這個類型。</span><span class="sxs-lookup"><span data-stu-id="535b3-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="535b3-118">SIMD 加速型別的實作為可以搭配非 SIMD 加速硬體或 JIT 編譯程式使用的方式。</span><span class="sxs-lookup"><span data-stu-id="535b3-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="535b3-119">若要利用 SIMD 指示，您的64位應用程式必須由使用**RyuJIT**編譯器的執行時間執行。</span><span class="sxs-lookup"><span data-stu-id="535b3-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="535b3-120">**RyuJIT**編譯器包含在 .net Core 和 .NET Framework 4.6 和更新版本中。</span><span class="sxs-lookup"><span data-stu-id="535b3-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="535b3-121">只有以64位處理器為目標時，才會提供 SIMD 支援。</span><span class="sxs-lookup"><span data-stu-id="535b3-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="535b3-122">如何使用 SIMD？</span><span class="sxs-lookup"><span data-stu-id="535b3-122">How to use SIMD?</span></span>

<span data-ttu-id="535b3-123">執行自訂 SIMD 演算法之前，您可以使用<xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>來檢查主機電腦是否支援 SIMD，這會傳回。 <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="535b3-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="535b3-124">這並不保證會針對特定類型啟用 SIMD 加速，而是某些類型支援的指標。</span><span class="sxs-lookup"><span data-stu-id="535b3-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="535b3-125">簡單向量</span><span class="sxs-lookup"><span data-stu-id="535b3-125">Simple Vectors</span></span>

<span data-ttu-id="535b3-126">.Net 中最基本的 SIMD 加速類型<xref:System.Numerics.Vector2>是、 <xref:System.Numerics.Vector3>和<xref:System.Numerics.Vector4>類型，代表具有2、3和 4 <xref:System.Single>值的向量。</span><span class="sxs-lookup"><span data-stu-id="535b3-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="535b3-127">下列範例會使用<xref:System.Numerics.Vector2>來新增兩個向量。</span><span class="sxs-lookup"><span data-stu-id="535b3-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl = v1 + v2;
```

<span data-ttu-id="535b3-128">您也可以使用 .net 向量來計算向量的其他數學屬性`Dot product`，例如、 `Transform`等等。 `Clamp`</span><span class="sxs-lookup"><span data-stu-id="535b3-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl1 = Vector2.Dot(v1, v2);
var vResutl2 = Vector2.Distance(v1, v2);
var vResutl3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="535b3-129">矩陣</span><span class="sxs-lookup"><span data-stu-id="535b3-129">Matrix</span></span>

<span data-ttu-id="535b3-130"><xref:System.Numerics.Matrix3x2>，代表3x2 矩陣，而<xref:System.Numerics.Matrix4x4>則代表4x4 矩陣。</span><span class="sxs-lookup"><span data-stu-id="535b3-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="535b3-131">可以用於矩陣相關的計算。</span><span class="sxs-lookup"><span data-stu-id="535b3-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="535b3-132">下列範例示範如何使用 SIMD 將矩陣乘以其對應的轉置矩陣。</span><span class="sxs-lookup"><span data-stu-id="535b3-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="535b3-133">向量\<T></span><span class="sxs-lookup"><span data-stu-id="535b3-133">Vector\<T></span></span>

<span data-ttu-id="535b3-134"><xref:System.Numerics.Vector%601>提供使用較長向量的功能。</span><span class="sxs-lookup"><span data-stu-id="535b3-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="535b3-135"><xref:System.Numerics.Vector%601>實例的計數是固定的，但其值<xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType>取決於執行程式碼之電腦的 CPU。</span><span class="sxs-lookup"><span data-stu-id="535b3-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="535b3-136">下列範例示範如何使用來<xref:System.Numerics.Vector%601>新增長陣列元素。</span><span class="sxs-lookup"><span data-stu-id="535b3-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

```csharp
double[] SimdVectorProd(double[] left, double[] right)
{
    var offset = Vector<double>.Count;
    double[] result = new double[left.Length];
    int i = 0;
    for (i = 0; i < left.Length; i += offset)
    {
        var v1 = new Vector<double>(left, i);
        var v2 = new Vector<double>(right, i);
        (v1 * v2).CopyTo(result, i);
    }

    //remaining items
    for (; i < left.Length; ++i)
    {
        result[i] = left[i] * right[i];
    }

    return result;
}
```

## <a name="remarks"></a><span data-ttu-id="535b3-137">備註</span><span class="sxs-lookup"><span data-stu-id="535b3-137">Remarks</span></span>

<span data-ttu-id="535b3-138">SIMD 較可能會移除一個瓶頸，並公開下一個，例如記憶體輸送量。</span><span class="sxs-lookup"><span data-stu-id="535b3-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="535b3-139">一般來說，使用 SIMD 的效能優勢會因特定案例而有所不同，在某些情況下，它甚至可以比簡單的非 SIMD 對等程式碼更糟。</span><span class="sxs-lookup"><span data-stu-id="535b3-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
