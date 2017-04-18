---
title: "如何：使用控制項呈現類別 | Microsoft Docs"
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
  - "專業外觀, 呈現 Windows Form 控制項"
  - "視覺化樣式, 呈現 Windows Form 控制項"
  - "視覺化佈景主題, 套用到 Windows Form 控制項"
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：使用控制項呈現類別
這個範例示範如何使用 <xref:System.Windows.Forms.ComboBoxRenderer> 類別呈現下拉式方塊控制項的下拉箭號。  此範例是由簡單自訂控制項的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法所組成。  <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=fullName> 屬性會用來決定在應用程式視窗的工作區 \(Client Area\) 中，是否啟用視覺樣式。  如果視覺樣式正在使用中，則 <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=fullName> 方法將會以視覺樣式呈現下拉箭頭，否則 <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=fullName> 方法會使用傳統 Windows 樣式來呈現下拉箭號。  
  
## 範例  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   衍生自 <xref:System.Windows.Forms.Control> 類別的自訂控制項。  
  
-   裝載自訂控制項的 <xref:System.Windows.Forms.Form>。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName> 和 <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 命名空間的參考。  
  
## 請參閱  
 [使用視覺化樣式呈現控制項](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)