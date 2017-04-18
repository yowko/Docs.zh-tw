---
title: "DomainUpDown 控制項 (Windows Form) | Microsoft Docs"
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
  - "DomainUpDown 控制項 [Windows Form]"
  - "微調按鈕控制項"
  - "微調按鈕控制項, 上下按鈕控制項"
  - "上下按鈕控制項"
  - "上下按鈕控制項, 微調按鈕控制項"
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# DomainUpDown 控制項 (Windows Form)
Windows Form <xref:System.Windows.Forms.DomainUpDown> 控制項看起來像是文字方塊和一對可在清單中上下移動的按鈕的組合。  這個控制項會顯示和設定選擇清單中的文字字串。  使用者可以按一下向上和向下按鈕在清單中移動、按向上鍵和向下鍵或輸入與清單項目相符的字串來選取字串。  這個控制項的可能用法之一，是從依字母順序排序的名稱清單中選取項目   \(若要排序清單，請將 <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> 屬性設定為 `true`\)。 這個控制項的功能與清單方塊或下拉式方塊非常類似，但它所佔的空間極少。  
  
 控制項的主要屬性有：<xref:System.Windows.Forms.DomainUpDown.Items%2A>、<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> 和 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。  <xref:System.Windows.Forms.DomainUpDown.Items%2A> 屬性包含於控制項中顯示其文字值的物件清單。  如果將 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> 設定為 `false`，控制項會自動完成使用者輸入的文字，並將它與清單中的值比對。  如果將 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> 設定為 `true`，捲至最後一個項目之後將會回到清單的第一個項目，反之亦然。  此控制項的主要方法是：<xref:System.Windows.Forms.DomainUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。  
  
 這個控制項只會顯示文字字串。  如果您想要使用顯示數值的控制項，請使用 <xref:System.Windows.Forms.NumericUpDown> 控制項。  如需詳細資訊，請參閱[NumericUpDown 控制項](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)。  
  
## 在本節中  
 [DomainUpDown 控制項概觀](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 介紹 <xref:System.Windows.Forms.DomainUpDown> 控制項的一般概念，這個控制項允許使用者瀏覽文字字串的清單並從中進行選取。  
  
 [如何：以程式設計的方式將項目加入至 Windows Form DomainUpDown 控制項](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 說明如何指定 <xref:System.Windows.Forms.DomainUpDown> 控制項應該顯示的文字字串。  
  
 [如何：從 Windows Form DomainUpDown 控制項中移除項目](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 說明如何在程式碼中從 <xref:System.Windows.Forms.DomainUpDown> 控制項刪除項目。  
  
## 參考  
 <xref:System.Windows.Forms.DomainUpDown>  
 描述這個類別並且連結到它所有的成員。  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 描述這個類別並且連結至它所有的成員。  
  
## 相關章節  
 [可以在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 提供 Windows Form 控制項的完整清單及其用法資訊的連結。