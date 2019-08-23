---
title: 作法：使用設計工具以 Windows Forms 建立多窗格使用者介面
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 97888a77dfc731be591d5f0284e87f45ef7dc437
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930173"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>HOW TO：使用設計工具以 Windows Forms 建立多窗格使用者介面
在下列程式中, 您將建立類似于 Microsoft Outlook 中所用的多窗格使用者介面, 以及**資料夾**清單、[**訊息**] 窗格和 [**預覽**] 窗格。 這種安排是透過將控制項與表單停駐的方式來 chiefly。

 當您停駐控制項時, 您會決定控制項已固定的父容器邊緣。 因此, 如果您將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設定為<xref:System.Windows.Forms.DockStyle.Right>, 控制項的右邊緣將停駐在其父控制項的右邊緣。 此外, 控制項的停駐邊緣也會調整大小, 以符合其容器控制項的邊緣。 如需<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性如何運作的詳細資訊, 請[參閱如何:將控制項停駐](how-to-dock-controls-on-windows-forms.md)在 Windows Forms 上。

 這個程式著重于在窗<xref:System.Windows.Forms.SplitContainer>體上排列和其他控制項, 而不是新增功能, 讓應用程式模擬 Microsoft Outlook。

 若要建立這個使用者介面, 您可以將控制項內<xref:System.Windows.Forms.SplitContainer>的所有控制項放在左側面板中, 其中<xref:System.Windows.Forms.TreeView>包含控制項。 <xref:System.Windows.Forms.SplitContainer>控制項的右側面板包含<xref:System.Windows.Forms.SplitContainer> <xref:System.Windows.Forms.ListView>具有控制項上方控制項的第二個控制項。<xref:System.Windows.Forms.RichTextBox> 這些<xref:System.Windows.Forms.SplitContainer>控制項可讓您在表單上獨立調整其他控制項的大小。 您可以調整此程式中的技術, 以製作您自己的自訂使用者介面。

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>在設計階段建立 Outlook 樣式的使用者介面

1. 建立新的 Windows 應用程式專案  > (檔案 **新增** > **專案** > **視覺效果C#** 或**Visual Basic**  > **傳統桌面** >  **Windows Forms 應用程式**)。

2. 將控制項從 [工具箱] 拖曳至表單。 <xref:System.Windows.Forms.SplitContainer> 在 [屬性] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。

3. 將控制項從 [**工具箱**] 拖曳至<xref:System.Windows.Forms.SplitContainer>控制項的左側面板。 <xref:System.Windows.Forms.TreeView> 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.SplitContainer.Dock%2A>按一下 [ <xref:System.Windows.Forms.DockStyle.Left>值編輯器] 中的左面板, 將屬性設定為, 方法是按一下向下箭號時顯示。

4. 從 [ <xref:System.Windows.Forms.SplitContainer> **工具箱**] 拖曳另一個控制項, 將它放在您新增至窗<xref:System.Windows.Forms.SplitContainer>體之控制項的右手邊面板中。 在 [**屬性**] 視窗中, <xref:System.Windows.Forms.SplitContainer.Dock%2A>將<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>設為, 並<xref:System.Windows.Forms.Orientation.Horizontal>將屬性設定為。

5. 將控制項從 [**工具箱**] 拖曳至您新增至表單<xref:System.Windows.Forms.SplitContainer>之第二個控制項的上方面板。 <xref:System.Windows.Forms.ListView> 將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 控制項的 <xref:System.Windows.Forms.ListView> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。

6. 將控制項從 [**工具箱**] 拖曳至第二個<xref:System.Windows.Forms.SplitContainer>控制項的下方面板。 <xref:System.Windows.Forms.RichTextBox> 將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 控制項的 <xref:System.Windows.Forms.RichTextBox> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。

     此時, 如果您按 F5 執行應用程式, 表單會顯示三個部分的使用者介面, 類似于 Microsoft Outlook。

    > [!NOTE]
    > 當您將滑鼠指標放在<xref:System.Windows.Forms.SplitContainer>控制項內的任何一個分隔器上方時, 您可以調整內部維度的大小。

在應用程式開發的這個階段中, 您已經製作了複雜的使用者介面。 下一步是繼續應用程式本身的設計, 也許是將<xref:System.Windows.Forms.TreeView>控制項和<xref:System.Windows.Forms.ListView>控制項連接到某種資料來源。 如需將控制項連接至資料的詳細資訊, 請參閱資料系結[和 Windows Forms](../data-binding-and-windows-forms.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
