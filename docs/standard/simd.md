---
title: .NET 中的 SIMD 加速類型
description: '本文說明 .NET 中的 SIMD 啟用類型，並示範如何在 c # 和 .NET 中使用硬體 SIMD 作業。'
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 5c1ad01ea15a9c4352cf7f87e5fba3bf74b4679c
ms.sourcegitcommit: 2987e241e2f76c9248d2146bf2761a33e2c7a882
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88228732"
---
# <a name="use-simd-accelerated-numeric-types"></a>使用 SIMD 加速數數值型別

SIMD (單一指令，多個資料) 提供硬體支援，讓您使用單一指令以平行方式對多個資料片段執行作業。 在 .NET 中，命名空間下有一組 SIMD 加速類型 <xref:System.Numerics> 。 SIMD 作業可以在硬體層級平行處理。 這能提升向量化運算 (常見於數學、科學及圖形應用程式中) 的輸送量。

## <a name="net-simd-accelerated-types"></a>.NET SIMD-加速類型

.NET SIMD-加速類型包含下列類型：

- <xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3> 及 <xref:System.Numerics.Vector4> 類型，其代表具有 2、3 及 4 <xref:System.Single> 值的向量。

- 兩個矩陣類型（ <xref:System.Numerics.Matrix3x2> 代表3x2 矩陣）和 <xref:System.Numerics.Matrix4x4> （表示值的4x4 矩陣） <xref:System.Single> 。

- <xref:System.Numerics.Plane>類型，表示使用值的3d 空間中的平面 <xref:System.Single> 。

- <xref:System.Numerics.Quaternion>類型，表示用來編碼三維實體旋轉使用值的向量 <xref:System.Single> 。

- <xref:System.Numerics.Vector%601> 類型，其代表指定數值類型的向量，並能提供一組受益於 SIMD 支援的廣泛運算子。 在 <xref:System.Numerics.Vector%601> 應用程式的存留期內，實例的計數是固定的，但其值 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> 取決於執行程式碼之電腦的 CPU。

  > [!NOTE]
  > 此 <xref:System.Numerics.Vector%601> 類型不包含在 .NET Framework 中。 您必須安裝 [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) \(英文\) NuGet 套件以存取這個類型。
  
SIMD 加速型別的實作為可以搭配非 SIMD 加速硬體或 JIT 編譯程式使用的方式。 若要利用 SIMD 指示，您的64位應用程式必須由使用 **RyuJIT** 編譯器的執行時間執行。 **RyuJIT**編譯器包含在 .net Core 和 .NET Framework 4.6 和更新版本中。 只有以64位處理器為目標時，才會提供 SIMD 支援。

## <a name="how-to-use-simd"></a>如何使用 SIMD？

執行自訂 SIMD 演算法之前，您可以使用來檢查主機電腦是否支援 SIMD，這會傳回 <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType> <xref:System.Boolean> 。 這並不保證會針對特定類型啟用 SIMD 加速，而是某些類型支援的指標。

## <a name="simple-vectors"></a>簡單向量

.NET 中最基本的 SIMD 加速類型是 <xref:System.Numerics.Vector2> 、 <xref:System.Numerics.Vector3> 和 <xref:System.Numerics.Vector4> 類型，代表具有2、3和4值的向量 <xref:System.Single> 。 下列範例會使用 <xref:System.Numerics.Vector2> 來新增兩個向量。

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult = v1 + v2;
```

您也可以使用 .net 向量來計算向量的其他數學屬性 `Dot product` ，例如、 `Transform` 等等 `Clamp` 。

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResult1 = Vector2.Dot(v1, v2);
var vResult2 = Vector2.Distance(v1, v2);
var vResult3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a>矩陣

<xref:System.Numerics.Matrix3x2>，代表3x2 矩陣，而 <xref:System.Numerics.Matrix4x4> 則代表4x4 矩陣。 可以用於矩陣相關的計算。 下列範例示範如何使用 SIMD 將矩陣乘以其對應的轉置矩陣。

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a>向量\<T>

<xref:System.Numerics.Vector%601>提供使用較長向量的功能。 實例的計數 <xref:System.Numerics.Vector%601> 是固定的，但其值 <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> 取決於執行程式碼之電腦的 CPU。

下列範例示範如何使用來新增長陣列元素 <xref:System.Numerics.Vector%601> 。

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

## <a name="remarks"></a>備註

SIMD 較可能會移除一個瓶頸，並公開下一個，例如記憶體輸送量。 一般來說，使用 SIMD 的效能優勢會因特定案例而有所不同，在某些情況下，它甚至可以比簡單的非 SIMD 對等程式碼更糟。
