---
title: "如何：以前置字元零來填補數字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="6b28b-102">如何：以前置字元零來填補數字</span><span class="sxs-lookup"><span data-stu-id="6b28b-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="6b28b-103">如果整數要加上前置零，您可以使用具有精確度規範的 "D" [標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="6b28b-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="6b28b-104">如果整數和浮點數都要加上前置零，您可以使用[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="6b28b-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="6b28b-105">此主題示範如何使用這兩種方法，以前置零填補數值。</span><span class="sxs-lookup"><span data-stu-id="6b28b-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="6b28b-106">以前置零將整數填補至特定長度</span><span class="sxs-lookup"><span data-stu-id="6b28b-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="6b28b-107">決定您要整數值顯示的位數下限。</span><span class="sxs-lookup"><span data-stu-id="6b28b-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="6b28b-108">在此數值中包含任何前置數。</span><span class="sxs-lookup"><span data-stu-id="6b28b-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="6b28b-109">決定要將整數顯示為十進位值或十六進位值。</span><span class="sxs-lookup"><span data-stu-id="6b28b-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="6b28b-110">若要將整數顯示為十進位值，呼叫其`ToString(String)`方法，然後傳遞字串"D*n*"的值為`format`參數，其中 *n* 代表字串的最小長度。</span><span class="sxs-lookup"><span data-stu-id="6b28b-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="6b28b-111">若要將整數顯示為十六進位值，呼叫其`ToString(String)`方法並傳遞字串"X*n*"的值為`format`參數，其中 *n* 代表字串的最小長度。</span><span class="sxs-lookup"><span data-stu-id="6b28b-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="6b28b-112">您也可以使用格式字串中的方法，例如<xref:System.String.Format%2A>或<xref:System.Console.WriteLine%2A>，使用[複合格式化](../../../docs/standard/base-types/composite-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="6b28b-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="6b28b-113">下列範例會使用前置零來將數個整數值格式化，讓格式化數值的總長度至少為 8 個字元。</span><span class="sxs-lookup"><span data-stu-id="6b28b-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="6b28b-114">以特定數目的前置零填補整數</span><span class="sxs-lookup"><span data-stu-id="6b28b-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="6b28b-115">決定您想要讓整數值顯示多少個前置零。</span><span class="sxs-lookup"><span data-stu-id="6b28b-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="6b28b-116">決定要將整數顯示為十進位值或十六進位值。</span><span class="sxs-lookup"><span data-stu-id="6b28b-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="6b28b-117">若要將其格式化為十進位值，您需要使用 "D" 標準格式規範；若要將其格式化為十六進位值，您需要使用 "X" 標準格式規範。</span><span class="sxs-lookup"><span data-stu-id="6b28b-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="6b28b-118">呼叫整數值的 `ToString("D").Length` 或 `ToString("X").Length` 方法，以決定未填補之數值字串的長度。</span><span class="sxs-lookup"><span data-stu-id="6b28b-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="6b28b-119">將您想要包含在格式化字串中的前置零個數，加入至未填補之數值字串的長度。</span><span class="sxs-lookup"><span data-stu-id="6b28b-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="6b28b-120">這會定義填補字串的總長度。</span><span class="sxs-lookup"><span data-stu-id="6b28b-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="6b28b-121">呼叫整數值的`ToString(String)`方法，然後傳遞字串"D*n*」 針對十進位字串和"X*n*"十六進位字串，其中 *n*代表填補字串的總長度。</span><span class="sxs-lookup"><span data-stu-id="6b28b-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="6b28b-122">您也可以使用"D*n*"或"X*n*"格式字串中可支援複合格式方法。</span><span class="sxs-lookup"><span data-stu-id="6b28b-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="6b28b-123">下列範例會以五個前置零填補整數值。</span><span class="sxs-lookup"><span data-stu-id="6b28b-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="6b28b-124">以前置零將數值填補至特定長度</span><span class="sxs-lookup"><span data-stu-id="6b28b-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="6b28b-125">決定您想要讓數值字串表示式的小數點左邊有幾位數。</span><span class="sxs-lookup"><span data-stu-id="6b28b-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="6b28b-126">在這個總位數中包含任何前置零。</span><span class="sxs-lookup"><span data-stu-id="6b28b-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="6b28b-127">定義自訂數值格式字串，使用零預留位置 ("0") 來表示零的數目下限。</span><span class="sxs-lookup"><span data-stu-id="6b28b-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="6b28b-128">呼叫數值的 `ToString(String)` 方法，並將其傳遞至自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="6b28b-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="6b28b-129">您也可以將自訂格式字串與支援複合格式的方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6b28b-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="6b28b-130">下列範例會使用前置零來將數個數值格式化，讓格式化數值的小數點左邊至少有 8 位數。</span><span class="sxs-lookup"><span data-stu-id="6b28b-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="6b28b-131">以特定數目的前置零填補數值</span><span class="sxs-lookup"><span data-stu-id="6b28b-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="6b28b-132">決定您想要讓數值有多少個前置零。</span><span class="sxs-lookup"><span data-stu-id="6b28b-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="6b28b-133">決定未填補之數值字串的小數點左邊有幾位數。</span><span class="sxs-lookup"><span data-stu-id="6b28b-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="6b28b-134">做法：</span><span class="sxs-lookup"><span data-stu-id="6b28b-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="6b28b-135">決定數值字串表示法是否包含小數點符號。</span><span class="sxs-lookup"><span data-stu-id="6b28b-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="6b28b-136">如果包含小數點符號，則要決定小數點左邊的字元數。</span><span class="sxs-lookup"><span data-stu-id="6b28b-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="6b28b-137">-或-</span><span class="sxs-lookup"><span data-stu-id="6b28b-137">-or-</span></span>  
  
         <span data-ttu-id="6b28b-138">如果不包含小數點符號，則要決定字串長度。</span><span class="sxs-lookup"><span data-stu-id="6b28b-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="6b28b-139">建立自訂格式字串，使用零預留位置 ("0")，讓每個前置零出現在字串中，並使用零預留位置或數字預留位置 ("#") 來代表預設字串中的每個數字。</span><span class="sxs-lookup"><span data-stu-id="6b28b-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="6b28b-140">提供自訂格式字串，以做為數值之 `ToString(String)` 方法或支援複合格式之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="6b28b-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="6b28b-141">下列範例會以五個前置零填補兩個 <xref:System.Double> 值。</span><span class="sxs-lookup"><span data-stu-id="6b28b-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6b28b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b28b-142">See Also</span></span>  
 [<span data-ttu-id="6b28b-143">Custom Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="6b28b-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [<span data-ttu-id="6b28b-144">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="6b28b-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="6b28b-145">複合格式</span><span class="sxs-lookup"><span data-stu-id="6b28b-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
