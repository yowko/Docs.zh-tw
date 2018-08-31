---
title: 如何：使用設計工具，以 Windows Form 建立多窗格使用者介面
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 9c8cab952fd9d0c58380a308dd360dcedb2ea8f1
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254196"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>如何：使用設計工具，以 Windows Form 建立多窗格使用者介面
在下列程序中，您將建立類似於使用 Microsoft Outlook 中所使用的多窗格使用者介面**資料夾** 清單中，**訊息**窗格中，和**預覽**  窗格。 這種排列方式是主要透過停駐控制項的表單來達成的。  
  
 當您將控制項停駐時，您決定父容器的邊緣控制項固定至。 因此，如果您設定<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Right>，右邊緣的控制項所停駐到其父控制項的右邊緣。 此外，停駐控制項的邊緣會調整大小以符合其容器控制項。 如需有關如何<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性雖然有效，請參閱[如何： 在 Windows Forms 上的停駐控制項](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)。  
  
 此程序著重於排列<xref:System.Windows.Forms.SplitContainer>和其他控制項在表單上，而不加入讓模仿 Microsoft Outlook 應用程式的功能。  
  
 若要建立此使用者介面，您會放置內的所有控制項<xref:System.Windows.Forms.SplitContainer>控制項，包含<xref:System.Windows.Forms.TreeView>左面板中的控制項。 右側面板中的<xref:System.Windows.Forms.SplitContainer>控制項包含第二個<xref:System.Windows.Forms.SplitContainer>控制項取代<xref:System.Windows.Forms.ListView>控制上述<xref:System.Windows.Forms.RichTextBox>控制項。 這些<xref:System.Windows.Forms.SplitContainer>控制項可讓您獨立調整大小的表單上的其他控制項。 您可以調整此程序來製作您自己的自訂使用者介面中的技術。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>若要在設計階段建立的 Outlook 樣式使用者介面  
  
1.  建立新的 Windows 應用程式專案 (**檔案** > **新增** > **專案** > **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。  
  
2.  拖曳<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**至表單。 在 **屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>。  
  
3.  拖曳<xref:System.Windows.Forms.TreeView>控制項從**工具箱**左側面板的<xref:System.Windows.Forms.SplitContainer>控制項。 在 **屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Left>依序按一下左側面板中按一下向下箭號時所顯示的值編輯器。  
  
4.  將另一個<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**; 將它放在右側面板中的<xref:System.Windows.Forms.SplitContainer>您加入至您的表單控制項。 在**屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Fill>並<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性設<xref:System.Windows.Forms.Orientation.Horizontal>。  
  
5.  拖曳<xref:System.Windows.Forms.ListView>控制項從**工具箱**上方面板，第二個<xref:System.Windows.Forms.SplitContainer>您加入至您的表單控制項。 將 <xref:System.Windows.Forms.ListView> 控制項的 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
6.  拖曳<xref:System.Windows.Forms.RichTextBox>控制項從**工具箱**第二個較低的面板<xref:System.Windows.Forms.SplitContainer>控制項。 將 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
     此時，如果您按 F5 執行應用程式時，表單會顯示三個部分使用者介面，類似於 Microsoft Outlook。  
  
    > [!NOTE]
    >  將滑鼠指標放在分隔器透過<xref:System.Windows.Forms.SplitContainer>控制項，您可以調整大小的內部的維度。  
  
     此時在應用程式開發中，您已經製作精緻的使用者介面。 下一個步驟繼續進行應用程式本身，程式設計可能是藉由連接<xref:System.Windows.Forms.TreeView>控制項和<xref:System.Windows.Forms.ListView>到某種資料來源的控制項。 如需有關如何連接至資料控制項的詳細資訊，請參閱[資料繫結和 Windows Form](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
