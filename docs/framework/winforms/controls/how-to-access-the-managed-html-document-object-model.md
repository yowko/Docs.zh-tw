---
title: "如何：存取 Managed HTML 文件物件模型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "HTML DOM 存取"
  - "managed HTML DOM 存取"
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：存取 Managed HTML 文件物件模型
您可以從兩種類型的應用程式中，存取受管理的「HTML 文件物件模型」(DOM)：  
  
-   受管理的 Windows Form 應用程式 (.exe) <xref:System.Windows.Forms.WebBrowser>控制項。 這兩種技術為互補，與<xref:System.Windows.Forms.WebBrowser>控制顯示給使用者，HTML DOM 負責文件的邏輯結構的頁面。  
  
-   Windows Form <xref:System.Windows.Forms.UserControl>在 Internet Explorer。 您可以存取 HTML DOM 的那一頁您<xref:System.Windows.Forms.UserControl>託管以變更文件的結構，或開啟強制回應對話方塊等等，許多其他的可能性。  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>從 Windows Forms 應用程式存取 DOM  
  
1.  主機<xref:System.Windows.Forms.WebBrowser> Windows Forms 應用程式中控制和監視的<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件。 如需執行控制項及監視事件的詳細資訊，請參閱[事件](../../../../docs/standard/events/index.md)。  
  
2.  擷取<xref:System.Windows.Forms.HtmlDocument>藉由存取目前的頁面<xref:System.Windows.Forms.WebBrowser.Document%2A>屬性<xref:System.Windows.Forms.WebBrowser>控制項。  
  
<!-- TODO: review snippet reference  [!CODE [AccessHTMLDOMApp#1](AccessHTMLDOMApp#1)]  -->  
  
### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>存取 Internet Explorer 中所執行之 UserControl 的 DOM  
  
1.  建立您自己的衍生的類別<xref:System.Windows.Forms.UserControl>類別。 如需詳細資訊，請參閱[How to︰ 撰寫複合控制項](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)。  
  
2.  將下列程式碼的 Load 事件處理常式內您<xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>穩固程式設計  
  
1.  使用透過 DOM 時<xref:System.Windows.Forms.WebBrowser>控制項，您必須永遠等候，直到<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>事件發生，再嘗試存取<xref:System.Windows.Forms.WebBrowser.Document%2A>屬性<xref:System.Windows.Forms.WebBrowser>控制項。 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>整份文件載入之後，就會引發事件，若您之前使用 DOM，可能會導致您的應用程式的執行階段例外狀況。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
  
1.  您的應用程式或<xref:System.Windows.Forms.UserControl>需要完全信任，才能存取 managed 的 HTML dom。 如果您要部署 Windows Form 應用程式使用[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]，您可以要求使用提高權限或受信任的應用程式部署的完全信任，請參閱[保護 ClickOnce 應用程式](../Topic/Securing%20ClickOnce%20Applications.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Managed 的 HTML 文件物件模型](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)