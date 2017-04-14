---
title: "如何：為控制項提供透明背景 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 透明背景"
  - "透明, Windows Form 自訂控制項"
  - "透明背景, 自訂控制項"
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 如何：為控制項提供透明背景
在舊版 .NET Framework 中，控制項必須先在表單建構函式中設定 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，才能支援設定透明背景色彩。 在最新版 Framework 中，您可以在設計階段於 \[屬性\] 視窗中，或透過表單建構函式中的程式碼，將大多數控制項的背景色彩設定為 <xref:System.Drawing.Color.Transparent%2A>。  
  
> [!NOTE]
>  Windows Form 控制項不支援純粹透明。 透明的 Windows Form 控制項的背景預設是由其父代所繪製。  
  
> [!NOTE]
>  即使 <xref:System.Windows.Forms.ButtonBase.BackColor%2A> 屬性設定為 <xref:System.Drawing.Color.Transparent%2A>，<xref:System.Windows.Controls.Button> 控制項也不支援透明背景色彩。  
  
### 為控制項提供透明背景色彩  
  
-   在 \[屬性\] 視窗中，選擇 <xref:System.Windows.Forms.ButtonBase.BackColor%2A> 屬性並將其設定為 <xref:System.Drawing.Color.Transparent%2A>。  
  
## 請參閱  
 <xref:System.Drawing.Color.FromArgb%2A>   
 [使用 .NET Framework 開發自訂的 Windows Form 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [使用 Managed 圖形類別](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)   
 [如何：繪製不透明和半透明線條](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)