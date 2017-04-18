---
title: "如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項 | Microsoft Docs"
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
  - "Panel 控制項 [Windows Form], 群組控制項"
  - "Windows Form 控制項, 群組"
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：搭配 Windows Form Panel 控制項使用設計工具群組控制項
Windows Form <xref:System.Windows.Forms.Panel> 控制項可用來將其他控制項設為群組。  有三個原因必須群組控制項。  第一個是，視覺化群組相關的表單項目，以取得清楚的使用者介面；另一個理由是，程式化群組，例如選項按鈕等；最後一個理由是，在設計階段中，將控制項當做一個單位來移動。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立控制項群組  
  
1.  從 \[工具箱\] 的 \[**Windows Form**\] 索引標籤，將 <xref:System.Windows.Forms.Panel> 控制項拖曳至表單中。  
  
2.  將其他控制項加入面版 \(Panel\)，並將每一項拖曳至面版中。  
  
     如果想將現存的控制項含括至一個面版中，您可以選取所有控制項，剪下它們並置入剪貼簿，選取 <xref:System.Windows.Forms.Panel> 控制項，然後將它們貼到面版中。  您也可以將它們拖曳至面版。  
  
3.  \(選擇性\) 若要加入面版的框線，請設定其 <xref:System.Windows.Forms.BorderStyle> 屬性。  其中有三個選擇：<xref:System.Windows.Forms.BorderStyle>、<xref:System.Windows.Forms.BorderStyle> 和 <xref:System.Windows.Forms.BorderStyle>。  
  
## 請參閱  
 [Panel 控制項](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Panel 控制項概觀](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [如何：設定面板背景](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)