---
title: "NumericUpDown 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "NumericUpDown"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "數字微調按鈕控制項, Windows Form"
  - "NumericUpDown 控制項 [Windows Form], 關於 NumericUpDown 控制項"
  - "微調按鈕控制項, Windows Form"
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# NumericUpDown 控制項概觀 (Windows Form)
<xref:System.Windows.Forms.NumericUpDown> 控制項看起來像文字方塊與一對箭號 \(使用者按一下以調整值\) 的組合。  這個控制項會顯示和設定固定數值選擇清單中的單一數值。  使用者可按一下向上和向下箭號、按下向上和向下鍵或在控制項的文字方塊部分輸入數字，以增加或減少數字。  按一下向上鍵會向最大值移動；按一下向下鍵則會向最小值移動。  
  
 例如，如果您想建立音樂播放應用程式的音量控制項，這個控制項因為具有靈活的功能，將是個明顯的好選擇。  <xref:System.Windows.Forms.NumericUpDown> 控制項使用於許多 Windows 控制台應用程式。  
  
## 主要屬性和方法  
 顯示在控制項文字方塊中的數字，可以具有各種格式 \(包含十六進位\)。  如需詳細資訊，請參閱 [如何：為 Windows Form NumericUpDown 控制項設定格式](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)。  控制項的主要屬性為 <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> \(預設值為 100\)、<xref:System.Windows.Forms.NumericUpDown.Minimum%2A> \(預設值為 0\) 和 <xref:System.Windows.Forms.NumericUpDown.Increment%2A> \(預設值為 1\)。  <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性會設定控制項中目前選取的數值。  <xref:System.Windows.Forms.NumericUpDown.Increment%2A> 屬性會設定使用者在按一下向上或向下箭號時數值的調整量。  當焦點離開控制項時，任何輸入都會根據最小和最大的數值加以驗證。  當使用者持續按向上和向下箭號時，您可以藉由 <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> 屬性加快控制項在數目之間移動的速度。  此控制項的主要方法是：<xref:System.Windows.Forms.NumericUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>。  
  
## 請參閱  
 <xref:System.Windows.Forms.NumericUpDown>   
 [NumericUpDown 控制項](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [如何：為 Windows Form NumericUpDown 控制項設定格式](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)   
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)