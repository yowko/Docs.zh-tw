---
title: HOW TO：使用 DateTimePicker 控制項顯示時間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: f1c1a0abaeddadb44b40d56eb2f8a28e4b58f4f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651775"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="53e82-102">HOW TO：使用 DateTimePicker 控制項顯示時間</span><span class="sxs-lookup"><span data-stu-id="53e82-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="53e82-103">如果您希望應用程式可讓使用者選取日期和時間，並在指定的格式中顯示該日期和時間，請使用 <xref:System.Windows.Forms.DateTimePicker> 控制項。</span><span class="sxs-lookup"><span data-stu-id="53e82-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="53e82-104">下列程序示範如何使用 <xref:System.Windows.Forms.DateTimePicker> 控制項來顯示時間。</span><span class="sxs-lookup"><span data-stu-id="53e82-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="53e82-105">使用 DateTimePicker 控制項顯示時間</span><span class="sxs-lookup"><span data-stu-id="53e82-105">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="53e82-106">將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定為 <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="53e82-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="53e82-107">將 <xref:System.Windows.Forms.DateTimePicker> 的 <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="53e82-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="53e82-108">範例</span><span class="sxs-lookup"><span data-stu-id="53e82-108">Example</span></span>  
 <span data-ttu-id="53e82-109">下列程式碼範例示範如何建立 <xref:System.Windows.Forms.DateTimePicker>，可讓使用者僅能選擇一個時間。</span><span class="sxs-lookup"><span data-stu-id="53e82-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="53e82-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="53e82-110">Compiling the Code</span></span>  
 <span data-ttu-id="53e82-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="53e82-111">This example requires:</span></span>  
  
- <span data-ttu-id="53e82-112">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="53e82-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="53e82-113">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="53e82-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="53e82-114">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="53e82-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e82-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53e82-115">See also</span></span>

- [<span data-ttu-id="53e82-116">DateTimePicker 控制項</span><span class="sxs-lookup"><span data-stu-id="53e82-116">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
