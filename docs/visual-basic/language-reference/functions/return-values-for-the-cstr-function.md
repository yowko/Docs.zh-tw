---
title: 傳回 CStr 函式的值
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406379"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="4b443-102">CStr 函式的傳回值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b443-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="4b443-103">下表描述 `CStr` 適用于之不同資料類型的傳回值 `expression` 。</span><span class="sxs-lookup"><span data-stu-id="4b443-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="4b443-104">如果 `expression` 類型為</span><span class="sxs-lookup"><span data-stu-id="4b443-104">If `expression` type is</span></span>|<span data-ttu-id="4b443-105">`CStr` 傳回</span><span class="sxs-lookup"><span data-stu-id="4b443-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="4b443-106">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="4b443-106">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="4b443-107">包含 "True" 或 "False" 的字串。</span><span class="sxs-lookup"><span data-stu-id="4b443-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="4b443-108">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="4b443-108">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="4b443-109">字串 `Date` ，包含您系統的簡短日期格式的值（日期和時間）。</span><span class="sxs-lookup"><span data-stu-id="4b443-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="4b443-110">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="4b443-110">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="4b443-111">表示數位的字串。</span><span class="sxs-lookup"><span data-stu-id="4b443-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="4b443-112">CStr 和 Date</span><span class="sxs-lookup"><span data-stu-id="4b443-112">CStr and Date</span></span>  
 <span data-ttu-id="4b443-113">`Date`類型一律同時包含日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="4b443-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="4b443-114">基於類型轉換的目的，Visual Basic 會將1/1/0001 （第1年1月1日）視為日期的*中性值*，而00:00:00 （午夜）則是時間的中性值。</span><span class="sxs-lookup"><span data-stu-id="4b443-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="4b443-115">`CStr`不會在產生的字串中包含中性值。</span><span class="sxs-lookup"><span data-stu-id="4b443-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="4b443-116">例如，如果您將轉換 `#January 1, 0001 9:30:00#` 成字串，則結果會是 "9:30:00 AM"; 日期資訊會隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="4b443-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="4b443-117">不過，日期資訊仍然會出現在原始值中， `Date` 而且可以使用之類的函數來復原 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4b443-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b443-118">函式會根據 `CStr` 應用程式目前的文化特性設定來執行其轉換。</span><span class="sxs-lookup"><span data-stu-id="4b443-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="4b443-119">若要取得特定文化特性之數位的字串表示，請使用數位的 `ToString(IFormatProvider)` 方法。</span><span class="sxs-lookup"><span data-stu-id="4b443-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="4b443-120">例如，將 <xref:System.Double.ToString%2A?displayProperty=nameWithType> 類型的值轉換為時，請使用 `Double` `String` 。</span><span class="sxs-lookup"><span data-stu-id="4b443-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b443-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b443-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="4b443-122">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="4b443-122">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="4b443-123">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="4b443-123">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="4b443-124">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="4b443-124">Date Data Type</span></span>](../data-types/date-data-type.md)
