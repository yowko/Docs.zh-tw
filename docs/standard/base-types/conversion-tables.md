---
title: .NET 中的類型轉換表
ms.date: 03/30/2017
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET], type conversions
- data types [.NET], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
ms.openlocfilehash: dc98a326155273805e3157d99755de2e97f83a46
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730210"
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="08e40-102">.NET 中的類型轉換表</span><span class="sxs-lookup"><span data-stu-id="08e40-102">Type Conversion Tables in .NET</span></span>

<span data-ttu-id="08e40-103">將一種類型的值轉換成另一種大小相等或較大類型的值時，就會發生擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="08e40-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="08e40-104">將一種類型的值轉換成另一種大小較小類型的值時，就會發生縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="08e40-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="08e40-105">本主題中的表格將說明這兩種轉換類型的行為。</span><span class="sxs-lookup"><span data-stu-id="08e40-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="08e40-106">擴展轉換</span><span class="sxs-lookup"><span data-stu-id="08e40-106">Widening Conversions</span></span>  

 <span data-ttu-id="08e40-107">下表描述可執行且不會導致資訊遺失的擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="08e40-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="08e40-108">類型</span><span class="sxs-lookup"><span data-stu-id="08e40-108">Type</span></span>|<span data-ttu-id="08e40-109">不會造成資料遺失的可轉換類型</span><span class="sxs-lookup"><span data-stu-id="08e40-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="08e40-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="08e40-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="08e40-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="08e40-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="08e40-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="08e40-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="08e40-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="08e40-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="08e40-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="08e40-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="08e40-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="08e40-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="08e40-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="08e40-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="08e40-117">某些轉換成 <xref:System.Single> 或 <xref:System.Double> 的擴展轉換可能會導致失去精確度。</span><span class="sxs-lookup"><span data-stu-id="08e40-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="08e40-118">下表描述有時會導致資訊遺失的擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="08e40-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="08e40-119">類型</span><span class="sxs-lookup"><span data-stu-id="08e40-119">Type</span></span>|<span data-ttu-id="08e40-120">可轉換類型</span><span class="sxs-lookup"><span data-stu-id="08e40-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="08e40-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="08e40-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="08e40-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="08e40-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="08e40-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="08e40-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="08e40-124">縮小轉換</span><span class="sxs-lookup"><span data-stu-id="08e40-124">Narrowing Conversions</span></span>  

 <span data-ttu-id="08e40-125">某些轉換成 <xref:System.Single> 或 <xref:System.Double> 的縮小轉換可能會導致資訊遺失。</span><span class="sxs-lookup"><span data-stu-id="08e40-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="08e40-126">如果目標類型無法正確表示來源的範圍，產生的類型會設定為常數 `PositiveInfinity` 或 `NegativeInfinity`。</span><span class="sxs-lookup"><span data-stu-id="08e40-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="08e40-127">`PositiveInfinity` 是正數除以零所得的結果；當 <xref:System.Single> 或 <xref:System.Double> 的值超過 `MaxValue` 欄位的值時，也會傳回此值。</span><span class="sxs-lookup"><span data-stu-id="08e40-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="08e40-128">`NegativeInfinity` 是負數除以零所得的結果；當 <xref:System.Single> 或 <xref:System.Double> 的值低於 `MinValue` 欄位的值時，也會傳回此值。</span><span class="sxs-lookup"><span data-stu-id="08e40-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="08e40-129">從 <xref:System.Double> 轉換為 <xref:System.Single> 可能會導致 `PositiveInfinity` 或 `NegativeInfinity`。</span><span class="sxs-lookup"><span data-stu-id="08e40-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="08e40-130">縮小轉換也可能會導致其他資料類型的資訊遺失。</span><span class="sxs-lookup"><span data-stu-id="08e40-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="08e40-131">不過，如果所轉換類型的值超出目標類型的 `MaxValue` 和 `MinValue` 欄位所指定的範圍，而且執行階段已檢查轉換，確定目標類型的值未超過其 `MaxValue` 或 `MinValue`，則會擲回 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="08e40-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="08e40-132">使用 <xref:System.Convert?displayProperty=nameWithType> 類別執行的轉換永遠都會以這種方式進行檢查。</span><span class="sxs-lookup"><span data-stu-id="08e40-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="08e40-133">下表列出使用 <xref:System.Convert?displayProperty=nameWithType> 擲回 <xref:System.OverflowException> 的轉換，或所轉換類型的值超出為產生類型所定義的範圍時的任何已檢查轉換。</span><span class="sxs-lookup"><span data-stu-id="08e40-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="08e40-134">類型</span><span class="sxs-lookup"><span data-stu-id="08e40-134">Type</span></span>|<span data-ttu-id="08e40-135">可轉換類型</span><span class="sxs-lookup"><span data-stu-id="08e40-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="08e40-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="08e40-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="08e40-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="08e40-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="08e40-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="08e40-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="08e40-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="08e40-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="08e40-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="08e40-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="08e40-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="08e40-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="08e40-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="08e40-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="08e40-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="08e40-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="08e40-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="08e40-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="08e40-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="08e40-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08e40-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08e40-146">See also</span></span>

- <xref:System.Convert?displayProperty=nameWithType>
- [<span data-ttu-id="08e40-147">.NET 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="08e40-147">Type Conversion in .NET</span></span>](type-conversion.md)
