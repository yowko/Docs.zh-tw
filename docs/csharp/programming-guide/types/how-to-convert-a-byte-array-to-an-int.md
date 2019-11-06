---
title: 如何：將位元組陣列轉換為 int 程式C#設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: cb6252069302a28f8a85247aa4584a9284b26c4d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195462"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>如何：將位元組陣列轉換成整數 (C# 程式設計手冊)

本例示範如何使用 <xref:System.BitConverter> 類別將位元組陣列轉換成 [int](../../language-reference/builtin-types/integral-numeric-types.md)，再回復成位元組陣列。 例如，在讀取網路位元組後，您可能必須從位元組轉換成內建資料類型。 除了範例中的[ToInt32 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法之外，下表還會列出將位元組（從位元組陣列）轉換成其他內建類型的 <xref:System.BitConverter> 類別中的方法。

|傳回的類型|方法|
|-------------------|------------|
|`bool`|[ToBoolean （Byte\[\]，Int32）](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar （Byte\[\]，Int32）](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble （Byte\[\]，Int32）](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[ToInt16 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[ToInt32 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[ToInt64 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle （Byte\[\]，Int32）](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[ToUInt16 （Byte\[\]，Int32）](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[ToUInt32 （Byte\[\]，Int32）](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[ToUInt64 （Byte\[\]，Int32）](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>範例

這個範例會初始化位元組的陣列，如果電腦架構是以小序（也就是第一次儲存最不重要的位元組），則會反轉陣列，然後呼叫[ToInt32 （byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法來轉換四個位元組在 `int`的陣列中。 ToInt32 的第二個引數[（Byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))會指定位元組陣列的開始索引。

> [!NOTE]
> 輸出可能會根據您電腦架構的「位元組順序」而有所不同。

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>範例

在此範例中，會呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法，將 `int` 轉換成位元組陣列。

> [!NOTE]
> 輸出可能會根據您電腦架構的「位元組順序」而有所不同。

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>請參閱

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [型別](./index.md)
