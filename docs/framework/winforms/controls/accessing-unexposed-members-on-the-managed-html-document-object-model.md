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
ms.openlocfilehash: 539ac998a557615c097c33cdd4207e99f396e81d
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959623"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>存取 Managed HTML 文件物件模型上未公開的成員
Managed HTML 文件物件模型 (DOM) 包含類別，稱為<xref:System.Windows.Forms.HtmlElement>公開屬性、 方法和所有 HTML 項目都有共通的事件。 有時候，不過，您將需要存取受管理的介面不會直接公開的成員。 本主題討論兩種方式來存取未公開的成員，包括 Web 網頁內定義的 JScript 和 VBScript 函式。  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>透過受管理的介面存取未公開的成員  
 <xref:System.Windows.Forms.HtmlDocument> 和<xref:System.Windows.Forms.HtmlElement>提供四種方法可讓您存取未公開的成員。 下表顯示的型別以及其對應的方法。  
  
|成員類型|方法|  
|-----------------|-----------------|  
|屬性 (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|方法|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlDocument>)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlElement>)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|事件 (<xref:System.Windows.Forms.HtmlWindow>)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 當您使用這些方法時，它會假設您有正確的基礎類型的項目。 假設您想要聆聽`Submit`事件的`FORM`HTML 項目頁面上，以便您可以在執行某些前置處理`FORM`的值之前的使用者將其提交至伺服器。 在理想情況下，如果您有 HTML 的控制，您會定義`FORM`有一個唯一`ID`屬性。  
  
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
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>存取未受管理的介面  
 您也可以使用 DOM 中的每個類別所公開的 unmanaged 的元件物件模型 (COM) 介面來存取 managed HTML DOM 中未公開的成員。 如果您必須呼叫幾個針對未公開的成員，或未公開的成員會傳回其他受管理的 HTML dom。 未包裝的 unmanaged 的介面，這被建議  
  
 下表顯示所有受管理的 HTML dom。 透過公開的 unmanaged 介面 按一下每個連結，以了解其使用方式及範例程式碼。  
  
|類型|未受管理的介面|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 若要使用的 COM 介面的最簡單方式是新增至未受管理的 HTML DOM 文件庫 (MSHTML.dll) 的參考，從您的應用程式，雖然這是不支援。 如需詳細資訊，請參閱 <<c0> [ 知識庫文章 934368](https://support.microsoft.com/kb/934368)。  
  
## <a name="accessing-script-functions"></a>存取指令碼函式  
 HTML 網頁可以定義一或多個函式使用 JScript 或 VBScript 的指令碼語言。 這些函式會放在`SCRIPT`在頁面中，頁面上，而且可以在 DOM 執行依需求或為了回應事件  
  
 您可以呼叫您定義 HTML 頁面使用的任何指令碼函式<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>方法。 如果指令碼方法傳回的 HTML 項目，您可以使用轉換來轉換這個傳回的結果，加<xref:System.Windows.Forms.HtmlElement>。 如需詳細資訊和範例程式碼，請參閱<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>。  
  
## <a name="see-also"></a>另請參閱

- [使用 Managed HTML 文件物件模型](using-the-managed-html-document-object-model.md)
