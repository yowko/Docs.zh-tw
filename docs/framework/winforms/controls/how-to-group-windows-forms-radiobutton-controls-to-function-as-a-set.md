---
title: "如何：將 Windows Form RadioButton 控制項群組成集合使用 | Microsoft Docs"
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
  - "控制項 [Windows Form], 群組"
  - "選項按鈕, 群組"
  - "RadioButton 控制項 [Windows Form], 群組"
  - "Windows Form 控制項, 群組"
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：將 Windows Form RadioButton 控制項群組成集合使用
Windows Form <xref:System.Windows.Forms.RadioButton> 控制項是設計用來讓使用者在兩個或多個設定中進行選擇，不過其中只有一個設定可以指派給程序或物件。  例如，<xref:System.Windows.Forms.RadioButton> 控制項群組會顯示訂單可使用的幾家貨運公司，但只能使用其中一家貨運公司。  因此一次只能選取一個 <xref:System.Windows.Forms.RadioButton>，即使它是功能群組的一部分也一樣。  
  
 您可以將選項按鈕拖曳到容器 \(Container\) \(例如，<xref:System.Windows.Forms.Panel> 控制項、<xref:System.Windows.Forms.GroupBox> 控制項，或表單\) 中來群組這些選項按鈕。  直接加入表單的所有選項按鈕會成為一個群組。  若要加入個別的群組，您需要將選項按鈕置於面板 \(Panel\) 或群組方塊中。  如需有關面板 \(Panel\) 或群組方塊的詳細資訊，請參閱 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) 或 [GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)。  
  
### 若要將 RadioButton 控制項組成集合以別於其他集合獨立運作  
  
1.  從 \[**工具箱**\] 的 \[**Windows Form**\] 索引標籤將 <xref:System.Windows.Forms.GroupBox> 或 <xref:System.Windows.Forms.Panel> 控制項拖曳至表單。  
  
2.  將 <xref:System.Windows.Forms.RadioButton> 控制項拖曳至 <xref:System.Windows.Forms.GroupBox> 或 <xref:System.Windows.Forms.Panel> 控制項上。  
  
## 請參閱  
 <xref:System.Windows.Forms.RadioButton>   
 [RadioButton 控制項概觀](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)   
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [GroupBox 控制項概觀](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)   
 [CheckBox 控制項概觀](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [RadioButton 控制項](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)