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
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988395"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a>存取 Managed HTML 文件物件模型上未公開的成員
Managed HTML 檔案物件模型（DOM）包含一個名<xref:System.Windows.Forms.HtmlElement>為的類別，它會公開所有 HTML 元素通用的屬性、方法和事件。 不過，有時候您需要存取 managed 介面不會直接公開的成員。 本主題將探討兩種存取未公開成員的方式，包括在網頁內定義的 JScript 和 VBScript 函式。  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a>透過 Managed 介面存取未公開的成員  
 <xref:System.Windows.Forms.HtmlDocument>和<xref:System.Windows.Forms.HtmlElement>提供四種方法，可讓您存取未公開的成員。 下表顯示類型及其對應的方法。  
  
|成員類型|方法|  
|-----------------|-----------------|  
|屬性（<xref:System.Windows.Forms.HtmlElement>）|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|方法|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|事件（<xref:System.Windows.Forms.HtmlDocument>）|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|事件（<xref:System.Windows.Forms.HtmlElement>）|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|事件（<xref:System.Windows.Forms.HtmlWindow>）|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 當您使用這些方法時，會假設您有正確基礎類型的元素。 假設您想要接聽`Submit` HTML 網頁上專案`FORM`的事件，讓您可以在使用者將其提交至伺服器之前，對`FORM`的值執行一些前置處理。 在理想的情況下，如果您可以控制 HTML，您會`FORM`將定義為具有`ID`唯一的屬性。  
  
```html  
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
  
 將此頁面<xref:System.Windows.Forms.WebBrowser>載入控制項之後，您可以<xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>使用方法， `FORM`在執行時間使用`form1`當做引數來取出。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a>存取未受管理的介面  
 您也可以使用每個 DOM 類別所公開的非受控元件物件模型（COM）介面，來存取 managed HTML DOM 上未公開的成員。 如果您必須對未公開的成員進行數個呼叫，或未公開的成員傳回 managed HTML DOM 未包裝的其他非受控介面，則建議使用此選項。  
  
 下表顯示所有透過 managed HTML DOM 公開的非受控介面。 按一下每個連結以取得其使用方式的說明，以及範例程式碼。  
  
|類型|非受控介面|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 使用 COM 介面最簡單的方式，就是從您的應用程式加入非受控 HTML DOM 程式庫（MSHTML）的參考，不過這是不支援的作法。 如需詳細資訊，請參閱[知識庫文章 934368](https://support.microsoft.com/kb/934368)。  
  
## <a name="accessing-script-functions"></a>存取腳本函式  
 HTML 網頁可以使用指令碼語言（例如 JScript 或 VBScript）來定義一或多個函式。 這些函式會放在頁面`SCRIPT`的頁面內，而且可以視需要執行，或是回應 DOM 上的事件。  
  
 您可以使用<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>方法，呼叫您在 HTML 網頁中定義的任何腳本函數。 如果腳本方法傳回 HTML 專案，您可以使用 cast 將這個傳回結果<xref:System.Windows.Forms.HtmlElement>轉換成。 如需詳細資訊和範例程式<xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>代碼，請參閱。  
  
## <a name="see-also"></a>另請參閱

- [使用 Managed HTML 文件物件模型](using-the-managed-html-document-object-model.md)
