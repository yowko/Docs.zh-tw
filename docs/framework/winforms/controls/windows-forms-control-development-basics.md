---
title: "Windows Form 控制項開發的基本概念 | Microsoft Docs"
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
  - "控制項 [Windows Form], 建立"
  - "自訂控制項 [Windows Form], 衍生類型"
  - "程式設計概念, Windows Form 控制項"
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows Form 控制項開發的基本概念
Windows Form 控制項是直接或間接衍生自 <xref:System.Windows.Forms.Control?displayProperty=fullName> 的類別。  下列清單說明開發 Windows Form 控制項的一般案例。  
  
-   組合現有控制項來撰寫複合控制項 \(Composite Control\)。  
  
     複合控制項封裝可當做控制項重複使用的使用者介面。  複合控制項的一個例子為文字方塊和重設按鈕所組成的控制項。  視覺設計工具提供用以建立複合控制項的豐富支援。  若要撰寫複合控制項，要衍生自 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>。  基底類別 \(Base Class\) <xref:System.Windows.Forms.UserControl> 提供子控制項的鍵盤路由，並讓子控制項能夠以群組來工作。  如需詳細資訊，請參閱[開發複合 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)。  
  
-   擴充現有控制項來自訂它，或加入至其功能。  
  
     其色彩無法變更的按鈕和具有額外屬性 \(記錄已按下的次數\) 的按鈕是擴充的控制項的例子。  您可以從它衍生並覆寫或加入屬性、方法和事件，來自訂任何 Windows Form 控制項。  
  
-   撰寫不會組合或擴充現有控制項的控制項。  
  
     在這個案例中，請從基底類別 <xref:System.Windows.Forms.Control> 衍生您的控制項。  您可以加入並且覆寫基底類別的屬性、方法和事件。  若要開始使用，請參閱 [如何：開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)。  
  
 <xref:System.Windows.Forms.Control> 是 Windows Forms 控制項的基底類別，提供在用戶端 Windows 架構應用程式中視覺顯示所需要的配管。  <xref:System.Windows.Forms.Control> 提供視窗控制代碼、處理訊息路由，以及提供滑鼠和鍵盤事件與許多其他的使用者介面事件。  它提供了進階配置，且具有視覺顯示特有的屬性，例如 <xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Height%2A>、<xref:System.Windows.Forms.Control.Width%2A> 和許多其他屬性。  此外，它提供安全性、執行緒支援和與 ActiveX 控制項的互通性 \(Interoperability\)。  因為基底類別提供如此大量的基礎結構，開發您自己的 Windows Form 控制項變得相當容易。  
  
## 請參閱  
 [如何：開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)   
 [開發複合 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)   
 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)   
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)