---
title: "如何：在日期與時間值中顯示毫秒"
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
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a><span data-ttu-id="cd76f-102">如何：在日期與時間值中顯示毫秒</span><span class="sxs-lookup"><span data-stu-id="cd76f-102">How to: Display Milliseconds in Date and Time Values</span></span>
<span data-ttu-id="cd76f-103">預設的日期和時間格式化方法，例如<xref:System.DateTime.ToString?displayProperty=nameWithType>，包含小時、 分鐘和秒的時間值，但排除其毫秒元件。</span><span class="sxs-lookup"><span data-stu-id="cd76f-103">The default date and time formatting methods, such as <xref:System.DateTime.ToString?displayProperty=nameWithType>, include the hours, minutes, and seconds of a time value but exclude its milliseconds component.</span></span> <span data-ttu-id="cd76f-104">本主題說明如何將日期和時間的毫秒部分加入格式化的日期和時間字串。</span><span class="sxs-lookup"><span data-stu-id="cd76f-104">This topic shows how to include a date and time's millisecond component in formatted date and time strings.</span></span>  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a><span data-ttu-id="cd76f-105">顯示 DateTime 值的毫秒部分</span><span class="sxs-lookup"><span data-stu-id="cd76f-105">To display the millisecond component of a DateTime value</span></span>  
  
1.  <span data-ttu-id="cd76f-106">如果您要處理日期的字串表示法，請使用靜態 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 方法，將其轉換成 <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 或 <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="cd76f-106">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="cd76f-107">要擷取的字串表示時間的毫秒元件，請呼叫日期和時間值的<xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>或<xref:System.DateTimeOffset.ToString%2A>方法，然後傳遞`fff`或`FFF`單獨或與其他自訂格式的自訂格式模式規範為`format`參數。</span><span class="sxs-lookup"><span data-stu-id="cd76f-107">To extract the string representation of a time's millisecond component, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%2A> method, and pass the `fff` or `FFF` custom format pattern either alone or with other custom format specifiers as the `format` parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd76f-108">範例</span><span class="sxs-lookup"><span data-stu-id="cd76f-108">Example</span></span>  
 <span data-ttu-id="cd76f-109">此範例會顯示的毫秒數元件<xref:System.DateTime>和<xref:System.DateTimeOffset>主控台中，單獨和包含在較長的日期和時間字串的值。</span><span class="sxs-lookup"><span data-stu-id="cd76f-109">The example displays the millisecond component of a <xref:System.DateTime> and a <xref:System.DateTimeOffset> value to the console, both alone and included in a longer date and time string.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 <span data-ttu-id="cd76f-110">`fff` 格式模式會包含毫秒值尾端的任何零。</span><span class="sxs-lookup"><span data-stu-id="cd76f-110">The `fff` format pattern includes any trailing zeros in the millisecond value.</span></span> <span data-ttu-id="cd76f-111">`FFF` 格式模式則會加以隱藏。</span><span class="sxs-lookup"><span data-stu-id="cd76f-111">The `FFF` format pattern suppresses them.</span></span> <span data-ttu-id="cd76f-112">下列範例會說明其間的差異。</span><span class="sxs-lookup"><span data-stu-id="cd76f-112">The difference is illustrated in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 <span data-ttu-id="cd76f-113">定義包含日期和時間毫秒部分之完整自訂格式規範的問題在於，它會定義硬式編碼格式，而該格式可能不會對應至應用程式目前文化特性中時間項目的排列。</span><span class="sxs-lookup"><span data-stu-id="cd76f-113">A problem with defining a complete custom format specifier that includes the millisecond component of a date and time is that it defines a hard-coded format that may not correspond to the arrangement of time elements in the application's current culture.</span></span> <span data-ttu-id="cd76f-114">較佳替代方式是擷取一個日期和時間顯示目前的文化特性所定義的模式<xref:System.Globalization.DateTimeFormatInfo>物件，並將它修改為包含毫秒。</span><span class="sxs-lookup"><span data-stu-id="cd76f-114">A better alternative is to retrieve one of the date and time display patterns defined by the current culture's <xref:System.Globalization.DateTimeFormatInfo> object and modify it to include milliseconds.</span></span> <span data-ttu-id="cd76f-115">此範例也會說明這個方法。</span><span class="sxs-lookup"><span data-stu-id="cd76f-115">The example also illustrates this approach.</span></span> <span data-ttu-id="cd76f-116">它會擷取目前文化特性的完整日期和時間模式從<xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType>屬性，然後將自訂模式`.ffff`其秒模式。</span><span class="sxs-lookup"><span data-stu-id="cd76f-116">It retrieves the current culture's full date and time pattern from the <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> property, and then inserts the custom pattern `.ffff` after its seconds pattern.</span></span> <span data-ttu-id="cd76f-117">請注意，此範例使用規則運算式，以單一方法呼叫來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="cd76f-117">Note that the example uses a regular expression to perform this operation in a single method call.</span></span>  
  
 <span data-ttu-id="cd76f-118">除了毫秒之外，您也可以使用自訂格式規範顯示秒的其他小數部分。</span><span class="sxs-lookup"><span data-stu-id="cd76f-118">You can also use a custom format specifier to display a fractional part of seconds other than milliseconds.</span></span> <span data-ttu-id="cd76f-119">例如，`f` 或 `F` 自訂格式規範會顯示十分之一秒，`ff` 或 `FF` 自訂格式規範會顯示百分之一秒，而 `ffff` 或 `FFFF` 自訂格式規範會顯示萬分之一秒。</span><span class="sxs-lookup"><span data-stu-id="cd76f-119">For example, the `f` or `F` custom format specifier displays tenths of a second, the `ff` or `FF` custom format specifier displays hundredths of a second, and the `ffff` or `FFFF` custom format specifier displays ten thousandths of a second.</span></span> <span data-ttu-id="cd76f-120">毫秒的小數部分會在傳回的字串中被截斷，而不是四捨五入。</span><span class="sxs-lookup"><span data-stu-id="cd76f-120">Fractional parts of a millisecond are truncated instead of rounded in the returned string.</span></span> <span data-ttu-id="cd76f-121">下列範例會使用這些格式規範。</span><span class="sxs-lookup"><span data-stu-id="cd76f-121">These format specifiers are used in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="cd76f-122">您可以使用非常小的小數單位來顯示秒，例如萬分之一秒或十萬分之一秒。</span><span class="sxs-lookup"><span data-stu-id="cd76f-122">It is possible to display very small fractional units of a second, such as ten thousandths of a second or hundred-thousandths of a second.</span></span> <span data-ttu-id="cd76f-123">不過，這些值可能沒有太大的意義。</span><span class="sxs-lookup"><span data-stu-id="cd76f-123">However, these values may not be meaningful.</span></span> <span data-ttu-id="cd76f-124">日期和時間值的精確度會根據系統時鐘的解析度而定。</span><span class="sxs-lookup"><span data-stu-id="cd76f-124">The precision of date and time values depends on the resolution of the system clock.</span></span> <span data-ttu-id="cd76f-125">在 Windows NT 3.5 版和更新版本，和[!INCLUDE[windowsver](../../../includes/windowsver-md.md)]作業系統，時鐘的解析度會大約為 10-15 毫秒。</span><span class="sxs-lookup"><span data-stu-id="cd76f-125">On Windows NT 3.5 and later, and [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] operating systems, the clock's resolution is approximately 10-15 milliseconds.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd76f-126">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="cd76f-126">Compiling the Code</span></span>  
 <span data-ttu-id="cd76f-127">在命令列使用 csc.exe 或 vb.exe 程式碼編譯。</span><span class="sxs-lookup"><span data-stu-id="cd76f-127">Compile the code at the command line using csc.exe or vb.exe.</span></span> <span data-ttu-id="cd76f-128">若要編譯中的程式碼[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，將其放在主控台應用程式專案範本。</span><span class="sxs-lookup"><span data-stu-id="cd76f-128">To compile the code in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], put it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd76f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd76f-129">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="cd76f-130">Custom Date and Time Format Strings</span><span class="sxs-lookup"><span data-stu-id="cd76f-130">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
