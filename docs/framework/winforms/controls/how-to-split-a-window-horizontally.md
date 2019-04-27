---
title: HOW TO：水平分割視窗
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
ms.openlocfilehash: a43d632a82678f362a1cdf6b3ee4486a8db5adde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012928"
---
# <a name="how-to-split-a-window-horizontally"></a>HOW TO：水平分割視窗
下列程式碼範例會將分割的分隔器<xref:System.Windows.Forms.SplitContainer>控制水平。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性<xref:System.Windows.Forms.SplitContainer>控制項會決定起的分隔器，而不是控制項本身的方向。  
  
### <a name="to-split-a-window-horizontally"></a>若要水平分隔視窗  
  
1. 在程序中，設定<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性<xref:System.Windows.Forms.SplitContainer>若要控制<xref:System.Windows.Forms.Orientation.Horizontal>。  
  
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
