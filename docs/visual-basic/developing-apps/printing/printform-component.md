---
title: "PrintForm 元件 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 533b3ee1a0440127c5f18c7a8243afc183f68407
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="printform-component-visual-basic"></a><span data-ttu-id="370fb-102">PrintForm 元件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="370fb-102">PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="370fb-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可讓您在執行階段列印 Windows Form 的影像。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enables you to print an image of a Windows Form at run time.</span></span> <span data-ttu-id="370fb-104">其行為取代了舊版 Visual Basic 中 `PrintForm` 方法的行為。</span><span class="sxs-lookup"><span data-stu-id="370fb-104">Its behavior replaces that of the `PrintForm` method in earlier versions of Visual Basic.</span></span>  
  
 <span data-ttu-id="370fb-105">Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。</span><span class="sxs-lookup"><span data-stu-id="370fb-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="printform-component-overview"></a><span data-ttu-id="370fb-106">PrintForm 元件概觀</span><span class="sxs-lookup"><span data-stu-id="370fb-106">PrintForm Component Overview</span></span>  
 <span data-ttu-id="370fb-107">Windows Form 的常見案例是建立一個表單，其格式類似紙本表單或報表，然後再列印表單的影像。</span><span class="sxs-lookup"><span data-stu-id="370fb-107">A common scenario for Windows Forms is to create a form that is formatted to resemble a paper form or a report, and then to print an image of the form.</span></span> <span data-ttu-id="370fb-108">雖然您可以使用<xref:System.Drawing.Printing.PrintDocument>元件，若要這樣做，這需要大量程式碼。</xref:System.Drawing.Printing.PrintDocument></span><span class="sxs-lookup"><span data-stu-id="370fb-108">Although you can use a <xref:System.Drawing.Printing.PrintDocument> component to do this, it would require a lot of code.</span></span> <span data-ttu-id="370fb-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件可讓您列印到印表機、 預覽列印視窗或檔案格式的映像而不需使用<xref:System.Drawing.Printing.PrintDocument>元件。</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to print an image of a form to a printer, to a print preview window, or to a file without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 <span data-ttu-id="370fb-110"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件位於**Visual Basic PowerPacks**  索引標籤的**工具箱**。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-110">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is located on the **Visual Basic PowerPacks** tab of the **Toolbox**.</span></span> <span data-ttu-id="370fb-111">當元件拖曳至表單時會顯示在元件匣中，也就是表單下框線下方的小型區域。</span><span class="sxs-lookup"><span data-stu-id="370fb-111">When it is dragged onto a form it appears in the component tray, the small area under the bottom border of the form.</span></span> <span data-ttu-id="370fb-112">您可以在選取元件時，設定 [屬性] **** 視窗中的屬性來定義元件的行為。</span><span class="sxs-lookup"><span data-stu-id="370fb-112">When the component is selected, properties that define its behavior can be set in the **Properties** window.</span></span> <span data-ttu-id="370fb-113">這些屬性也都可以在程式碼中設定。</span><span class="sxs-lookup"><span data-stu-id="370fb-113">All of these properties can also be set in code.</span></span> <span data-ttu-id="370fb-114">您也可以建立的執行個體<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件的程式碼，而不需要在設計階段加入元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-114">You can also create an instance of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component in code without adding the component at design time.</span></span>  
  
 <span data-ttu-id="370fb-115">當您列印表單時，會列印表單工作區中的所有內容。</span><span class="sxs-lookup"><span data-stu-id="370fb-115">When you print a form, everything in the client area of the form is printed.</span></span> <span data-ttu-id="370fb-116">這包括所有控制項，以及由 Graphics 方法在表單上繪製的任何文字或圖形。</span><span class="sxs-lookup"><span data-stu-id="370fb-116">This includes all controls and any text or graphics drawn on the form by graphics methods.</span></span> <span data-ttu-id="370fb-117">預設不會列印表單的標題列、捲軸和框線。</span><span class="sxs-lookup"><span data-stu-id="370fb-117">By default, the form's title bar, scroll bars, and border are not printed.</span></span> <span data-ttu-id="370fb-118">根據預設，也<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件列印表單的可見部分。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-118">Also by default, the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component prints only the visible part of the form.</span></span> <span data-ttu-id="370fb-119">例如，如果使用者在執行階段調整表單的大小，則只會列印目前可見的控制項和圖形。</span><span class="sxs-lookup"><span data-stu-id="370fb-119">For example, if the user resizes the form at run time, only the controls and graphics that are currently visible are printed.</span></span>  
  
 <span data-ttu-id="370fb-120">所使用的預設印表機<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件由作業系統的控制台中設定決定。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-120">The default printer used by the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is determined by the operating system's Control Panel settings.</span></span>  
  
 <span data-ttu-id="370fb-121">在起始列印之後，標準<xref:System.Drawing.Printing.PrintDocument>列印對話方塊隨即出現。</xref:System.Drawing.Printing.PrintDocument></span><span class="sxs-lookup"><span data-stu-id="370fb-121">After printing is initiated, a standard <xref:System.Drawing.Printing.PrintDocument> printing dialog box is displayed.</span></span> <span data-ttu-id="370fb-122">這個對話方塊可讓使用者取消列印工作。</span><span class="sxs-lookup"><span data-stu-id="370fb-122">This dialog box enables users to cancel the print job.</span></span>  
  
### <a name="key-methods-properties-and-events"></a><span data-ttu-id="370fb-123">主要方法、屬性和事件</span><span class="sxs-lookup"><span data-stu-id="370fb-123">Key Methods, Properties, and Events</span></span>  
 <span data-ttu-id="370fb-124">金鑰的方法<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件是<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法，它會列印到印表機、 預覽列印視窗或檔案格式的影像。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-124">The key method of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method, which prints an image of the form to a printer, print preview window, or file.</span></span> <span data-ttu-id="370fb-125">有兩個版本的<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法︰</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-125">There are two versions of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method:</span></span>  
  
-   <span data-ttu-id="370fb-126">不含參數的基本版本︰`Print()`</span><span class="sxs-lookup"><span data-stu-id="370fb-126">A basic version without parameters: `Print()`</span></span>  
  
-   <span data-ttu-id="370fb-127">指定列印行為的參數多載的版本︰`Print(printForm As Form, printFormOption As PrintOption)`</span><span class="sxs-lookup"><span data-stu-id="370fb-127">An overloaded version with parameters that specify printing behavior: `Print(printForm As Form, printFormOption As PrintOption)`</span></span>  
  
     <span data-ttu-id="370fb-128">多載方法的 `PrintOption` 參數可決定用來列印表單的基礎實作；是否列印表單的標題列、捲軸和框線；以及是否列印表單可捲動的部分。</span><span class="sxs-lookup"><span data-stu-id="370fb-128">The `PrintOption` parameter of the overloaded method determines the underlying implementation used to print the form, whether the form's title bar, scroll bars, and border are printed, and whether scrollable parts of the form are printed.</span></span>  
  
 <span data-ttu-id="370fb-129"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>屬性是索引鍵屬性的<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-129">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property is a key property of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component.</span></span> <span data-ttu-id="370fb-130">這個屬性可決定要將輸出傳送至印表機、顯示在 [預覽列印] 視窗中，還是儲存為封裝式 PostScript 檔案。</span><span class="sxs-lookup"><span data-stu-id="370fb-130">This property determines whether the output is sent to a printer, displayed in a print preview window, or saved as an Encapsulated PostScript file.</span></span> <span data-ttu-id="370fb-131">如果<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>屬性設定為<xref:System.Drawing.Printing.PrintAction>、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>屬性指定的路徑和檔案名稱。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> </xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-131">If the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property is set to <xref:System.Drawing.Printing.PrintAction>, the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property specifies the path and file name.</span></span>  
  
 <span data-ttu-id="370fb-132"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A>屬性會提供基礎<xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>物件，可讓您指定要使用的印表機和列印的份數等設定</xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>的存取權</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-132">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> property provides access to an underlying <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> object that enables you to specify such settings as the printer to use and the number of copies to print.</span></span> <span data-ttu-id="370fb-133">您也可以查詢印表機的功能，例如彩色或雙面列印支援。</span><span class="sxs-lookup"><span data-stu-id="370fb-133">You can also query the printer's capabilities, such as color or duplex support.</span></span> <span data-ttu-id="370fb-134">這個屬性不會顯示在 [屬性] **** 視窗中，只能透過程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="370fb-134">This property does not appear in the **Properties** window; it can be accessed only from code.</span></span>  
  
 <span data-ttu-id="370fb-135"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A>屬性用來指定當您叫用來列印表單<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件以程式設計的方式。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-135">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> property is used to specify the form to print when you invoke the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component programmatically.</span></span> <span data-ttu-id="370fb-136">如果該元件在設計階段已加入表單中，則該表單會是預設值。</span><span class="sxs-lookup"><span data-stu-id="370fb-136">If the component is added to a form at design time, that form is the default.</span></span>  
  
 <span data-ttu-id="370fb-137">索引鍵的事件<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件包括下列︰</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-137">Key events for the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component include the following:</span></span>  
  
-   <span data-ttu-id="370fb-138"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint></span><span class="sxs-lookup"><span data-stu-id="370fb-138"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> event.</span></span> <span data-ttu-id="370fb-139">發生於當<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法稱為 「 文件列印的第一頁之前。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-139">Occurs when the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method is called and before the first page of the document prints.</span></span>  
  
-   <span data-ttu-id="370fb-140"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint></span><span class="sxs-lookup"><span data-stu-id="370fb-140"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> event.</span></span> <span data-ttu-id="370fb-141">發生於列印最後一頁時。</span><span class="sxs-lookup"><span data-stu-id="370fb-141">Occurs after the last page is printed.</span></span>  
  
-   <span data-ttu-id="370fb-142"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings></span><span class="sxs-lookup"><span data-stu-id="370fb-142"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> event.</span></span> <span data-ttu-id="370fb-143">在每頁即將列印前發生。</span><span class="sxs-lookup"><span data-stu-id="370fb-143">Occurs immediately before each page is printed.</span></span>  
  
### <a name="remarks"></a><span data-ttu-id="370fb-144">備註</span><span class="sxs-lookup"><span data-stu-id="370fb-144">Remarks</span></span>  
 <span data-ttu-id="370fb-145">如果表單包含文字或圖形來繪製<xref:System.Drawing.Graphics>方法時，使用基本<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>(`Print()`) 方法，以列印它</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="370fb-145">If a form contains text or graphics drawn by <xref:System.Drawing.Graphics> methods, use the basic <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) method to print it.</span></span> <span data-ttu-id="370fb-146">圖形可能不會在某些作業系統上呈現時的多載<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法可用。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-146">Graphics may not render on some operating systems when the overloaded <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> method is used.</span></span>  
  
 <span data-ttu-id="370fb-147">如果表單的寬度超過印表機中紙張的寬度，則表單的右側可能會被截斷。</span><span class="sxs-lookup"><span data-stu-id="370fb-147">If the width of a form is wider than the width of the paper in the printer, the right side of the form might be cut off.</span></span> <span data-ttu-id="370fb-148">設計列印用的表單時，請確定表單符合標準大小的紙張。</span><span class="sxs-lookup"><span data-stu-id="370fb-148">When you design forms for printing, make sure that the form fits on standard-sized paper.</span></span>  
  
## <a name="example"></a><span data-ttu-id="370fb-149">範例</span><span class="sxs-lookup"><span data-stu-id="370fb-149">Example</span></span>  
 <span data-ttu-id="370fb-150">下列範例將示範一種常見用法<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="370fb-150">The following example shows a common use of the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component.</span></span>  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a><span data-ttu-id="370fb-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="370fb-151">See Also</span></span>  
 <span data-ttu-id="370fb-152"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-152"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></span></span>   
 <span data-ttu-id="370fb-153"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span><span class="sxs-lookup"><span data-stu-id="370fb-153"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></span></span>   
<span data-ttu-id="370fb-154"> [如何︰ 使用 PrintForm 元件列印表單](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md) </span><span class="sxs-lookup"><span data-stu-id="370fb-154"> [How to: Print a Form by Using the PrintForm Component](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md) </span></span>  
<span data-ttu-id="370fb-155"> [如何︰ 列印表單的工作區](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="370fb-155"> [How to: Print the Client Area of a Form](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md) </span></span>  
<span data-ttu-id="370fb-156"> [如何︰ 列印用戶端和非工作區的表單](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span><span class="sxs-lookup"><span data-stu-id="370fb-156"> [How to: Print Client and Non-Client Areas of a Form](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md) </span></span>  
<span data-ttu-id="370fb-157"> [如何：列印可捲動的表單](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)</span><span class="sxs-lookup"><span data-stu-id="370fb-157"> [How to: Print a Scrollable Form](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)</span></span>
