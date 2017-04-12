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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f0c51ef0131c874ed33af7a19f9145a790d14ade
ms.lasthandoff: 03/13/2017

---
# <a name="printform-component-visual-basic"></a>PrintForm 元件 (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可讓您在執行階段列印 Windows Form 的影像。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 其行為取代了舊版 Visual Basic 中 `PrintForm` 方法的行為。  
  
 Visual Studio 中已不再包含 PowerPack 控制項，但您可以從 [下載中心](http://www.microsoft.com/en-us/download/details.aspx?id=25169)下載這些控制項。  
  
## <a name="printform-component-overview"></a>PrintForm 元件概觀  
 Windows Form 的常見案例是建立一個表單，其格式類似紙本表單或報表，然後再列印表單的影像。 雖然您可以使用<xref:System.Drawing.Printing.PrintDocument>元件，若要這樣做，這需要大量程式碼。</xref:System.Drawing.Printing.PrintDocument> <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件可讓您列印到印表機、 預覽列印視窗或檔案格式的映像而不需使用<xref:System.Drawing.Printing.PrintDocument>元件。</xref:System.Drawing.Printing.PrintDocument> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件位於**Visual Basic PowerPacks**  索引標籤的**工具箱**。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 當元件拖曳至表單時會顯示在元件匣中，也就是表單下框線下方的小型區域。 您可以在選取元件時，設定 [屬性] **** 視窗中的屬性來定義元件的行為。 這些屬性也都可以在程式碼中設定。 您也可以建立的執行個體<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件的程式碼，而不需要在設計階段加入元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 當您列印表單時，會列印表單工作區中的所有內容。 這包括所有控制項，以及由 Graphics 方法在表單上繪製的任何文字或圖形。 預設不會列印表單的標題列、捲軸和框線。 根據預設，也<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件列印表單的可見部分。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 例如，如果使用者在執行階段調整表單的大小，則只會列印目前可見的控制項和圖形。  
  
 所使用的預設印表機<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件由作業系統的控制台中設定決定。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 在起始列印之後，標準<xref:System.Drawing.Printing.PrintDocument>列印對話方塊隨即出現。</xref:System.Drawing.Printing.PrintDocument> 這個對話方塊可讓使用者取消列印工作。  
  
### <a name="key-methods-properties-and-events"></a>主要方法、屬性和事件  
 金鑰的方法<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件是<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法，它會列印到印表機、 預覽列印視窗或檔案格式的影像。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 有兩個版本的<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法︰</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
  
-   不含參數的基本版本︰`Print()`  
  
-   指定列印行為的參數多載的版本︰`Print(printForm As Form, printFormOption As PrintOption)`  
  
     多載方法的 `PrintOption` 參數可決定用來列印表單的基礎實作；是否列印表單的標題列、捲軸和框線；以及是否列印表單可捲動的部分。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>屬性是索引鍵屬性的<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 這個屬性可決定要將輸出傳送至印表機、顯示在 [預覽列印] 視窗中，還是儲存為封裝式 PostScript 檔案。 如果<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>屬性設定為<xref:System.Drawing.Printing.PrintAction>、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>屬性指定的路徑和檔案名稱。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> </xref:System.Drawing.Printing.PrintAction> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A>屬性會提供基礎<xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>物件，可讓您指定要使用的印表機和列印的份數等設定</xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>的存取權</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> 您也可以查詢印表機的功能，例如彩色或雙面列印支援。 這個屬性不會顯示在 [屬性] **** 視窗中，只能透過程式碼存取。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A>屬性用來指定當您叫用來列印表單<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件以程式設計的方式。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> </xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> 如果該元件在設計階段已加入表單中，則該表單會是預設值。  
  
 索引鍵的事件<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件包括下列︰</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> 發生於當<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法稱為 「 文件列印的第一頁之前。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> 發生於列印最後一頁時。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings>事件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> 在每頁即將列印前發生。  
  
### <a name="remarks"></a>備註  
 如果表單包含文字或圖形來繪製<xref:System.Drawing.Graphics>方法時，使用基本<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>(`Print()`) 方法，以列印它</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:System.Drawing.Graphics> 圖形可能不會在某些作業系統上呈現時的多載<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>方法可用。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
  
 如果表單的寬度超過印表機中紙張的寬度，則表單的右側可能會被截斷。 設計列印用的表單時，請確定表單符合標準大小的紙張。  
  
## <a name="example"></a>範例  
 下列範例將示範一種常見用法<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>元件。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 [如何︰ 使用 PrintForm 元件列印表單](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)   
 [如何︰ 列印表單的工作區](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [如何︰ 列印用戶端和非工作區的表單](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)   
 [如何：列印可捲動的表單](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
