---
title: "如何：定義分隔視窗的調整大小和位置行為 | Microsoft Docs"
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
  - "分隔視窗, 調整大小"
  - "SplitContainer 控制項 [Windows Form], 調整大小"
  - "分隔視窗, 調整大小"
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：定義分隔視窗的調整大小和位置行為
<xref:System.Windows.Forms.SplitContainer> 控制項的面板，讓他們本身可以輕易的調整大小和操作。  不過，當您要可程式化控制分隔器時 \-\- 它已定位並且可以移動他所能移動的。  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性和其他在 <xref:System.Windows.Forms.SplitContainer> 控制項上的屬性，讓您對使用者介面的行為上具有實質掌控權，以搭配您的需求。  這些屬性已列示於下表中。  
  
|名稱|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|決定分隔器是否可隨鍵盤或滑鼠移動。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定從左方或上方邊緣至可移動的分隔列間的距離 \(以像素計算\)。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定使用者可移動分隔器之最短距離 \(以像素計算\)。|  
  
 以下的範例修改了 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性以建立「快照分隔器」效果；當使用者拖曳分隔器時，它會以 10 萬畫素為單位 \(而非 default 1\) 累積。  
  
### 若要定義 SplitContainer 調整大小行為  
  
1.  在程序中，設定 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性至想要的大小，因此，分隔器的「快照」行為已達成。  
  
     在下列的範例程式碼中，表單中的 <xref:System.Windows.Forms.Form.Load> 事件，和在 <xref:System.Windows.Forms.SplitContainer> 控制項中的分隔器，已設定每次拖曳時跳 10 個畫素。  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     稍微移動分隔器至左方或右方，將會沒有可識別的效果；然而，當滑鼠指標在不論哪個方向移動超過 10 個畫素，分隔器將快照至新的位置。  
  
## 請參閱  
 <xref:System.Windows.Forms.SplitContainer>   
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>