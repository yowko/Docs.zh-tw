---
title: "如何：水平分隔視窗 | Microsoft Docs"
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
  - "SplitContainer 控制項 [Windows Form], 水平分隔器"
  - "分隔視窗, 變更分隔器方向"
  - "分隔視窗, 水平"
  - "視窗, 水平分隔"
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：水平分隔視窗
下列程式碼範例會製作水平分割 <xref:System.Windows.Forms.SplitContainer> 控制項的分隔器 \(Splitter\)。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SplitContainer> 控制項的 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性會決定分隔器的方向，而不是控制項本身的方向。  
  
### 水平分隔視窗  
  
1.  在程序中，將 <xref:System.Windows.Forms.SplitContainer> 控制項的 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> 屬性設定為 <xref:System.Windows.Forms.Orientation>。  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)