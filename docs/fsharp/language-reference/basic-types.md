---
title: 基本類型
description: '探索 F # 語言中使用的基本基本類型。'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557694"
---
# <a name="basic-types"></a>基本類型

本主題列出在 F # 語言中定義的基本類型。 這些類型在 F # 中是最基本的，形成幾乎每一個 F # 程式的基礎。 它們是 .NET 基本型別的超集合。

|類型|.NET 類型|描述|範例|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|可能的值是 `true` 和 `false`。|`true`/`false`|
|`byte`|<xref:System.Byte>|從0到255的值。|`1uy`|
|`sbyte`|<xref:System.SByte>|介於-128 到127之間的值。|`1y`|
|`int16`|<xref:System.Int16>|介於-32768 到32767之間的值。|`1s`|
|`uint16`|<xref:System.UInt16>|從0到65535的值。|`1us`|
|`int`|<xref:System.Int32>|介於-2147483648 到2147483647之間的值。|`1`|
|`uint`|<xref:System.UInt32>|從0到4294967295的值。|`1u`|
|`int64`|<xref:System.Int64>|從-9223372036854775808 到9223372036854775807的值。|`1L`|
|`uint64`|<xref:System.UInt64>|0到18446744073709551615之間的值。|`1UL`|
|`nativeint`|<xref:System.IntPtr>|作為帶正負號整數的原生指標。|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|原生指標，作為不帶正負號的整數。|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|浮點數資料類型至少有28個有效位數。|`1.0`|
|`float`, `double`|<xref:System.Double>|64位浮點數類型。|`1.0`|
|`float32`, `single`|<xref:System.Single>|32位浮點數類型。|`1.0f`|
|`char`|<xref:System.Char>|Unicode 字元值。|`'c'`|
|`string`|<xref:System.String>|Unicode 文字。|`"str"`|
|`unit`|不適用|指出沒有實際值。 型別只有一個正式值，即表示 `()` 。 單位值（ `()` ）通常用來做為需要值的預留位置，但沒有可用的實際值或意義。|`()`|

> [!NOTE]
> 您可以使用 [Bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) 型別，對64位整數類型的整數執行太大的計算。 `bigint` 不會被視為基本類型;這是的縮寫 `System.Numerics.BigInteger` 。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
