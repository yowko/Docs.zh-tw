---
title: 如何將位元組陣列轉換為 int - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698751"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>如何將位元組陣列轉換為 int（C# 程式設計指南）

本例示範如何使用 <xref:System.BitConverter> 類別將位元組陣列轉換成 [int](../../language-reference/builtin-types/integral-numeric-types.md)，再回復成位元組陣列。 例如，在讀取網路位元組後，您可能必須從位元組轉換成內建資料類型。 除了示例中的[ToInt32（位元組\[\]、 Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法外，下表還列出了<xref:System.BitConverter>類中將位元組（從位元組陣列）轉換為其他內置類型的方法。

|傳回的類型|方法|
|-------------------|------------|
|`bool`|[托布利安（位元組\[\]，Int32）](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[托查爾（位元組\[\]， Int32）](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[到雙（位元組\[\]， Int32）](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toint16（位元組\[\]， Int32）](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[Toint32（位元組\[\]， Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toint64（位元組\[\]， Int32）](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[到單（位元組\[\]， Int32）](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[ToUInt16（位元組\[\]，Int32）](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[ToUInt32（位元組\[\]，Int32）](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[ToUInt64（位元組\[\]，Int32）](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>範例

此示例初始化位元組陣列，如果電腦體系結構是小位元組（即首先存儲最不重要的位元組），則反轉陣列，然後調用[ToInt32（位元組\[\]， Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法將陣列中的四個`int`位元組轉換為 。 [ \[ \]ToInt32（位元組，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))的第二個參數指定位元組陣列的開始索引。

> [!NOTE]
> 輸出可能因電腦體系結構的端性而異。

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>範例

在此範例中，會呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法，將 `int` 轉換成位元組陣列。

> [!NOTE]
> 輸出可能因電腦體系結構的端性而異。

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>另請參閱

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [型別](./index.md)
