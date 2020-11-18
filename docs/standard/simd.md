---
title: .NET 中的 SIMD 加速類型
description: '本文說明在 .NET 中啟用 SIMD 的類型，並示範如何在 c # 和 .NET 中使用硬體 SIMD 作業。'
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.openlocfilehash: 9ac437fd78ed81cd4c2d786f52bac80c5cf22e8f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826620"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="b0d70-103">使用 SIMD 加速的數數值型別</span><span class="sxs-lookup"><span data-stu-id="b0d70-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="b0d70-104">SIMD (單一指令，多個資料) 提供硬體支援，可讓您使用單一指示，以平行方式在多個資料片段上執行運算。</span><span class="sxs-lookup"><span data-stu-id="b0d70-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="b0d70-105">在 .NET 中，命名空間底下有一組 SIMD 加速類型 <xref:System.Numerics> 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="b0d70-106">SIMD 作業可在硬體層級進行平行處理。</span><span class="sxs-lookup"><span data-stu-id="b0d70-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="b0d70-107">這能提升向量化運算 (常見於數學、科學及圖形應用程式中) 的輸送量。</span><span class="sxs-lookup"><span data-stu-id="b0d70-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="b0d70-108">.NET SIMD-加速類型</span><span class="sxs-lookup"><span data-stu-id="b0d70-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="b0d70-109">.NET SIMD 加速類型包含下列類型：</span><span class="sxs-lookup"><span data-stu-id="b0d70-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="b0d70-110"><xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3> 及 <xref:System.Numerics.Vector4> 類型，其代表具有 2、3 及 4 <xref:System.Single> 值的向量。</span><span class="sxs-lookup"><span data-stu-id="b0d70-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="b0d70-111">兩個矩陣類型（ <xref:System.Numerics.Matrix3x2> 代表3x2 矩陣）和 <xref:System.Numerics.Matrix4x4> （代表值的4x4 矩陣） <xref:System.Single> 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="b0d70-112"><xref:System.Numerics.Plane>類型，代表使用值之三維空間中的平面 <xref:System.Single> 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="b0d70-113"><xref:System.Numerics.Quaternion>型別，表示用來使用值編碼三維實體旋轉的向量 <xref:System.Single> 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="b0d70-114"><xref:System.Numerics.Vector%601> 類型，其代表指定數值類型的向量，並能提供一組受益於 SIMD 支援的廣泛運算子。</span><span class="sxs-lookup"><span data-stu-id="b0d70-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="b0d70-115">在 <xref:System.Numerics.Vector%601> 應用程式的存留期內，實例的計數是固定的，但其值 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> 取決於執行程式碼之電腦的 CPU。</span><span class="sxs-lookup"><span data-stu-id="b0d70-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b0d70-116">此 <xref:System.Numerics.Vector%601> 類型不包含在 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="b0d70-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="b0d70-117">您必須安裝 [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) \(英文\) NuGet 套件以存取這個類型。</span><span class="sxs-lookup"><span data-stu-id="b0d70-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="b0d70-118">SIMD 加速類型會以可搭配非 SIMD 加速硬體或 JIT 編譯程式使用的方式來執行。</span><span class="sxs-lookup"><span data-stu-id="b0d70-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="b0d70-119">若要利用 SIMD 指令，您的64位應用程式必須由使用 **RyuJIT** 編譯器的執行時間執行。</span><span class="sxs-lookup"><span data-stu-id="b0d70-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="b0d70-120">**RyuJIT** 編譯器隨附于 .net Core 和 .NET Framework 4.6 和更新版本中。</span><span class="sxs-lookup"><span data-stu-id="b0d70-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="b0d70-121">只有在以64位處理器為目標時，才會提供 SIMD 支援。</span><span class="sxs-lookup"><span data-stu-id="b0d70-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="b0d70-122">如何使用 SIMD？</span><span class="sxs-lookup"><span data-stu-id="b0d70-122">How to use SIMD?</span></span>

<span data-ttu-id="b0d70-123">在執行自訂 SIMD 演算法之前，可以使用傳回的來檢查主機電腦是否支援 SIMD <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> <xref:System.Boolean> 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="b0d70-124">這並不保證會針對特定類型啟用 SIMD 加速功能，但這是某些類型所支援的指標。</span><span class="sxs-lookup"><span data-stu-id="b0d70-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="b0d70-125">簡單向量</span><span class="sxs-lookup"><span data-stu-id="b0d70-125">Simple Vectors</span></span>

<span data-ttu-id="b0d70-126">.NET 中最基本的 SIMD 加速類型是 <xref:System.Numerics.Vector2> 、 <xref:System.Numerics.Vector3> 和 <xref:System.Numerics.Vector4> 類型，代表具有2、3和4值的向量 <xref:System.Single> 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="b0d70-127">下列範例會使用 <xref:System.Numerics.Vector2> 來新增兩個向量。</span><span class="sxs-lookup"><span data-stu-id="b0d70-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

<span data-ttu-id="b0d70-128">您也可以使用 .net 向量來計算向量的其他數學屬性 `Dot product` ，例如、 `Transform` 等等 `Clamp` 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="b0d70-129">矩陣</span><span class="sxs-lookup"><span data-stu-id="b0d70-129">Matrix</span></span>

<span data-ttu-id="b0d70-130"><xref:System.Numerics.Matrix3x2>代表3x2 矩陣的，以及 <xref:System.Numerics.Matrix4x4> 表示4x4 矩陣的。</span><span class="sxs-lookup"><span data-stu-id="b0d70-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="b0d70-131">可用於矩陣相關計算。</span><span class="sxs-lookup"><span data-stu-id="b0d70-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="b0d70-132">下列範例示範如何使用 SIMD 將矩陣乘至其對應的換位矩陣。</span><span class="sxs-lookup"><span data-stu-id="b0d70-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="b0d70-133">向量\<T></span><span class="sxs-lookup"><span data-stu-id="b0d70-133">Vector\<T></span></span>

<span data-ttu-id="b0d70-134"><xref:System.Numerics.Vector%601>提供使用較長向量的能力。</span><span class="sxs-lookup"><span data-stu-id="b0d70-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="b0d70-135">實例的計數 <xref:System.Numerics.Vector%601> 是固定的，但其值 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> 取決於執行程式碼之電腦的 CPU。</span><span class="sxs-lookup"><span data-stu-id="b0d70-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="b0d70-136">下列範例示範如何使用新增長陣列元素 <xref:System.Numerics.Vector%601> 。</span><span class="sxs-lookup"><span data-stu-id="b0d70-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b0d70-137">備註</span><span class="sxs-lookup"><span data-stu-id="b0d70-137">Remarks</span></span>

<span data-ttu-id="b0d70-138">SIMD 更可能移除一個瓶頸並公開下一個瓶頸，例如記憶體輸送量。</span><span class="sxs-lookup"><span data-stu-id="b0d70-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="b0d70-139">一般而言，使用 SIMD 的效能優點會因特定案例而有所不同，而且在某些情況下，它甚至可以比更簡單的非 SIMD 對等程式碼更糟。</span><span class="sxs-lookup"><span data-stu-id="b0d70-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
