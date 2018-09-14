---
title: PrintForm 元件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
ms.openlocfilehash: 879d31c5a572689d84af6b2e46f3d33e1a8841c8
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45583725"
---
# <a name="printform-component-visual-basic"></a>PrintForm 元件 (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Visual basic 中的元件可讓您在執行階段列印 Windows Form 的影像。 其行為取代了舊版 Visual Basic 中 `PrintForm` 方法的行為。  
  
 在 Visual Studio 中，已不再包含 PowerPack 控制項，但您可以下載從[下載中心](https://www.microsoft.com/en-us/download/details.aspx?id=25169)。  
  
## <a name="printform-component-overview"></a>PrintForm 元件概觀  
 Windows Form 的常見案例是建立一個表單，其格式類似紙本表單或報表，然後再列印表單的影像。 雖然您可以使用 <xref:System.Drawing.Printing.PrintDocument> 元件來執行這項作業，但這樣做需要撰寫許多程式碼。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件可讓您將表單的影像列印至印表機、[預覽列印] 視窗或檔案，而不需要使用 <xref:System.Drawing.Printing.PrintDocument> 元件。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件位於 [工具箱]  的 [Visual Basic PowerPacks] 索引標籤中。 當元件拖曳至表單時會顯示在元件匣中，也就是表單下框線下方的小型區域。 您可以在選取元件時，設定 [屬性]  視窗中的屬性來定義元件的行為。 這些屬性也都可以在程式碼中設定。 您也可以在程式碼中建立 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的執行個體，而不需要在設計階段加入該元件。  
  
 當您列印表單時，會列印表單工作區中的所有內容。 這包括所有控制項，以及由 Graphics 方法在表單上繪製的任何文字或圖形。 預設不會列印表單的標題列、捲軸和框線。 此外， <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件預設只會列印表單的可見部分。 例如，如果使用者在執行階段調整表單的大小，則只會列印目前可見的控制項和圖形。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件所使用的預設印表機，是由作業系統的 [控制台] 設定所決定。  
  
 啟始列印之後，即會顯示標準的 <xref:System.Drawing.Printing.PrintDocument> 列印對話方塊。 這個對話方塊可讓使用者取消列印工作。  
  
### <a name="key-methods-properties-and-events"></a>主要方法、屬性和事件  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的主要方法是 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法，這個方法會將表單的影像列印至印表機、[預覽列印] 視窗或檔案。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法有兩種版本：  
  
-   不含參數的基本版本： `Print()`  
  
-   指定列印行為之具有參數的多載版本： `Print(printForm As Form, printFormOption As PrintOption)`  
  
     多載方法的 `PrintOption` 參數可決定用來列印表單的基礎實作；是否列印表單的標題列、捲軸和框線；以及是否列印表單可捲動的部分。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性是 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的主要屬性。 這個屬性可決定要將輸出傳送至印表機、顯示在 [預覽列印] 視窗中，還是儲存為封裝式 PostScript 檔案。 如果將 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 屬性設定為 <xref:System.Drawing.Printing.PrintAction.PrintToFile>，則 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> 屬性會指定路徑和檔案名稱。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> 屬性可存取基礎 <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> 物件，這個物件可讓您指定要使用的印表機及要列印的份數等設定。 您也可以查詢印表機的功能，例如彩色或雙面列印支援。 這個屬性不會顯示在 [屬性]  視窗中，只能透過程式碼存取。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> 屬性可在您以程式設計方式叫用 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件時，用來指定要列印的表單。 如果該元件在設計階段已加入表單中，則該表單會是預設值。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的主要事件包括：  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> 事件。 發生於呼叫 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法時 (在文件的第一頁列印之前)。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> 事件。 發生於列印最後一頁時。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> 事件。 在每頁即將列印前發生。  
  
### <a name="remarks"></a>備註  
 如果表單包含由 <xref:System.Drawing.Graphics> 方法所繪製的文字或圖形，請使用基本的 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) 方法列印。 使用多載 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法時，在某些作業系統上可能無法呈現圖形。  
  
 如果表單的寬度超過印表機中紙張的寬度，則表單的右側可能會被截斷。 設計列印用的表單時，請確定表單符合標準大小的紙張。  
  
## <a name="example"></a>範例  
 下列範例會示範 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 元件的常見用法。  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 [操作說明：使用 PrintForm 元件列印表單](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [操作說明：列印表單的工作區](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [操作說明：列印表單的工作區和非工作區](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [操作說明：列印可捲動的表單](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
