---
title: "存取 Managed HTML 文件物件模型上未公開的成員 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Managed HTML DOM, 存取未公開的成員"
  - "未公開的成員"
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 存取 Managed HTML 文件物件模型上未公開的成員
Managed HTML 文件物件模型 \(DOM\) 包含名為 <xref:System.Windows.Forms.HtmlElement> 的類型，此類型公開了所有 HTML 項目共有的屬性、方法和事件。  不過，有時候需要存取 Managed 介面未直接公開的成員。  這個主題檢視了用以存取未公開成員的兩種方式，未公開成員中包括 Web 網頁內定義的 [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] 和 VBScript 函式。  
  
## 透過 Managed 介面存取未公開的成員  
 <xref:System.Windows.Forms.HtmlDocument> 和 <xref:System.Windows.Forms.HtmlElement> 提供了四個存取未公開成員的方法。  下表將顯示型別及對應的方法。  
  
|成員型別|方法|  
|----------|--------|  
|屬性 \(<xref:System.Windows.Forms.HtmlElement>\)|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|方法|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|事件 \(<xref:System.Windows.Forms.HtmlDocument>\)|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|事件 \(<xref:System.Windows.Forms.HtmlElement>\)|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|事件 \(<xref:System.Windows.Forms.HtmlWindow>\)|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 使用這些方法時，已假設您有一個項目為正確的基礎型別。  並且假設您想要接聽 HTML 網頁上 `FORM` 項目的 `Submit` 事件，以便在使用者送出 `FORM` 值給伺服器之前能夠對該值執行部分的前置處理。  理論上，擁有 HTML 的控制項就表示可定義 `FORM` 使其擁有唯一的 `ID` 屬性。  
  
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
  
 當您將這個頁面載入 <xref:System.Windows.Forms.WebBrowser> 控制項之後，即可使用 <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> 方法，在執行階段以 `form1` 為引數來擷取 `FORM`。  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## 存取 Unmanaged 介面  
 也可以利用每個 DOM 類別所公開的 Unmanaged 元件物件模型 \(Component Object Model，COM\)，來存取 Managed HTML DOM 上的未公開成員。  如果必須對未公開的成員進行數次呼叫，或者如果未公開的成員所傳回的是未由 Managed HTML DOM 包裝的其他 Unmanaged 介面，則建議使用這個方式。  
  
 下表顯示所有透過 Managed HTML DOM 公開的 Unmanaged 介面。  按一下每個連結即可取得用法說明及範例程式碼。  
  
|型別|Unmanaged 介面|  
|--------|------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 若要使用的COM介面最簡單的方法是新增至未受管理HTMLDOM文件庫\(MSHTML.dll\) 的參考，從您應用程式中，雖然它不受支援。  如需詳細資訊，請參閱[知識庫文章 934368](http://support.microsoft.com/kb/934368)。  
  
## 存取指令碼函式  
 HTML 網頁利用指令碼語言 \(例如 [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] 或 VBScript\)，即可定義一或多個函式。  這些函式是放置於網頁的 `SCRIPT` 頁面內，可視需要或為了回應 DOM 上的事件而執行。  
  
 可使用 <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> 方法來呼叫 HTML 網頁中定義的任何指令碼函式。  如果此指令碼方法傳回 HTML 項目，可利用轉換 \(Cast\) 將傳回的結果轉換為 <xref:System.Windows.Forms.HtmlElement>。  如需詳細資訊和範例程式碼，請參閱 <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>。  
  
## 請參閱  
 [使用 Managed HTML 文件物件模型](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)