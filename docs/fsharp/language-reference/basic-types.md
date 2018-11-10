---
title: 基本類型 （F#）
description: 探索基本 F# 語言中使用的基本類型。
ms.date: 07/09/2018
ms.openlocfilehash: 8f948d066323527b09b1d3f9f4167b95b1c875cf
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "48026931"
---
# <a name="basic-types"></a>基本類型

本主題列出 F# 語言中所定義的基本型別。 這些類型是最基本 F#，形成幾乎每個 F# 程式的基礎。 也就是.NET 基本類型的超集。

|類型|.NET 型別|描述|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|可能的值為 `true` 和 `false`。|
|`byte`|<xref:System.Byte>|介於 0 到 255 的值。|
|`sbyte`|<xref:System.SByte>|介於-128 到 127 的值。|
|`int16`|<xref:System.Int16>|範圍為-32768 到 32767 之間的值。|
|`uint16`|<xref:System.UInt16>|介於 0 到 65535 的值。|
|`int`|<xref:System.Int32>|從-2,147,483,648 到 2,147,483,647 的值。|
|`uint32`|<xref:System.UInt32>|介於 0 到 4,294,967,295 的值。|
|`int64`|<xref:System.Int64>|值-9223372036854775808 到 9,223,372,036,854,775,807。|
|`uint64`|<xref:System.UInt64>|介於 0 到 18446744073709551615 的值。|
|`nativeint`|<xref:System.IntPtr>|為帶正負號的整數變數的原生指標。|
|`unativeint`|<xref:System.UIntPtr>|原生指標做為不帶正負號的整數。|
|`char`|<xref:System.Char>|Unicode 字元值。|
|`string`|<xref:System.String>|Unicode 文字。|
|`decimal`|<xref:System.Decimal>|浮點資料型別具有至少 28 位有效位數。|
|`unit`|不適用|表示沒有實際的值。 類型具有一個型式的值，表示`()`。 單位值， `()`，通常做為預留位置，其中需要值時，但沒有真正的值使用，或有意義。|
|`void`|<xref:System.Void>|表示沒有類型或值。|
|`float32`、 `single`|<xref:System.Single>|32 位元浮點數類型。|
|`float`、 `double`|<xref:System.Double>|64 位元浮點數類型。|

>[!NOTE]
您也可以使用 64 位元整數類型執行計算整數太大[bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型別。 `bigint` 不是基本的類型;它是縮寫`System.Numerics.BigInteger`。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
