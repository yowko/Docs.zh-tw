---
title: 作法：使用 DateTimePicker 控制項顯示時間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: 84f10540e7735ac1043e63eecda84161c10deeef
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591727"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="7d53f-102">作法：使用 DateTimePicker 控制項顯示時間</span><span class="sxs-lookup"><span data-stu-id="7d53f-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="7d53f-103">如果您希望應用程式可讓使用者選取日期和時間，並在指定的格式中顯示該日期和時間，請使用 <xref:System.Windows.Forms.DateTimePicker> 控制項。</span><span class="sxs-lookup"><span data-stu-id="7d53f-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="7d53f-104">下列程序示範如何使用 <xref:System.Windows.Forms.DateTimePicker> 控制項來顯示時間。</span><span class="sxs-lookup"><span data-stu-id="7d53f-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="7d53f-105">使用 DateTimePicker 控制項顯示時間</span><span class="sxs-lookup"><span data-stu-id="7d53f-105">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="7d53f-106">將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定為 <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="7d53f-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="7d53f-107">將 <xref:System.Windows.Forms.DateTimePicker> 的 <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7d53f-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="7d53f-108">範例</span><span class="sxs-lookup"><span data-stu-id="7d53f-108">Example</span></span>  
 <span data-ttu-id="7d53f-109">下列程式碼範例示範如何建立 <xref:System.Windows.Forms.DateTimePicker>，可讓使用者僅能選擇一個時間。</span><span class="sxs-lookup"><span data-stu-id="7d53f-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d53f-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="7d53f-110">Compiling the Code</span></span>  
 <span data-ttu-id="7d53f-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="7d53f-111">This example requires:</span></span>  
  
- <span data-ttu-id="7d53f-112">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="7d53f-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d53f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d53f-113">See also</span></span>

- [<span data-ttu-id="7d53f-114">DateTimePicker 控制項</span><span class="sxs-lookup"><span data-stu-id="7d53f-114">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
