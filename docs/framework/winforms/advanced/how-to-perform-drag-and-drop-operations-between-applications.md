---
title: HOW TO：在應用程式之間執行拖放作業
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 9aac3a0efd6359c25a6972f0e0b52dd489ec31db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327525"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="3c03f-102">HOW TO：在應用程式之間執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="3c03f-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="3c03f-103">在應用程式之間執行拖放作業與在應用程式之內啟用這個動作並無不同，只要涉及的兩個應用程式根據 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> 和 <xref:System.Windows.Forms.DragEventArgs.Effect%2A> 屬性之間建立的「合約」表現即可。</span><span class="sxs-lookup"><span data-stu-id="3c03f-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="3c03f-104">在下列程序中，您將使用您建立的 Windows 架構應用程式以及隨附於 Windows 作業系統、用來執行應用程式間拖放作業的 WordPad 文書處理器。</span><span class="sxs-lookup"><span data-stu-id="3c03f-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="3c03f-105">WordPad 具有一組特定的允許拖曳和卸除文字的效果集；您將為其撰寫程式碼的 Windows 架構應用程式將會使用這些效果，如此便可能會成功完成拖放作業。</span><span class="sxs-lookup"><span data-stu-id="3c03f-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="3c03f-106">執行應用程式之間的拖放程序</span><span class="sxs-lookup"><span data-stu-id="3c03f-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1. <span data-ttu-id="3c03f-107">新建 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="3c03f-107">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="3c03f-108">新增 <xref:System.Windows.Forms.TextBox> 控制項至表單。</span><span class="sxs-lookup"><span data-stu-id="3c03f-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3. <span data-ttu-id="3c03f-109">設定 <xref:System.Windows.Forms.TextBox> 控制項以接收已卸除的資料。</span><span class="sxs-lookup"><span data-stu-id="3c03f-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="3c03f-110">如需詳細資訊，請參閱[逐步解說：在 Windows Form 中執行拖放作業](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="3c03f-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4. <span data-ttu-id="3c03f-111">執行 Windows 架構應用程式，並與此同時執行 WordPad。</span><span class="sxs-lookup"><span data-stu-id="3c03f-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="3c03f-112">WordPad 是由允許拖放作業之 Windows 所安裝的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="3c03f-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="3c03f-113">它是藉由按下存取**開始**按鈕、 選取**執行**，然後輸入`WordPad`的文字方塊**執行** 對話方塊中，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="3c03f-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5. <span data-ttu-id="3c03f-114">一旦開啟 WordPad，請於其中輸入文字的字串。</span><span class="sxs-lookup"><span data-stu-id="3c03f-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6. <span data-ttu-id="3c03f-115">使用滑鼠、選取文字，然後再將選取的文字拖曳到 Windows 架構應用程式中的 <xref:System.Windows.Forms.TextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="3c03f-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="3c03f-116">觀察當以滑鼠移過 <xref:System.Windows.Forms.TextBox> 控制項 (然後因此引發 <xref:System.Windows.Forms.Control.DragEnter> 事件)，游標會變更，且您可以卸除選取的文字 <xref:System.Windows.Forms.TextBox> 至控制項。</span><span class="sxs-lookup"><span data-stu-id="3c03f-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="3c03f-117">此外，您可以設定您的 <xref:System.Windows.Forms.TextBox> 控制項，以允許將文字字串拖放到 WordPad。</span><span class="sxs-lookup"><span data-stu-id="3c03f-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="3c03f-118">如需詳細資訊，請參閱[逐步解說：在 Windows Form 中執行拖放作業](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="3c03f-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c03f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c03f-119">See also</span></span>

- [<span data-ttu-id="3c03f-120">如何：將資料加入至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="3c03f-120">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="3c03f-121">如何：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="3c03f-121">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="3c03f-122">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="3c03f-122">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
