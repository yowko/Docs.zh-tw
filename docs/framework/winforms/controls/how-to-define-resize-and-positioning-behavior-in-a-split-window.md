---
title: HOW TO：定義分割視窗的調整大小和位置行為
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 8cdcfdfaa135a92ed6a6e96d4a72de2c97f2493d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328669"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>HOW TO：定義分割視窗的調整大小和位置行為
個面板<xref:System.Windows.Forms.SplitContainer>控制項讓他們也正在調整大小，並由使用者操作。 不過，可能會當您將想要以程式設計方式控制分隔器，其中的位置，而哪種程度移動。  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性和其他屬性，在<xref:System.Windows.Forms.SplitContainer>控制項讓您精確地控制您的使用者介面，以符合您需求的行為。 下表會列出這些屬性。  
  
|名稱|描述|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> 屬性|判斷是否透過鍵盤或滑鼠可移動的分隔器。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> 屬性|決定在可移動的分隔器列的像素的左邊緣或上邊緣的距離。|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> 屬性|決定的最短距離，單位為像素，使用者可以移動分隔器。|  
  
 下列範例會修改<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性來建立 「 貼齊分隔器 」 的效果; 當使用者拖曳分隔器，就會自動遞增單位為 10 個像素，而不是預設值 1。  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>若要定義 SplitContainer 調整大小行為  
  
1. 在程序，設定<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>屬性至所需的大小，以便達成 '貼齊' 起的分隔器行為。  
  
     在下列的程式碼範例中，而表單內<xref:System.Windows.Forms.Form.Load>事件，在分隔器<xref:System.Windows.Forms.SplitContainer>控制項跳 10 個像素拖曳時設定。  
  
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
  
     向左或向右稍微移動分隔器會有任何顯著的作用中;不過，當滑鼠指標進入任一方向的 10 個像素，分隔器會貼齊至新位置中。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
