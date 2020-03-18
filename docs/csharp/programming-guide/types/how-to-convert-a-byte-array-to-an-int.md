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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="3000b-102">如何將位元組陣列轉換為 int（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="3000b-102">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="3000b-103">本例示範如何使用 <xref:System.BitConverter> 類別將位元組陣列轉換成 [int](../../language-reference/builtin-types/integral-numeric-types.md)，再回復成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3000b-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="3000b-104">例如，在讀取網路位元組後，您可能必須從位元組轉換成內建資料類型。</span><span class="sxs-lookup"><span data-stu-id="3000b-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="3000b-105">除了示例中的[ToInt32（位元組\[\]、 Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法外，下表還列出了<xref:System.BitConverter>類中將位元組（從位元組陣列）轉換為其他內置類型的方法。</span><span class="sxs-lookup"><span data-stu-id="3000b-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="3000b-106">傳回的類型</span><span class="sxs-lookup"><span data-stu-id="3000b-106">Type returned</span></span>|<span data-ttu-id="3000b-107">方法</span><span class="sxs-lookup"><span data-stu-id="3000b-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="3000b-108">[托布利安（位元組\[\]，Int32）](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="3000b-109">[托查爾（位元組\[\]， Int32）](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="3000b-110">[到雙（位元組\[\]， Int32）](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="3000b-111">[Toint16（位元組\[\]， Int32）](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="3000b-112">[Toint32（位元組\[\]， Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="3000b-113">[Toint64（位元組\[\]， Int32）](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="3000b-114">[到單（位元組\[\]， Int32）](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="3000b-115">[ToUInt16（位元組\[\]，Int32）](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="3000b-116">[ToUInt32（位元組\[\]，Int32）](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="3000b-117">[ToUInt64（位元組\[\]，Int32）](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3000b-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="3000b-118">範例</span><span class="sxs-lookup"><span data-stu-id="3000b-118">Example</span></span>

<span data-ttu-id="3000b-119">此示例初始化位元組陣列，如果電腦體系結構是小位元組（即首先存儲最不重要的位元組），則反轉陣列，然後調用[ToInt32（位元組\[\]， Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法將陣列中的四個`int`位元組轉換為 。</span><span class="sxs-lookup"><span data-stu-id="3000b-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="3000b-120">[ \[ \]ToInt32（位元組，Int32）](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))的第二個參數指定位元組陣列的開始索引。</span><span class="sxs-lookup"><span data-stu-id="3000b-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="3000b-121">輸出可能因電腦體系結構的端性而異。</span><span class="sxs-lookup"><span data-stu-id="3000b-121">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="3000b-122">範例</span><span class="sxs-lookup"><span data-stu-id="3000b-122">Example</span></span>

<span data-ttu-id="3000b-123">在此範例中，會呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法，將 `int` 轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="3000b-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="3000b-124">輸出可能因電腦體系結構的端性而異。</span><span class="sxs-lookup"><span data-stu-id="3000b-124">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="3000b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3000b-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="3000b-126">型別</span><span class="sxs-lookup"><span data-stu-id="3000b-126">Types</span></span>](./index.md)
