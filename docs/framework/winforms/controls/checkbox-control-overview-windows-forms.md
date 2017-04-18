---
title: "CheckBox 控制項概觀 (Windows Form) | Microsoft Docs"
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
  - "CheckBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "繫結控制項, 核取方塊"
  - "核取方塊, 關於核取方塊"
  - "CheckBox 控制項 [Windows Form], 關於 CheckBox 控制項"
  - "資料繫結, CheckBox 控制項"
  - "資料繫結控制項, 核取方塊"
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# CheckBox 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.CheckBox> 控制項會指出某個特定條件是開啟或關閉。  它通常針對使用者，呈現「是\/否」或「真\/假」的選擇。  您可以使用群組中的核取方塊控制項以顯示多個選擇，讓使用者從中選取一或多個。  
  
 核取方塊控制項與選項按鈕控制項的相似之處在於：兩者都是用來指示使用者所做的選擇；  它們的差異則是您一次只能在選項按鈕群組中選取一個選項按鈕，  而使用核取方塊控制項則可選取任何數目的核取方塊。  
  
 核取方塊可以透過簡單的資料繫結 \(Data Binding\) 連接到資料庫中的項目。  您可使用 <xref:System.Windows.Forms.GroupBox> 控制項將多個核取方塊分組。  這對視覺化外觀及使用者介面設計都很有用，因為群組的控制項可在表單設計工具上同時移動。  如需詳細資訊，請參閱 [Windows Form 資料繫結](../../../../docs/framework/winforms/windows-forms-data-binding.md)和 [GroupBox 控制項](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)。  
  
 <xref:System.Windows.Forms.CheckBox> 控制項有兩個重要的屬性，<xref:System.Windows.Forms.CheckBox.Checked%2A> 和 <xref:System.Windows.Forms.CheckBox.CheckState%2A>。  <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性會傳回 `true` 或 `false`。  <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性會傳回 <xref:System.Windows.Forms.CheckState> 或 <xref:System.Windows.Forms.CheckState>。或者如果將 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設為 `true`，則 <xref:System.Windows.Forms.CheckBox.CheckState%2A> 也會傳回 <xref:System.Windows.Forms.CheckState>。  方塊在不定狀態中會顯示出暗灰色的外觀，以表示無法使用的選項。  
  
## 請參閱  
 <xref:System.Windows.Forms.CheckBox>   
 [如何：使用 Windows Form CheckBox 控制項設定選項](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)   
 [如何：回應 Windows Form CheckBox 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)   
 [CheckBox 控制項](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)