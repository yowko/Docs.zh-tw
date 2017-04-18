---
title: "如何：以 Windows Form GroupBox 控制項來群組控制項 | Microsoft Docs"
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
  - "GroupBox 控制項 [Windows Form], 群組控制項"
  - "Windows Form 控制項, 群組"
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：以 Windows Form GroupBox 控制項來群組控制項
Windows Form <xref:System.Windows.Forms.GroupBox> 控制項可用來將其他控制項設為群組。  將控制項群組起來的三個目的：  
  
-   將表單內相關元素群組起來，可以達到較清晰的使用者介面視覺效果。  
  
-   依程式設計方式組成群組 \(例如選項按鈕\)。  
  
-   在設計階段，可一次移動群組內所有的控制項。  
  
### 若要建立控制項群組  
  
1.  在表單上繪製 <xref:System.Windows.Forms.GroupBox> 控制項。  
  
2.  將其他控制項加入群組方塊，並在群組方塊中繪製各個控制項。  
  
     如果您已經具有您想要置於某個群組方塊中的現有控制項，您可以選取所有控制項，然後剪下並置入剪貼簿，選取 <xref:System.Windows.Forms.GroupBox> 控制項，然後將它們貼到這個群組方塊內即可。  您也可以將它們拖曳至群組方塊。  
  
3.  將群組方塊的 <xref:System.Windows.Forms.GroupBox.Text%2A> 屬性設為適當的標題。  
  
## 請參閱  
 <xref:System.Windows.Forms.GroupBox>   
 [GroupBox 控制項](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)