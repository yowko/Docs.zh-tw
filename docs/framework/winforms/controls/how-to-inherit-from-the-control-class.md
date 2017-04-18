---
title: "如何：繼承自 Control 類別 | Microsoft Docs"
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
  - "Control 類別, 繼承自"
  - "自訂控制項 [Windows Form], 建立"
  - "自訂控制項 [Windows Form], 繼承"
  - "繼承, Windows Form 自訂控制項"
  - "OnPaint 方法 [Windows Form]"
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：繼承自 Control 類別
如果您要建立完全自訂的控制項以在 Windows Form 上使用，就應該要繼承自 <xref:System.Windows.Forms.Control> 類別。  繼承自 <xref:System.Windows.Forms.Control> 類別需要您執行更多計劃和實作，同時也提供您最大範圍的選項。  繼承 <xref:System.Windows.Forms.Control> 時，您會繼承讓控制項運作的最基本功能。  在 <xref:System.Windows.Forms.Control> 類別中繼承的功能會處理使用者透過鍵盤和滑鼠的輸入、定義控制項的範圍和大小、提供視窗控制代碼 \(Window Handle\)，及提供訊息處理 \(Message Handling\) 和安全性。  它不會加入任何繪製 \(控制項的圖形介面的實際轉譯\)，也不會加入任何特定的使用者互動功能。  您必須透過自訂程式碼提供這些方面的功能。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立自訂控制項  
  
1.  建立新的 \[**Windows 應用程式**\] 或 \[**Windows 控制項程式庫**\] 專案。  
  
2.  在 \[**專案**\] 功能表中選擇 \[**加入類別**\]。  
  
3.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**自訂控制項**\]。  
  
     新的自訂控制項將加入至您的專案中。  
  
4.  按下 F7 以開啟自訂控制項的 \[**程式碼編輯器**\]。  
  
5.  找到 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，除了對基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 的呼叫以外，該方法會是空的。  
  
6.  修改程式碼以加入控制項所需的任何自訂繪製。  
  
     如需撰寫程式碼以呈現控制項圖形的詳細資訊，請參閱[自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)。  
  
7.  實作您的控制項將加入的任何自訂方法、屬性或事件。  
  
8.  儲存和測試您的控制項。  
  
## 請參閱  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [如何：繼承自 UserControl 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [如何：繼承自現有的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [如何：撰寫 Windows Form 的控制項](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [在設計階段開發 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)