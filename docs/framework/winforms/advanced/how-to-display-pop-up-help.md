---
title: "如何：顯示快顯說明 | Microsoft Docs"
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
  - "F1 說明, 在對話方塊中"
  - "表單, 顯示說明"
  - "說明, 加入至對話方塊"
  - "說明, 快顯說明"
  - "HelpProvider 元件 [Windows Form]"
  - "強制回應對話方塊, 快顯說明"
  - "快顯說明"
  - "Windows Form, 顯示說明"
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：顯示快顯說明
在 Windows Form 上顯示 \[說明\] 的一種方式是透過 \[說明\] 按鈕，這個按鈕位於標題列的右側，並可透過 <xref:System.Windows.Forms.Form.HelpButton%2A> 屬性來存取。  這種顯示 \[說明\] 的方式非常適合與對話方塊一起使用。  以強制回應方式 \(使用 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法\) 顯示的對話方塊無法啟動外部 \[說明\] 系統，因為將焦點轉換至另一個視窗之前，必須先關閉強制回應對話方塊。  此外，使用 \[說明\] 按鈕時，標題列不能顯示 \[最小化\] 按鈕或 \[最大化\] 按鈕。  這是標準的對話方塊慣例，而表單則通常具有 \[最小化\] 和 \[最大化\] 按鈕。  
  
 請注意，您也可以使用 <xref:System.Windows.Forms.HelpProvider> 元件將控制項連結至 \[說明\] 系統中的檔案，即使您已實作快顯 \[說明\] 亦然。  如需詳細資訊，請參閱[在 Windows 應用程式中提供說明](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 顯示快顯說明  
  
1.  將 [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) 元件從 \[工具箱\] 拖曳至表單。  
  
     該元件會位於 Windows Form 設計工具底部的系統匣中。  
  
2.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.Form.HelpButton%2A> 屬性設定為 `true`。  表單的標題列右側會顯示一個有問號的按鈕。  
  
3.  為了顯示 <xref:System.Windows.Forms.Form.HelpButton%2A>，您必須將表單的 <xref:System.Windows.Forms.Form.MinimizeBox%2A> 和 <xref:System.Windows.Forms.Form.MaximizeBox%2A> 屬性設定為 `false`；將 <xref:System.Windows.Forms.Form.ControlBox%2A> 屬性設定為 `true`；並將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為下列其中一個值：<xref:System.Windows.Forms.FormBorderStyle>、<xref:System.Windows.Forms.FormBorderStyle>、<xref:System.Windows.Forms.FormBorderStyle> 或 <xref:System.Windows.Forms.FormBorderStyle>。  
  
4.  選取您要在表單上顯示 \[說明\] 的控制項，並在 \[屬性\] 視窗中設定 \[說明\] 字串。  這是會在視窗中顯示的文字字串，類似[工具提示](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)。  
  
5.  請按 **F5**。  
  
6.  按下標題列上的 \[說明\] 按鈕，然後按一下設定 \[說明\] 字串的控制項。  
  
## 請參閱  
 [使用工具提示來顯示控制項說明](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)   
 [整合 Windows Form 中的使用者說明](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)   
 [Windows Form](../../../../docs/framework/winforms/index.md)