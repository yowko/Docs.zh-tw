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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="e4d15-102">如何：將位元組陣列轉換成整數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e4d15-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="e4d15-103">本例示範如何使用 <xref:System.BitConverter> 類別將位元組陣列轉換成 [int](../../language-reference/builtin-types/integral-numeric-types.md)，再回復成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="e4d15-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="e4d15-104">例如，在讀取網路位元組後，您可能必須從位元組轉換成內建資料類型。</span><span class="sxs-lookup"><span data-stu-id="e4d15-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="e4d15-105">除了範例中的[ToInt32 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法之外，下表還會列出將位元組（從位元組陣列）轉換成其他內建類型的 <xref:System.BitConverter> 類別中的方法。</span><span class="sxs-lookup"><span data-stu-id="e4d15-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="e4d15-106">傳回的類型</span><span class="sxs-lookup"><span data-stu-id="e4d15-106">Type returned</span></span>|<span data-ttu-id="e4d15-107">方法</span><span class="sxs-lookup"><span data-stu-id="e4d15-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="e4d15-108">[ToBoolean （Byte\[\]，Int32）](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="e4d15-109">[ToChar （Byte\[\]，Int32）](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="e4d15-110">[ToDouble （Byte\[\]，Int32）](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="e4d15-111">[ToInt16 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="e4d15-112">[ToInt32 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="e4d15-113">[ToInt64 （Byte\[\]，Int32）](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="e4d15-114">[ToSingle （Byte\[\]，Int32）](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="e4d15-115">[ToUInt16 （Byte\[\]，Int32）](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="e4d15-116">[ToUInt32 （Byte\[\]，Int32）](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="e4d15-117">[ToUInt64 （Byte\[\]，Int32）](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e4d15-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="e4d15-118">範例</span><span class="sxs-lookup"><span data-stu-id="e4d15-118">Example</span></span>

<span data-ttu-id="e4d15-119">這個範例會初始化位元組的陣列，如果電腦架構是以小序（也就是第一次儲存最不重要的位元組），則會反轉陣列，然後呼叫[ToInt32 （byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法來轉換四個位元組在 `int`的陣列中。</span><span class="sxs-lookup"><span data-stu-id="e4d15-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="e4d15-120">ToInt32 的第二個引數[（Byte\[\]，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))會指定位元組陣列的開始索引。</span><span class="sxs-lookup"><span data-stu-id="e4d15-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="e4d15-121">輸出可能會根據您電腦架構的「位元組順序」而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e4d15-121">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="e4d15-122">範例</span><span class="sxs-lookup"><span data-stu-id="e4d15-122">Example</span></span>

<span data-ttu-id="e4d15-123">在此範例中，會呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法，將 `int` 轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="e4d15-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="e4d15-124">輸出可能會根據您電腦架構的「位元組順序」而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e4d15-124">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="e4d15-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4d15-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="e4d15-126">型別</span><span class="sxs-lookup"><span data-stu-id="e4d15-126">Types</span></span>](./index.md)
