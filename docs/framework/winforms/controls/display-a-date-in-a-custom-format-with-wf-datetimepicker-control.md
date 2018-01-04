---
title: "如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5f5c7d856991ae8e0bf7caff656bf7010255628
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="912ba-102">如何：使用 Windows Form DateTimePicker 控制項顯示自訂格式的日期</span><span class="sxs-lookup"><span data-stu-id="912ba-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="912ba-103">Windows Form<xref:System.Windows.Forms.DateTimePicker>控制項可讓您格式化的日期和時間在控制項中的顯示的彈性。</span><span class="sxs-lookup"><span data-stu-id="912ba-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="912ba-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A>屬性可讓您從預先定義的格式，清單中選取<xref:System.Windows.Forms.DateTimePickerFormat>。</span><span class="sxs-lookup"><span data-stu-id="912ba-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="912ba-105">其中一個項目是否適合您的目的，您可以建立您自己使用中所列的格式字元的格式樣式<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>。</span><span class="sxs-lookup"><span data-stu-id="912ba-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="912ba-106">若要顯示的自訂格式</span><span class="sxs-lookup"><span data-stu-id="912ba-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="912ba-107">將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定為 `DateTimePickerFormat.Custom`。</span><span class="sxs-lookup"><span data-stu-id="912ba-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="912ba-108">設定<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>屬性設為格式字串。</span><span class="sxs-lookup"><span data-stu-id="912ba-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="912ba-109">將文字加入格式化的值</span><span class="sxs-lookup"><span data-stu-id="912ba-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="912ba-110">使用單引號來括住格式字元，例如"M"或類似的分隔符號不是任何字元":"。</span><span class="sxs-lookup"><span data-stu-id="912ba-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="912ba-111">例如，下列的格式字串會顯示目前的日期格式 」 現在是： 05:30:31 星期五 2012 年 3 月 02，「 英文 （美國） 文化特性。</span><span class="sxs-lookup"><span data-stu-id="912ba-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="912ba-112">根據文化特性設定，可能會變更任何不在單引號中的字元。</span><span class="sxs-lookup"><span data-stu-id="912ba-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="912ba-113">例如，上述的格式字串會顯示目前的日期格式 」 現在： 05:30:31 星期五 2012 年 3 月 02，「 英文 （美國） 文化特性。</span><span class="sxs-lookup"><span data-stu-id="912ba-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="912ba-114">請注意第一個冒號會括在單引號中，因為它不是分隔字元，因為它是"ss"。</span><span class="sxs-lookup"><span data-stu-id="912ba-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="912ba-115">另一個文化特性中，格式可能會顯示為 「 目前是： 05.30.31 2012 年 3 月 02 日星期五"。</span><span class="sxs-lookup"><span data-stu-id="912ba-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912ba-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="912ba-116">See Also</span></span>  
 [<span data-ttu-id="912ba-117">DateTimePicker 控制項</span><span class="sxs-lookup"><span data-stu-id="912ba-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="912ba-118">操作說明：使用 Windows Forms DateTimePicker 控制項設定和傳回日期</span><span class="sxs-lookup"><span data-stu-id="912ba-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
