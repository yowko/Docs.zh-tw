---
title: 使用 DateTimePicker 控制項以自訂格式顯示日期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: a27dbe737b81af86c0ac50b791bcd87bafe05b4f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745941"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="eafb7-102">如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期</span><span class="sxs-lookup"><span data-stu-id="eafb7-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="eafb7-103">Windows Forms <xref:System.Windows.Forms.DateTimePicker> 控制項可讓您彈性地在控制項中格式化日期和時間的顯示。</span><span class="sxs-lookup"><span data-stu-id="eafb7-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="eafb7-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性可讓您從 <xref:System.Windows.Forms.DateTimePickerFormat>中所列的預先定義格式進行選取。</span><span class="sxs-lookup"><span data-stu-id="eafb7-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="eafb7-105">如果這些都不適合您的用途，您可以使用 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>中列出的格式字元來建立自己的格式樣式。</span><span class="sxs-lookup"><span data-stu-id="eafb7-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="eafb7-106">若要顯示自訂格式</span><span class="sxs-lookup"><span data-stu-id="eafb7-106">To display a custom format</span></span>  
  
1. <span data-ttu-id="eafb7-107">將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定為 `DateTimePickerFormat.Custom`。</span><span class="sxs-lookup"><span data-stu-id="eafb7-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="eafb7-108">將 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 屬性設定為格式字串。</span><span class="sxs-lookup"><span data-stu-id="eafb7-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="eafb7-109">若要將文字加入至格式化的值</span><span class="sxs-lookup"><span data-stu-id="eafb7-109">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="eafb7-110">使用單引號來括住任何不是格式字元的字元，例如 "M" 或 "：" 之類的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="eafb7-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="eafb7-111">例如，下面的格式字串會以英文（美國）文化特性的格式，顯示目前的日期，其格式為「今天是：05:30:31，2012年3月2日星期五」。</span><span class="sxs-lookup"><span data-stu-id="eafb7-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     <span data-ttu-id="eafb7-112">根據文化特性設定，未以單引號括住的任何字元可能會變更。</span><span class="sxs-lookup"><span data-stu-id="eafb7-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="eafb7-113">例如，上方的格式字串會以英文（美國）文化特性的格式顯示目前的日期，其格式為「今日為：05:30:31，2012年3月2日星期五」。</span><span class="sxs-lookup"><span data-stu-id="eafb7-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="eafb7-114">請注意，第一個冒號是以單引號括住，因為它不適合做為 "hh： mm： ss" 中的分隔字元。</span><span class="sxs-lookup"><span data-stu-id="eafb7-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="eafb7-115">在另一種文化特性中，格式可能會顯示為「今天是：05.30.31 星期五，2012」。</span><span class="sxs-lookup"><span data-stu-id="eafb7-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafb7-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="eafb7-116">See also</span></span>

- [<span data-ttu-id="eafb7-117">DateTimePicker 控制項</span><span class="sxs-lookup"><span data-stu-id="eafb7-117">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="eafb7-118">操作說明：使用 Windows Forms DateTimePicker 控制項設定和傳回日期</span><span class="sxs-lookup"><span data-stu-id="eafb7-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
