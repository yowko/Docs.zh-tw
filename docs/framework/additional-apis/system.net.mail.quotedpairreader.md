---
title: QuotedPairReader 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.QuotedPairReader
- System.Net.Mail.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 898c6e9d2d5dd02f3d5f9c096ad470b5dd445d1d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051307"
---
# <a name="quotedpairreader-class"></a>QuotedPairReader 類別

決定以引號括住的字串括住的字元（已轉義）。 這個類別無法被繼承。

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> 這個類別是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="countquotedchars-method"></a>CountQuotedChars 方法

在指定的字串中計算連續加上引號的字元數，包括多個前面加上引號的反斜線。 例如，假設字串和的 `a\\\b` 索引 `4` ，方法 `4` 會傳回，因為 `b` 會加上引號，因此是前面三個反斜線。

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a>參數

- `data` <xref:System.String>

  要在其中計算連續引號字元的資料字串。

- `index` <xref:System.Int32>

  指定字串中的位置，最高到，包括應計算的連續引號字元。

- `permitUnicodeEscaping` <xref:System.Boolean>

  `true`表示允許轉義 Unicode 字元;否則為 `false` 。

### <a name="return-value"></a>傳回值

<xref:System.Int32?displayProperty=nameWithType>

`0`如果指定索引處的字元未進行轉義，則為，否則，就是在中最多加上引號字元數，並在其中包含字元 `index` 。

### <a name="exceptions"></a>例外狀況

<xref:System.FormatException?displayProperty=nameWithType>

找到了已轉義的 Unicode 字元，但不允許這樣做。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
