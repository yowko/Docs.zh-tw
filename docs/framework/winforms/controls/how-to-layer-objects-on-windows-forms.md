---
title: "如何：將 Windows Form 上的物件分層 | Microsoft Docs"
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
  - "控制項 [Windows Form], 分層"
  - "控制項 [Windows Form], 位置"
  - "Windows Form 控制項, 分層"
  - "疊置順序"
  - "疊置順序"
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：將 Windows Form 上的物件分層
在建立複雜的使用者介面，或使用多重文件介面 \(MDI\) 表單時，通常需要將控制項和子表單層級化，以建立更複雜的使用者介面 \(UI\)。  若要移動和追蹤上下文群組內的控制項和視窗，您可以利用其疊置順序來操控。  「*疊置順序*」是延著表單 Z 軸 \(深度\) 為表單上的控制項進行視覺分層。  疊置順序最上層的視窗覆蓋於其他的視窗之上。  所有其他的視窗則覆蓋於疊置順序最底層的視窗。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在設計階段分層控制項  
  
1.  選取您想要分層的控制項。  
  
2.  在 \[**格式**\] 功能表上指向 \[**順序**\]，然後按一下 \[**提到最上層**\] 或 \[**移到最下層**\]。  
  
### 若要以程式設計方式配置控制項  
  
-   使用 <xref:System.Windows.Forms.Control.BringToFront%2A> 和 <xref:System.Windows.Forms.Control.SendToBack%2A> 方法來操作控制項的疊置順序 \(Z\-order\)。  
  
     例如，如果 <xref:System.Windows.Forms.TextBox> 控制項 `txtFirstName` 位於另一個控制項下方，且您想將它擺在上面，就可以使用下列程式碼：  
  
    ```vb  
    txtFirstName.BringToFront()  
  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Form 支援「*控制項內含項目*」。  控制項內含項目指的是將一些控制項擺在包含控制項之內，例如有一些 <xref:System.Windows.Forms.RadioButton> 控制項位於 <xref:System.Windows.Forms.GroupBox> 控制項之內。  您可以在包含控制項之內將控制項層級化。  移動群組方塊也就移動了控制項，因為控制項包含在其中。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [依功能區分 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)