---
title: "如何：在 Windows 應用程式中提供說明 | Microsoft Docs"
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
  - "表單, 提供說明"
  - "說明, Windows 應用程式"
  - "HelpProvider 元件 [Windows Form]"
  - "HTML 說明, Windows Form"
  - "Windows 應用程式, 提供說明"
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 Windows 應用程式中提供說明
您可以使用 <xref:System.Windows.Forms.HelpProvider> 元件將說明檔中的說明主題附加至 Windows Form 上的特定控制項。  說明檔可以是 HTML 或 HTMLHelp 1.x 或更高階的格式。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要提供說明  
  
1.  從 \[**工具箱**\] 將 <xref:System.Windows.Forms.HelpProvider> 元件拖曳至表單。  
  
     接著元件就會出現在 Windows Form 設計工具下方的匣中。  
  
2.  在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> 屬性設定為 .chm、.col 或 .htm 說明檔。  
  
3.  選取表單上的另一個控制項，並在 \[**屬性**\] 視窗中設定 [HelpKeyword](frlrfSystemWindowsFormsHelpProviderClassSetHelpKeywordTopic) 屬性。  
  
     這是一個透過 <xref:System.Windows.Forms.HelpProvider> 元件傳遞至說明檔的字串，用來召喚適當的說明主題。  
  
4.  在 \[**屬性**\] 視窗中，將 [HelpNavigator](frlrfSystemWindowsFormsHelpProviderClassSetHelpNavigatorTopic) 屬性設定為 <xref:System.Windows.Forms.HelpNavigator> 列舉型別的值。  
  
     這樣可以決定 **HelpKeyword** 屬性傳遞至說明系統的方式。  下表列出可能的設定以及說明。  
  
    |成員名稱|描述|  
    |----------|--------|  
    |AssociateIndex|指定特定主題的索引在特定 URL 中執行。|  
    |Find|指定顯示特定 URL 的搜尋網頁。|  
    |索引|指定顯示特定 URL 的索引。|  
    |KeywordIndex|指定要在特定的 URL 中搜尋的關鍵字和執行的動作。|  
    |TableOfContents|指定顯示 HTML 1.0 說明檔的目錄。|  
    |主題|指定顯示特定 URL 所參考的主題。|  
  
 在執行階段，如果焦點 \(Focus\) 在控制項上 \(已設定 **HelpKeyword** 和 **HelpNavigator** 屬性的控制項\)，則按下 F1 鍵會開啟和 <xref:System.Windows.Forms.HelpProvider> 元件相關的說明檔。  
  
 目前 **HelpNamespace** 屬性可支援下列三種格式的說明檔：HTMLHelp 1.x、HTMLHelp 2.0 和 HTML。  因此，您可以將 **HelpNamespace** 屬性設定為 http:\/\/ 位址 \(例如 Web 網頁\)。  如果已經這麼做了，它會以做為錨定的 **HelpKeyword** 屬性中所指定的字串開啟預設瀏覽器並顯示 Web 網頁，  此錨定是用來跳至 HTML 網頁的特定部分。  
  
> [!IMPORTANT]
>  在應用程式中使用從用戶端傳來的任何資訊前，請小心檢查。  惡意使用者可能嘗試傳送或插入可執行的指令碼、SQL 陳述式或其他程式碼。  在顯示使用者的輸入前，請先將它儲存在資料庫中或使用它，檢查它確實不包含可能不安全的資訊。  檢查的一般方式，是從使用者接收輸入時，使用規則運算式尋找如「SCRIPT」之類的關鍵字。  
  
 您也可以使用 <xref:System.Windows.Forms.HelpProvider> 元件來顯示快顯說明，即使您已將其設定為要顯示 Windows Form 上控制項的說明檔，也是一樣。  如需詳細資訊，請參閱 [如何：顯示快顯說明](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)。  
  
## 請參閱  
 [如何：顯示快顯說明](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)   
 [使用工具提示來顯示控制項說明](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)   
 [整合 Windows Form 中的使用者說明](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)   
 [Windows Form](../../../../docs/framework/winforms/index.md)