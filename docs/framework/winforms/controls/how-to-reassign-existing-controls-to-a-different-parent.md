---
title: "如何：將現有控制項重新指派至不同的父代 | Microsoft Docs"
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
  - "容器控制項, Windows Forms"
  - "版面配置 [Windows Forms], 調整大小"
  - "版面配置 [Windows Forms], 子控制項"
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：將現有控制項重新指派至不同的父代
您可以將表單上現有的控制項指派給新的容器控制項。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。 若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。 如需詳細資訊，請參閱[在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### 將現有控制項重新指派至不同的父代  
  
1.  從 \[工具箱\] 將三個 <xref:System.Windows.Forms.Button> 控制項拖曳至表單。  
  
     將它們放在相鄰的位置，但不要對齊。  
  
2.  按一下 \[工具箱\] 的 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。  
  
     請勿將圖示拖曳到表單上。  
  
3.  將滑鼠指標靠近三個 <xref:System.Windows.Forms.Button> 控制項。  
  
     指標會變成十字形狀並附有 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項圖示。  
  
4.  按住滑鼠按鈕。  
  
5.  拖曳滑鼠指標以繪製 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項的外框。  
  
6.  繪製三個 <xref:System.Windows.Forms.Button> 控制項的外框。  
  
7.  放開滑鼠按鈕。  
  
     三個 <xref:System.Windows.Forms.Button> 控制項現在都已插入 <xref:System.Windows.Forms.FlowLayoutPanel> 控制項中。  
  
## 請參閱  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)