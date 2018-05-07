---
title: 存取 Managed HTML 文件物件模型上未公開的成員
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: d2fbccfb3ecd7716420ca951e86f728798d25258
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>存取 Managed HTML 文件物件模型上未公開的成員
Managed HTML 文件物件模型 (DOM) 包含一種類別稱為<xref:System.Windows.Forms.HtmlElement>會公開屬性、 方法和所有 HTML 項目都有通用的事件。 有時候，不過，您將需要存取的受管理的介面不會直接公開的成員。 本主題討論兩種方式來存取未公開的成員，包括[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]和網頁內所定義的 VBScript 函式。  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>透過 Managed 的介面存取未公開的成員  
 <xref:System.Windows.Forms.HtmlDocument> 和<xref:System.Windows.Forms.HtmlElement>提供四種方法，以便存取未公開的成員。 下表顯示類型和其對應的方法。  
  
|成員類型|方法|  
|-----------------|-----------------|  
|屬性 (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|方法|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 當您使用這些方法時，它會假設您有正確的基礎類型的元素。 假設您想要聆聽`Submit`事件`FORM`上 HTML 項目頁面上，以便您可以在執行某些前置處理`FORM`的值之前，使用者將其提交至伺服器。 在理想情況下，如果您有 HTML 的控制，您會定義`FORM`能夠唯一`ID`屬性。  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 載入到這個頁面之後<xref:System.Windows.Forms.WebBrowser>控制項，您可以使用<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>方法來擷取`FORM`在執行的階段使用`form1`做為引數。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>存取未受管理的介面  
 您也可以使用每個 DOM 類別所公開的 unmanaged 的元件物件模型 (COM) 介面，以存取 managed HTML DOM 中未公開的成員。 如果您需要進行數次呼叫針對未公開的成員，或是未公開的成員會傳回其他未受管理的 HTML DOM 所包裝的 unmanaged 的介面，這被建議  
  
 下表顯示所有 managed HTML dom。 透過公開的 unmanaged 介面 如需說明其用法及範例程式碼的每個連結上按一下。  
  
|類型|Unmanaged 的介面|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 若要使用的 COM 介面最簡單方式是加入至未受管理的 HTML DOM 文件庫 (MSHTML.dll) 的參考，從您的應用程式中，雖然這是不支援。 如需詳細資訊，請參閱[知識庫文章 934368](http://support.microsoft.com/kb/934368)。  
  
## <a name="accessing-script-functions"></a>存取指令碼函式  
 HTML 網頁可以定義一個或多個函式，利用指令碼語言，例如[!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)]或 VBScript。 這些函式會放在`SCRIPT`頁面的頁面上，並且可以 DOM 上執行依需求或為了回應事件  
  
 您可以呼叫您定義在 HTML 頁面使用的任何指令碼函式<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>方法。 如果指令碼方法傳回的 HTML 項目，您可以使用轉型將這個傳回結果至轉換<xref:System.Windows.Forms.HtmlElement>。 如需詳細資訊和範例程式碼，請參閱<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Managed HTML 文件物件模型](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
