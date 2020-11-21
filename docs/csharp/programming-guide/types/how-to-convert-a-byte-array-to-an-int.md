---
title: '如何將位元組陣列轉換為 int-c # 程式設計指南'
description: 瞭解如何將位元組陣列轉換成整數。請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: a339766313678590cb80263ba5b2ff328c018a58
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099181"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="5903a-103">如何將位元組陣列轉換為 int (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="5903a-103">How to convert a byte array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="5903a-104">本例示範如何使用 <xref:System.BitConverter> 類別將位元組陣列轉換成 [int](../../language-reference/builtin-types/integral-numeric-types.md)，再回復成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="5903a-104">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="5903a-105">例如，在讀取網路位元組後，您可能必須從位元組轉換成內建資料類型。</span><span class="sxs-lookup"><span data-stu-id="5903a-105">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="5903a-106">除了此範例中的[ToInt32 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法，下表列出類別中的方法， <xref:System.BitConverter> 這些方法會將 (位元組從) 位元組陣列轉換為其他內建類型。</span><span class="sxs-lookup"><span data-stu-id="5903a-106">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="5903a-107">傳回的類型</span><span class="sxs-lookup"><span data-stu-id="5903a-107">Type returned</span></span>|<span data-ttu-id="5903a-108">方法</span><span class="sxs-lookup"><span data-stu-id="5903a-108">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="5903a-109">[ToBoolean (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-109">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="5903a-110">[ToChar (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-110">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="5903a-111">[ToDouble (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-111">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="5903a-112">[ToInt16 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-112">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="5903a-113">[ToInt32 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-113">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="5903a-114">[ToInt64 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-114">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="5903a-115">[ToSingle (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-115">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="5903a-116">[ToUInt16 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-116">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="5903a-117">[ToUInt32 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-117">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="5903a-118">[ToUInt64 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="5903a-118">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="5903a-119">範例</span><span class="sxs-lookup"><span data-stu-id="5903a-119">Example</span></span>

<span data-ttu-id="5903a-120">這個範例會初始化位元組陣列，如果電腦架構是位元組由小到大的，則反轉陣列 (也就是最不重要的位元組會先儲存) ，然後再呼叫[ToInt32 (byte \[ \] ，Int32) ](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))方法，將陣列中的四個位元組轉換成 `int` 。</span><span class="sxs-lookup"><span data-stu-id="5903a-120">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="5903a-121">[ToInt32 (Byte \[ \] ，Int32) ](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))的第二個引數會指定位元組陣列的開始索引。</span><span class="sxs-lookup"><span data-stu-id="5903a-121">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="5903a-122">輸出可能會因電腦架構的位元組順序而不同。</span><span class="sxs-lookup"><span data-stu-id="5903a-122">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="5903a-123">範例</span><span class="sxs-lookup"><span data-stu-id="5903a-123">Example</span></span>

<span data-ttu-id="5903a-124">在此範例中，會呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法，將 `int` 轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="5903a-124">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="5903a-125">輸出可能會因電腦架構的位元組順序而不同。</span><span class="sxs-lookup"><span data-stu-id="5903a-125">The output may differ depending on the endianness of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="5903a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5903a-126">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="5903a-127">類型</span><span class="sxs-lookup"><span data-stu-id="5903a-127">Types</span></span>](./index.md)
