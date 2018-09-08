---
title: 如何：使用 DateTimePicker 控制項顯示時間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: c65a1102ccb8b05602d813831745dbcefed8c17d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131905"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="b0ac8-102">如何：使用 DateTimePicker 控制項顯示時間</span><span class="sxs-lookup"><span data-stu-id="b0ac8-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="b0ac8-103">如果您希望應用程式可讓使用者選取日期和時間，並在指定的格式中顯示該日期和時間，請使用 <xref:System.Windows.Forms.DateTimePicker> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="b0ac8-104">下列程序示範如何使用 <xref:System.Windows.Forms.DateTimePicker> 控制項來顯示時間。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="b0ac8-105">使用 DateTimePicker 控制項顯示時間</span><span class="sxs-lookup"><span data-stu-id="b0ac8-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="b0ac8-106">將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定為 <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="b0ac8-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="b0ac8-107">將 <xref:System.Windows.Forms.DateTimePicker> 的 <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b0ac8-108">範例</span><span class="sxs-lookup"><span data-stu-id="b0ac8-108">Example</span></span>  
 <span data-ttu-id="b0ac8-109">下列程式碼範例示範如何建立 <xref:System.Windows.Forms.DateTimePicker>，可讓使用者僅能選擇一個時間。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b0ac8-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b0ac8-110">Compiling the Code</span></span>  
 <span data-ttu-id="b0ac8-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b0ac8-111">This example requires:</span></span>  
  
-   <span data-ttu-id="b0ac8-112">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b0ac8-113">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b0ac8-114">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b0ac8-115">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="b0ac8-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ac8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0ac8-116">See Also</span></span>  
 [<span data-ttu-id="b0ac8-117">DateTimePicker 控制項</span><span class="sxs-lookup"><span data-stu-id="b0ac8-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
