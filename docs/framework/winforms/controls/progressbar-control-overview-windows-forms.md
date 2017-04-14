---
title: "ProgressBar 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "ProgressBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "進度控制項, 關於進度控制項"
  - "ProgressBar 控制項 [Windows Form], 關於 ProgressBar 控制項"
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# ProgressBar 控制項概觀 (Windows Form)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form <xref:System.Windows.Forms.ProgressBar> 控制項藉由在水平列 \(Horizontal Bar\) 中顯示所排列的適當矩形數目來指示處理序的進度。  當處理序完成時，水平列將被填滿。  進度列通常用來讓使用者暸解完成長時間處理序所需等待的時間，例如，載入大型檔案時。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> 控制項僅可以在表單上呈水平導向。  
  
## 主要屬性和方法  
 <xref:System.Windows.Forms.ProgressBar> 控制項的主要屬性為 <xref:System.Windows.Forms.ProgressBar.Value%2A>、<xref:System.Windows.Forms.ProgressBar.Minimum%2A>，和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A>。  <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 和 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 屬性設定進度列所能顯示的最大和最小值。  <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性表示目前作業的完成進度。  由於顯示在控制項中的進度列是由區塊所組成，因此由 <xref:System.Windows.Forms.ProgressBar> 控制項所顯示的值只是 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性目前大約的值。  <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性會根據 <xref:System.Windows.Forms.ProgressBar> 控制項的大小，決定何時顯示下一個區塊。  
  
 最常用於更新目前進度值的方法，是撰寫程式碼以設定 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性。  以載入大型檔案為例，您可將最大值設定為以 KB 為單位的檔案大小。  例如，如果 <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 屬性設定為 100，<xref:System.Windows.Forms.ProgressBar.Minimum%2A> 屬性設定為 10，而 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性設定為 50，則會顯示 5 個矩型。  這是可顯示數量的一半。  
  
 然而，除了直接設定 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性以外，還有其他方法可以修改由 <xref:System.Windows.Forms.ProgressBar> 控制項顯示的值。  <xref:System.Windows.Forms.ProgressBar.Step%2A> 屬性可以用於指定遞增 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性的值。  然後，呼叫 <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> 方法將會遞增這個值。  若要變更該遞增值，可使用 <xref:System.Windows.Forms.ProgressBar.Increment%2A> 方法，並指定用以遞增 <xref:System.Windows.Forms.ProgressBar.Value%2A> 屬性的值。  
  
 另一個以圖形化方式將目前動作告知使用者的控制項是 <xref:System.Windows.Forms.StatusBar> 控制項。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代和加入功能至 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項；不過 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項會保留以提供回溯相容性和未來使用 \(如果您選擇要使用\)。  
  
## 請參閱  
 <xref:System.Windows.Forms.ProgressBar>   
 [ProgressBar 控制項](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)