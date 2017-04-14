---
title: "自訂控制項繪製和轉譯 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 繪圖"
  - "自訂控制項 [Windows Form], 呈現"
  - "OnPaint 方法"
  - "使用者控制項 [Windows Form], 繪圖"
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 自訂控制項繪製和轉譯
控制項的自訂繪製是可由 .NET Framework 簡化的許多複雜工作之一。  當撰寫自訂控制項時，您需要選擇許多與控制項的圖形外觀相關的選項。  如果您正在撰寫的控制項是繼承自 `Control`，您必須提供程式碼，讓您的控制項轉譯其圖形表示。  如果您是藉由繼承 `UserControl` 來建立使用者控制項，或繼承自任一 Windows Form 控制項，則您可以覆寫標準的圖形表示並提供您自己的圖形程式碼。  如果您要將自訂轉譯提供給正在撰寫的 `UserControl` 的組成控制項 \(Constituent Control\)，則您的選項會受到更多的限制，不過您的控制項和應用程式仍可使用廣泛的圖形選項。  
  
## 在本節中  
 [呈現 Windows Form 控制項](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 示範如何為顯示控制項的邏輯撰寫程式。  
  
 [使用者自訂描繪控制項](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 提供撰寫和覆寫控制項的轉譯程式碼所需步驟之概觀。  
  
 [組成控制項](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 說明如何在您的使用者控制項和表單中，實作組成控制項的自訂轉譯程式碼。  
  
 [如何：在執行階段期間隱藏控制項](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 顯示如何使用 <xref:System.Windows.Forms.Control.Visible%2A> 屬性來隱藏或顯示控制項。  
  
 [如何：為控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 顯示如何使用 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法來建立不透明、透明或部分透明的背景色彩。  
  
 [使用視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 顯示如何在支援的作業系統中使用視覺化樣式來轉譯控制項。  
  
## 參考  
 <xref:System.Windows.Forms.Control>  
 不僅描述這個類別，並且提供連至它所有成員的連結。  
  
 <xref:System.Windows.Forms.UserControl>  
 不僅描述這個類別，並且提供連至它所有成員的連結。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 描述這個方法。  
  
## 相關章節  
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 從 Visual Studio 的觀點簡介 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 的圖形功能，並提供詳細資訊的連結。  
  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 描述您可以撰寫的自訂控制項類型。