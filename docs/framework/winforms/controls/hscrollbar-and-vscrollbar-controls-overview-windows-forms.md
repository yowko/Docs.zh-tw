---
title: "HScrollBar 和 VScrollBar 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "HScrollBar"
  - "VScrollBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "HScrollBar 控制項 [Windows Form], 關於 HScrollBar"
  - "捲軸, 關於捲軸"
  - "ScrollBar 控制項 [Windows Form]"
  - "ScrollBar 控制項 [Windows Form], 關於 ScrollBar 控制項"
  - "VScrollBar 控制項 [Windows Form], 關於 VScrollBar 控制項"
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)
利用在應用程式或控制項內水平或垂直捲動的方式，Windows Form <xref:System.Windows.Forms.ScrollBar> 控制項可用來輕鬆巡覽冗長的項目清單或大量資訊。  捲軸是 Windows 介面中的常見項目，因此 <xref:System.Windows.Forms.ScrollBar> 控制項常用於非衍生自 <xref:System.Windows.Forms.ScrollableControl> 類別的控制項。  基於同樣的原因，有許多開發人員會在撰寫自己的使用者控制項時選擇加入 <xref:System.Windows.Forms.ScrollBar> 控制項。  
  
 <xref:System.Windows.Forms.HScrollBar> \(水平\) 和 <xref:System.Windows.Forms.VScrollBar> \(垂直\) 控制項的操作獨立於其他控制項，而且它們擁有自己的事件、屬性和方法。  <xref:System.Windows.Forms.ScrollBar> 控制項與附加至文字方塊、清單方塊、下拉式方塊或 MDI 表單的內建捲軸不同 \(<xref:System.Windows.Forms.TextBox> 控制項擁有 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性，可顯示或隱藏附加在控制項上的捲軸\)。  
  
 <xref:System.Windows.Forms.ScrollBar> 控制項使用 <xref:System.Windows.Forms.ScrollBar.Scroll> 事件來監視捲軸上捲動方塊 \(有時稱為縮圖\) 的移動動作。  使用 <xref:System.Windows.Forms.ScrollBar.Scroll> 事件能夠存取拖曳捲軸時的捲軸值。  
  
## Value 屬性  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> 屬性 \(預設值為 0\) 是對應至捲軸中捲動方塊位置的 `integer` 值。  當捲動方塊位置位於最小值時，它會移至最左邊的位置 \(水平捲軸\) 或最上方的位置 \(垂直捲軸\)。  當捲動方塊位於最大值時，捲動方塊會移至最右邊或底部的位置。  同樣地，介於範圍上下限中間的值會將捲動方塊的前緣置於捲軸中間。  
  
 除了按一下滑鼠來變更捲軸值之外，使用者也可將捲動方塊拖曳至捲軸上的任何位置。  產生的值將視捲動方塊的位置而定，但這個值永遠是在使用者設定的 <xref:System.Windows.Forms.ScrollBar.Minimum%2A> 到 <xref:System.Windows.Forms.ScrollBar.Maximum%2A> 屬性的範圍內。  
  
## LargeChange 和 SmallChange 屬性  
 當使用者按 PAGE UP 或 PAGE DOWN 鍵，或按一下捲動方塊兩端的捲軸列時，<xref:System.Windows.Forms.ScrollBar.Value%2A> 屬性會根據 <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> 屬性中所設定的值變更。  
  
 當使用者按任一方向鍵或按一下任一捲軸按鈕時，<xref:System.Windows.Forms.ScrollBar.Value%2A> 屬性會根據 <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> 屬性中所設定的值變更。  
  
## 請參閱  
 <xref:System.Windows.Forms.HScrollBar>   
 <xref:System.Windows.Forms.VScrollBar>   
 [Additions to Windows Forms for the .NET Framework 2.0](http://msdn.microsoft.com/zh-tw/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)