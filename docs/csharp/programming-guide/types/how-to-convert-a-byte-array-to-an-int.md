---
title: "如何：將位元組陣列轉換成整數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2d26bb4821e09c6633d1c5a4dd40e132e57acf94
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="c7b49-102">如何：將位元組陣列轉換成整數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c7b49-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="c7b49-103">本例示範如何使用 <xref:System.BitConverter> 類別將位元組陣列轉換成 [int](../../../csharp/language-reference/keywords/int.md)，再回復成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c7b49-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="c7b49-104">例如，在讀取網路位元組後，您可能必須從位元組轉換成內建資料類型。</span><span class="sxs-lookup"><span data-stu-id="c7b49-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="c7b49-105">除了範例中的 [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) 方法外，下表會列出 <xref:System.BitConverter> 類別中可將位元組轉換成其他內建類型的方法。</span><span class="sxs-lookup"><span data-stu-id="c7b49-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="c7b49-106">傳回的類型</span><span class="sxs-lookup"><span data-stu-id="c7b49-106">Type returned</span></span>|<span data-ttu-id="c7b49-107">方法</span><span class="sxs-lookup"><span data-stu-id="c7b49-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="c7b49-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="c7b49-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="c7b49-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="c7b49-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="c7b49-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="c7b49-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="c7b49-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="c7b49-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="c7b49-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="c7b49-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c7b49-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7b49-118">範例</span><span class="sxs-lookup"><span data-stu-id="c7b49-118">Example</span></span>  
 <span data-ttu-id="c7b49-119">本例會初始化位元組陣列，如果電腦是位元組由小到大的架構則反轉陣列 (也就是先儲存最低位元組)，然後呼叫 [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) 方法，將陣列中的四個位元組轉換成 `int`。</span><span class="sxs-lookup"><span data-stu-id="c7b49-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="c7b49-120">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) 的第二個引數指定位元組陣列的起始索引。</span><span class="sxs-lookup"><span data-stu-id="c7b49-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7b49-121">輸出會隨電腦架構位元組由大到小或由小到大而有所不同。</span><span class="sxs-lookup"><span data-stu-id="c7b49-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 <span data-ttu-id="c7b49-122">[!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c7b49-122">[!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7b49-123">範例</span><span class="sxs-lookup"><span data-stu-id="c7b49-123">Example</span></span>  
 <span data-ttu-id="c7b49-124">在本例中，呼叫 <xref:System.BitConverter> 類別的 <xref:System.BitConverter.GetBytes%28System.Int32%29> 方法將 `int` 轉換成位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c7b49-124">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7b49-125">輸出會隨電腦架構位元組由大到小或由小到大而有所不同。</span><span class="sxs-lookup"><span data-stu-id="c7b49-125">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 <span data-ttu-id="c7b49-126">[!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c7b49-126">[!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b49-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7b49-127">See Also</span></span>  
 <span data-ttu-id="c7b49-128"><xref:System.BitConverter></span><span class="sxs-lookup"><span data-stu-id="c7b49-128"><xref:System.BitConverter></span></span>   
 <span data-ttu-id="c7b49-129"><xref:System.BitConverter.IsLittleEndian></span><span class="sxs-lookup"><span data-stu-id="c7b49-129"><xref:System.BitConverter.IsLittleEndian></span></span>   
<span data-ttu-id="c7b49-130"> [型別](../../../csharp/programming-guide/types/index.md)</span><span class="sxs-lookup"><span data-stu-id="c7b49-130"> [Types](../../../csharp/programming-guide/types/index.md)</span></span>

