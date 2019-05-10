---
title: HOW TO：處理資料繫結發生的錯誤和例外狀況
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: 43e22f34f488f0ec7664587e194c026dedb87824
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651703"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="0b9e7-102">HOW TO：處理資料繫結發生的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="0b9e7-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="0b9e7-103">當您將它們繫結至控制項時，有時候基礎商務物件會發生例外狀況和錯誤。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="0b9e7-104">您可以攔截這些錯誤和例外狀況然後復原，或藉由為特定的 <xref:System.Windows.Forms.Binding> 、 <xref:System.Windows.Forms.BindingSource> 或 <xref:System.Windows.Forms.CurrencyManager> 元件處理 <xref:System.Windows.Forms.Binding.BindingComplete> 事件，將錯誤資訊傳遞給使用者。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b9e7-105">範例</span><span class="sxs-lookup"><span data-stu-id="0b9e7-105">Example</span></span>  
 <span data-ttu-id="0b9e7-106">這個程式碼範例會示範如何處理錯誤以及資料繫結作業期間發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="0b9e7-107">它示範如何藉由處理 <xref:System.Windows.Forms.Binding> 物件中的 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> 事件來攔截錯誤。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="0b9e7-108">若要藉由處理這個事件來攔截錯誤和例外狀況，您必須為繫結啟用格式化。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="0b9e7-109">您可以於繫結被建構或加到繫結集合中時，或藉由設定 <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> 屬性為 `true` 來啟用格式化。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="0b9e7-110">當程式碼正在執行，同時在部分名稱輸入空字串或在部分編號輸入小於 100 的值時，會出現訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="0b9e7-111">這是為了這些文字方塊繫結處理 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> 事件所得到的結果。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b9e7-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0b9e7-112">Compiling the Code</span></span>  
 <span data-ttu-id="0b9e7-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0b9e7-113">This example requires:</span></span>  
  
- <span data-ttu-id="0b9e7-114">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0b9e7-115">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0b9e7-116">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0b9e7-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b9e7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b9e7-117">See also</span></span>

- <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>
- [<span data-ttu-id="0b9e7-118">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="0b9e7-118">BindingSource Component</span></span>](bindingsource-component.md)
