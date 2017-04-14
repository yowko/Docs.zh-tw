---
title: "DomainUpDown 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "DomainUpDown"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DomainUpDown 控制項 [Windows Form], 關於 DomainUpDown 控制項"
  - "微調按鈕控制項, 關於微調按鈕"
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# DomainUpDown 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.DomainUpDown> 控制項基本上是文字方塊和一對可在清單中上下移動的按鈕之組合。  這個控制項會顯示和設定選擇清單中的文字字串。  使用者可以按一下向上和向下按鈕在清單中移動、按向上鍵和向下鍵或輸入與清單項目相符的字串來選取字串。  這個控制項的可能用法之一，是從依字母順序排序的名稱清單中選取項目  
  
> [!NOTE]
>  若要排序清單，請將 <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> 屬性設定為 `true`。  
  
 這個控制項的功能與清單方塊或下拉式方塊非常類似，但它所佔的空間極少。  
  
## 主要屬性  
 控制項的主要屬性有：<xref:System.Windows.Forms.DomainUpDown.Items%2A>、<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> 和 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。  <xref:System.Windows.Forms.DomainUpDown.Items%2A> 屬性包含於控制項中顯示其文字值的物件清單。  如果將 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> 設定為 `false`，控制項會自動完成使用者輸入的文字，並將它與清單中的值比對。  如果將 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> 設定為 `true`，捲至最後一個項目之後將會回到清單的第一個項目，反之亦然。  此控制項的主要方法是：<xref:System.Windows.Forms.DomainUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 這個控制項只會顯示文字字串。  如果您想要使用顯示數值的控制項，請使用 <xref:System.Windows.Forms.NumericUpDown> 控制項。  如需詳細資訊，請參閱 [NumericUpDown 控制項概觀](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.DomainUpDown>   
 [DomainUpDown 控制項](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)