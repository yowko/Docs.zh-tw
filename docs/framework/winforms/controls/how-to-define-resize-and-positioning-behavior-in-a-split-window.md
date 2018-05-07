---
title: 如何：定義分隔視窗的調整大小和位置行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 015e93fb551b8d48b8a57662b8def61c3cb46c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>如何：定義分隔視窗的調整大小和位置行為
個面板<xref:System.Windows.Forms.SplitContainer>控制項擔任也正在調整大小，並由使用者操作。 不過，可能會當您將想要以程式設計方式控制分隔器，它會定位，並且程度就可以移動它。  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性與其他屬性上的<xref:System.Windows.Forms.SplitContainer>控制項可讓您精確掌控您的使用者介面，以符合您需求的行為。 下表會列出這些屬性。  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|決定分隔器是否可以透過鍵盤或滑鼠移動。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定從左方或上方的邊緣可移動的分隔列以像素為單位的距離。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定最小距離，單位為像素，使用者可以移動分隔器。|  
  
 下列範例會修改<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性來建立 「 貼齊分隔器 」 效果; 當使用者拖曳分隔器，它會自動遞增單位的 10 個像素，而不是預設值 1。  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>若要定義 SplitContainer 調整大小行為  
  
1.  在程序，設定<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性至所需的大小達到 '貼齊' 分隔器的行為。  
  
     在下列程式碼範例中，表單內<xref:System.Windows.Forms.Form.Load>事件、 分隔器內<xref:System.Windows.Forms.SplitContainer>控制設為跳 10 個像素拖曳時。  
  
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
  
     (Visual C#)下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     稍微向左或向右移動分隔器不會影響差別。不過，當滑鼠指標進入任一方向的 10 個像素，分隔器會貼齊至新位置中。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
