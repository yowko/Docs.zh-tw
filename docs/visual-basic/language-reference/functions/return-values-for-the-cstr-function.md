---
title: "CStr 函式的傳回值 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="8ea91-102">CStr 函式的傳回值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea91-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="8ea91-103">下表描述的傳回值`CStr`不同的資料類型的`expression`。</span><span class="sxs-lookup"><span data-stu-id="8ea91-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="8ea91-104">如果`expression`型別</span><span class="sxs-lookup"><span data-stu-id="8ea91-104">If `expression` type is</span></span>|<span data-ttu-id="8ea91-105">`CStr`傳回</span><span class="sxs-lookup"><span data-stu-id="8ea91-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="8ea91-106">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="8ea91-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="8ea91-107">字串，包含"True"或者"False"。</span><span class="sxs-lookup"><span data-stu-id="8ea91-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="8ea91-108">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="8ea91-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="8ea91-109">字串，包含`Date`系統的簡短日期格式的值 （日期和時間）。</span><span class="sxs-lookup"><span data-stu-id="8ea91-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="8ea91-110">數值資料類型</span><span class="sxs-lookup"><span data-stu-id="8ea91-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="8ea91-111">表示數字的字串。</span><span class="sxs-lookup"><span data-stu-id="8ea91-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="8ea91-112">CStr 和日期</span><span class="sxs-lookup"><span data-stu-id="8ea91-112">CStr and Date</span></span>  
 <span data-ttu-id="8ea91-113">`Date`類型一定會包含日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="8ea91-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="8ea91-114">類型轉換的目的而言，Visual Basic 視為 1/1/0001 (1 年的 1 年)*中性值*日期，和 00:00:00 （午夜） 是中性值的時間。</span><span class="sxs-lookup"><span data-stu-id="8ea91-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="8ea91-115">`CStr`不產生的字串中包含相關的值。</span><span class="sxs-lookup"><span data-stu-id="8ea91-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="8ea91-116">例如，如果您要轉換`#January 1, 0001 9:30:00#`為字串，結果會是 「 上午 9:30:00"; 隱藏日期資訊。</span><span class="sxs-lookup"><span data-stu-id="8ea91-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="8ea91-117">不過，將日期資訊是仍會出現在原始`Date`值，並可以復原與函式例如<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>。</span><span class="sxs-lookup"><span data-stu-id="8ea91-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ea91-118">`CStr`函式會執行轉換取決於應用程式的目前文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="8ea91-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="8ea91-119">若要取得特定文化特性中的數字的字串表示，使用數字的`ToString(IFormatProvider)`方法。</span><span class="sxs-lookup"><span data-stu-id="8ea91-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="8ea91-120">例如，使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>轉換類型的值時`Double`至`String`。</span><span class="sxs-lookup"><span data-stu-id="8ea91-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea91-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ea91-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [<span data-ttu-id="8ea91-122">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="8ea91-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="8ea91-123">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="8ea91-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="8ea91-124">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="8ea91-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
