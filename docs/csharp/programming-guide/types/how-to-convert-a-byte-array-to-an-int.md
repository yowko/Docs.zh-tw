---
title: 作法：將位元組陣列轉換成整數 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 82ed87bbcbc741695afc49069c413ae440bd147b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423546"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="060e9-102">作法：將位元組陣列轉換成整數 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="060e9-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="060e9-103">本例示範如何使用 <xref:System.BitConverter> 類別將位元組陣列轉換成 [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)，再回復成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="060e9-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="060e9-104">例如，在讀取網路位元組後，您可能必須從位元組轉換成內建資料類型。</span><span class="sxs-lookup"><span data-stu-id="060e9-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="060e9-105">除了範例中的 [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) 方法外，下表會列出 <xref:System.BitConverter> 類別中可將位元組轉換成其他內建類型的方法。</span><span class="sxs-lookup"><span data-stu-id="060e9-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="060e9-106">傳回的類型</span><span class="sxs-lookup"><span data-stu-id="060e9-106">Type returned</span></span>|<span data-ttu-id="060e9-107">方法</span><span class="sxs-lookup"><span data-stu-id="060e9-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="060e9-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="060e9-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="060e9-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="060e9-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="060e9-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="060e9-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="060e9-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="060e9-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="060e9-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="060e9-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="060e9-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="060e9-118">範例</span><span class="sxs-lookup"><span data-stu-id="060e9-118">Example</span></span>  
 <span data-ttu-id="060e9-119">本例會初始化位元組陣列，如果電腦是位元組由小到大的架構則反轉陣列 (也就是先儲存最低位元組)，然後呼叫 [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) 方法，將陣列中的四個位元組轉換成 `int`。</span><span class="sxs-lookup"><span data-stu-id="060e9-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="060e9-120">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) 的第二個引數指定位元組陣列的起始索引。</span><span class="sxs-lookup"><span data-stu-id="060e9-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="060e9-121">輸出會隨電腦架構位元組由大到小或由小到大而有所不同。</span><span class="sxs-lookup"><span data-stu-id="060e9-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a><span data-ttu-id="060e9-122">範例</span><span class="sxs-lookup"><span data-stu-id="060e9-122">Example</span></span>  
 <span data-ttu-id="060e9-123">在此範例中，會呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法，將 `int` 轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="060e9-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="060e9-124">輸出會隨電腦架構位元組由大到小或由小到大而有所不同。</span><span class="sxs-lookup"><span data-stu-id="060e9-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a><span data-ttu-id="060e9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="060e9-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="060e9-126">型別</span><span class="sxs-lookup"><span data-stu-id="060e9-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
