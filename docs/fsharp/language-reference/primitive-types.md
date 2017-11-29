---
title: "基本類型 (F#)"
description: "探索用於 F # 語言的基本基本類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a>基本類型

本主題列出用於 F # 語言的基本基本類型。 它也會提供對應的 .NET 類型以及每個類型的最小值和最大值。

## <a name="summary-of-primitive-types"></a>基本類型的摘要
下表摘要說明基本的 F # 類型的屬性。

|類型|.NET 型別|說明|
|----|---------|-----------|
|`bool`|`System.Boolean`|可能的值為 `true` 和 `false`。|
|`byte`|`System.Byte`|從 0 到 255 之間的值。|
|`sbyte`|`System.SByte`|從-128 到 127 的值。|
|`int16`|`System.Int16`|從-32768 到 32767 之間的值。|
|`uint16`|`System.UInt16`|介於 0 到 65535 的值。|
|`int`|`System.Int32`|從-2,147,483,648 到 2,147,483,647 的值。|
|`uint32`|`System.UInt32`|介於 0 到 4,294,967,295 的值。|
|`int64`|`System.Int64`|值-9223372036854775808 到 9,223,372,036,854,775,807。|
|`uint64`|`System.UInt64`|介於 0 到 18446744073709551615 的值。|
|`nativeint`|`System.IntPtr`|原生指標為帶正負號的整數。|
|`unativeint`|`System.UIntPtr`|原生指標的不帶正負號的整數。|
|`char`|`System.Char`|Unicode 字元值。|
|`string`|`System.String`|Unicode 文字。|
|`decimal`|`System.Decimal`|浮點資料類型具有至少 28 位有效位數。|
|`unit`|不適用|指出實際的值不存在。 類型具有一個型式的值，表示`()`。 單位值， `()`，通常是做為預留位置，其中需要值時，但沒有真正的價值可用或有意義。|
|`void`|`System.Void`|表示沒有類型或值。|
|`float32, single`|`System.Single`|32 位元浮點類型。|
|`float, double`|`System.Double`|64 位元浮點類型。|

>[!NOTE]
您也可以使用 64 位元整數類型的執行與整數太大的計算[bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa)型別。 `bigint`不是基本型別。它是的縮寫`System.Numerics.BigInteger`。

## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
