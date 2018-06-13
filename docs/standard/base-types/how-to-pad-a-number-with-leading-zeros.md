---
title: 如何：以前置字元零來填補數字
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ce3b59db027ffebf616a035b018629cb7aed30c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569768"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="4b8a4-102">如何：以前置字元零來填補數字</span><span class="sxs-lookup"><span data-stu-id="4b8a4-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="4b8a4-103">如果整數要加上前置零，您可以使用具有精確度規範的 "D" [標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="4b8a4-104">如果整數和浮點數都要加上前置零，您可以使用[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="4b8a4-105">此主題示範如何使用這兩種方法，以前置零填補數值。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4b8a4-106">以前置零將整數填補至特定長度</span><span class="sxs-lookup"><span data-stu-id="4b8a4-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="4b8a4-107">決定您要整數值顯示的位數下限。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="4b8a4-108">在此數值中包含任何前置數。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="4b8a4-109">決定要將整數顯示為十進位值或十六進位值。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="4b8a4-110">若要將整數顯示為十進位值，請呼叫其 `ToString(String)` 方法，然後傳遞字串 "D*n*" 以作為 `format` 參數的值，其中 *n* 代表字串的長度下限。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="4b8a4-111">若要將整數顯示為十六進位值，請呼叫其 `ToString(String)` 方法，然後傳遞字串 "X*n*" 以作為 `format` 參數的值，其中 *n* 代表字串的長度下限。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="4b8a4-112">您也可以在使用[複合格式](../../../docs/standard/base-types/composite-formatting.md)的方法 (例如 <xref:System.String.Format%2A> 或 <xref:System.Console.WriteLine%2A>) 中使用格式字串。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="4b8a4-113">下列範例會使用前置零來將數個整數值格式化，讓格式化數值的總長度至少為 8 個字元。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4b8a4-114">以特定數目的前置零填補整數</span><span class="sxs-lookup"><span data-stu-id="4b8a4-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="4b8a4-115">決定您想要讓整數值顯示多少個前置零。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="4b8a4-116">決定要將整數顯示為十進位值或十六進位值。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="4b8a4-117">若要將其格式化為十進位值，您需要使用 "D" 標準格式規範；若要將其格式化為十六進位值，您需要使用 "X" 標準格式規範。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="4b8a4-118">呼叫整數值的 `ToString("D").Length` 或 `ToString("X").Length` 方法，以決定未填補之數值字串的長度。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="4b8a4-119">將您想要包含在格式化字串中的前置零個數，加入至未填補之數值字串的長度。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="4b8a4-120">這會定義填補字串的總長度。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="4b8a4-121">呼叫整數值的 `ToString(String)` 方法，針對十進位字串，請傳遞字串 "D*n*"，針對十六進位字串，請傳遞 "X*n*"，其中 *n* 代表填補字串的總長度。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="4b8a4-122">您也可以在支援複合格式的方法中，使用 "D*n*" 或 "X*n*" 格式字串。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4b8a4-123">下列範例會以五個前置零填補整數值。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4b8a4-124">以前置零將數值填補至特定長度</span><span class="sxs-lookup"><span data-stu-id="4b8a4-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="4b8a4-125">決定您想要讓數值字串表示式的小數點左邊有幾位數。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="4b8a4-126">在這個總位數中包含任何前置零。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="4b8a4-127">定義自訂數值格式字串，使用零預留位置 ("0") 來表示零的數目下限。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="4b8a4-128">呼叫數值的 `ToString(String)` 方法，並將其傳遞至自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="4b8a4-129">您也可以將自訂格式字串與支援複合格式的方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4b8a4-130">下列範例會使用前置零來將數個數值格式化，讓格式化數值的小數點左邊至少有 8 位數。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4b8a4-131">以特定數目的前置零填補數值</span><span class="sxs-lookup"><span data-stu-id="4b8a4-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="4b8a4-132">決定您想要讓數值有多少個前置零。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="4b8a4-133">決定未填補之數值字串的小數點左邊有幾位數。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="4b8a4-134">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="4b8a4-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="4b8a4-135">決定數值字串表示法是否包含小數點符號。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="4b8a4-136">如果包含小數點符號，則要決定小數點左邊的字元數。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="4b8a4-137">-或-</span><span class="sxs-lookup"><span data-stu-id="4b8a4-137">-or-</span></span>  
  
         <span data-ttu-id="4b8a4-138">如果不包含小數點符號，則要決定字串長度。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="4b8a4-139">建立自訂格式字串，使用零預留位置 ("0")，讓每個前置零出現在字串中，並使用零預留位置或數字預留位置 ("#") 來代表預設字串中的每個數字。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="4b8a4-140">提供自訂格式字串，以做為數值之 `ToString(String)` 方法或支援複合格式之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4b8a4-141">下列範例會以五個前置零填補兩個 <xref:System.Double> 值。</span><span class="sxs-lookup"><span data-stu-id="4b8a4-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4b8a4-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b8a4-142">See Also</span></span>  
 [<span data-ttu-id="4b8a4-143">Custom Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="4b8a4-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [<span data-ttu-id="4b8a4-144">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="4b8a4-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="4b8a4-145">複合格式</span><span class="sxs-lookup"><span data-stu-id="4b8a4-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
