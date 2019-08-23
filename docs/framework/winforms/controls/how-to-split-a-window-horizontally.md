---
title: 作法：水平分割視窗
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
ms.openlocfilehash: 7ef3fe1210ae42c52a4fd7f23633d6566bc102a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956064"
---
# <a name="how-to-split-a-window-horizontally"></a>作法：水平分割視窗
下列程式碼範例會建立將<xref:System.Windows.Forms.SplitContainer>控制項水準分割的分隔器。  
  
> [!NOTE]
> <xref:System.Windows.Forms.SplitContainer>控制項<xref:System.Windows.Forms.SplitContainer.Orientation%2A>的屬性會決定分隔器的方向, 而不是控制項本身。  
  
### <a name="to-split-a-window-horizontally"></a>水準分割視窗  
  
1. 在程式中, 將<xref:System.Windows.Forms.SplitContainer.Orientation%2A> <xref:System.Windows.Forms.SplitContainer>控制項的屬性設為<xref:System.Windows.Forms.Orientation.Horizontal>。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
