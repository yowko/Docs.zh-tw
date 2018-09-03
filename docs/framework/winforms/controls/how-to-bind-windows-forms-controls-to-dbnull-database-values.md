---
title: 如何：將 Windows Forms 控制項繫結至 DBNull 資料庫數值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 278fd4ed0622673a49bfaa2567501b832bd535d3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469956"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="1b844-102">如何：將 Windows Forms 控制項繫結至 DBNull 資料庫數值</span><span class="sxs-lookup"><span data-stu-id="1b844-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="1b844-103">當您將 Windows Form 控制項繫結至資料來源，且資料來源傳回 <xref:System.DBNull> 值時，您可以替代為適當值，而不需處理、格式化或剖析事件。</span><span class="sxs-lookup"><span data-stu-id="1b844-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="1b844-104">在格式化或剖析資料來源值的時候，<xref:System.Windows.Forms.Binding.NullValue%2A> 屬性會轉換 <xref:System.DBNull> 為指定的物件。</span><span class="sxs-lookup"><span data-stu-id="1b844-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b844-105">範例</span><span class="sxs-lookup"><span data-stu-id="1b844-105">Example</span></span>  
 <span data-ttu-id="1b844-106">下列範例示範如何在兩個不同的情況下繫結 <xref:System.DBNull> 的值。</span><span class="sxs-lookup"><span data-stu-id="1b844-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="1b844-107">第一個範例示範如何為字串屬性設定 <xref:System.Windows.Forms.Binding.NullValue%2A>；第二個示範如何為影像屬性設定 <xref:System.Windows.Forms.Binding.NullValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="1b844-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="1b844-108">繫結屬性和 <xref:System.Windows.Forms.Binding.NullValue%2A> 屬性的類型都必須相同，否則會產生錯誤，將不會再進一步處理 <xref:System.Windows.Forms.Binding.NullValue%2A> 的值。</span><span class="sxs-lookup"><span data-stu-id="1b844-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="1b844-109">在此情況下，將不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1b844-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b844-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1b844-110">Compiling the Code</span></span>  
 <span data-ttu-id="1b844-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1b844-111">This example requires:</span></span>  
  
-   <span data-ttu-id="1b844-112">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1b844-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1b844-113">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1b844-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1b844-114">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1b844-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1b844-115">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="1b844-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b844-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b844-116">See Also</span></span>  
 [<span data-ttu-id="1b844-117">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="1b844-117">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="1b844-118">操作說明：處理資料繫結時所發生的錯誤和例外狀況</span><span class="sxs-lookup"><span data-stu-id="1b844-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [<span data-ttu-id="1b844-119">操作說明：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="1b844-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
