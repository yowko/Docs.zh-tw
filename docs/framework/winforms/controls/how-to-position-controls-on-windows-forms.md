---
title: "如何：將控制項定位在 Windows Form 上 | Microsoft Docs"
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
  - "Location"
  - "Location.Y"
  - "Location.X"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form]"
  - "控制項 [Windows Form], 移動"
  - "控制項 [Windows Form], 位置"
  - "對齊線"
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 如何：將控制項定位在 Windows Form 上
若要調整控制項的位置，請使用 Windows Form 設計工具，或指定 <xref:System.Windows.Forms.Control.Location%2A> 屬性。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在 Windows Form 設計工具的設計介面上調整控制項的位置  
  
-   用滑鼠拖曳控制項到適當的位置。  
  
    > [!NOTE]
    >  選取控制項並用方向鍵移動它，使其位置更精確。  此外，*對齊線*也可以協助您精確地在表單上放置控制項。  如需詳細資訊，請參閱[逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。  
  
### 若要使用屬性視窗調整控制項的位置  
  
1.  按一下要調整位置的控制項。  
  
2.  在 \[**屬性**\] 視窗中，輸入 <xref:System.Windows.Forms.Control.Location%2A> 屬性的值並以逗號分開，以便在容器 \(Container\) 中調整控制項的位置。  
  
     第一個數字 \(X\) 是與容器左框線之間的距離；第二個數字 \(Y\) 是與容器面積上方框線之間的距離，並以像素為單位。  
  
    > [!NOTE]
    >  您可以展開 <xref:System.Windows.Forms.Control.Location%2A> 屬性，以便分別輸入 **X** 及 **Y** 值。  
  
### 若要以程式設計方式調整控制項的位置  
  
1.  將控制項的 <xref:System.Windows.Forms.Control.Location%2A> 屬性設為一個 <xref:System.Drawing.Point>。  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  使用 <xref:System.Windows.Forms.Control.Left%2A> 子屬性，改變控制項位置的 X 座標。  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### 若要以程式設計方式增加控制項的位置  
  
1.  設定 <xref:System.Windows.Forms.Control.Left%2A> 子屬性來增加控制項的 X 座標。  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  使用 <xref:System.Windows.Forms.Control.Location%2A> 屬性來同時設定控制項的 X 及 Y 位置。  要個別設定位置，使用控制項的 <xref:System.Windows.Forms.Control.Left%2A> \(**X**\) 或 <xref:System.Windows.Forms.Control.Top%2A> \(**Y**\) 子屬性。  請勿隱含設定 <xref:System.Drawing.Point> 結構 \(表示按鈕的位置\) 的 X 及 Y 座標，因為這個結構包含了按鈕座標的複本。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [逐步解說：使用對齊線排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [依功能區分 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)   
 [How to: Set the Screen Location of Windows Forms](http://msdn.microsoft.com/zh-tw/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)