---
title: "HelpProvider 元件概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HelpProvider"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "對話方塊, 即時線上說明"
  - "F1 說明, 加入到 Windows Form"
  - "說明, 加入到 Windows 應用程式"
  - "HelpProvider 元件 [Windows Form], 關於 HelpProvider 元件"
  - "Windows Form, 即時線上說明"
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# HelpProvider 元件概觀 (Windows Form)
Windows Form [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) 元件用於將 HTML HELP 1.x 說明檔 \(可能是以 HTML Help Workshop 產生的 .chm 檔，或是 .htm 檔\) 與您的 Windows 應用程式建立關聯。  您可利用各種方式提供說明：  
  
-   為 Windows Form 上的控制項提供即時線上說明。  
  
-   為特定對話方塊或對話方塊中的特定控制項提供即時線上說明。  
  
-   在特定區域中開啟說明檔，例如目錄的主頁、索引或搜尋功能。  
  
## 使用說明提供者  
 在 Windows Form 中加入 <xref:System.Windows.Forms.HelpProvider> 元件，可讓表單上的其他控制項公開 \(Expose\) <xref:System.Windows.Forms.HelpProvider> 元件的說明內容。  這可讓您針對 Windows Form 上的控制項提供說明。  可以利用 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> 屬性，將說明檔與 <xref:System.Windows.Forms.HelpProvider> 元件建立關聯。  您可以呼叫 <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>，並為指定之控制項提供 <xref:System.Windows.Forms.HelpNavigator> 列舉的值，以便指定所提供 \[說明\] 的類型。  呼叫 <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> 方法，則可提供說明的關鍵字或主題。  
  
 另外，若要將特定說明字串與其他控制項建立關聯，請使用 <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> 方法。  當使用者在控制項具有焦點 \(Focus\) 的情況下按 F1 時，使用這個方法與控制項建立關聯的字串就會出現在快顯視窗 \(Pop\-Up Window\) 中。  
  
 如果 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> 尚未設定，必須使用 <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> 以提供說明文字。  如果同時設定了 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> 以及說明字串，則會優先採用以 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> 為根據的說明。  
  
> [!NOTE]
>  如果在 <xref:System.Windows.Forms.Help.ShowHelp%2A> 方法或 <xref:System.Windows.Forms.HelpProvider> 控制項的 <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> 屬性中以相對路徑指定說明檔路徑，可能會遇到問題。  因此，請務必使用絕對檔案路徑來指定說明檔。  
  
## 請參閱  
 [Windows Form 應用程式中的說明系統](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)