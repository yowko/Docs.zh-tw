---
title: HOW TO：在 Windows Forms 中建立 Windows 檔案總管樣式的介面
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: dd70feaba29e29748ac56729632fa359582a6914
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327369"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>HOW TO：在 Windows Forms 中建立 Windows 檔案總管樣式的介面
Windows 檔案總管會是應用程式的一般使用者介面選擇，因為其準備好的熟悉度。  
  
 基本上，Windows 檔案總管已<xref:System.Windows.Forms.TreeView>控制項和<xref:System.Windows.Forms.ListView>在個別的面板上的控制項。 面板是透過分隔器建立可調整大小。 此控制項的排列方式可有效地顯示和瀏覽資訊。  
  
 下列步驟示範如何在 Windows 檔案總管類似的表單中排列控制項。 它們不會出現如何新增 Windows 檔案總管應用程式的檔案瀏覽功能。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>若要建立 Windows 檔案總管樣式的 Windows 表單  
  
1. 建立新的 Windows 應用程式專案 (**檔案** > **新增** > **專案** > **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。  
  
2. 從**工具箱**:  
  
    1.  拖曳<xref:System.Windows.Forms.SplitContainer>控制項拖曳至表單。  
  
    2.  拖曳<xref:System.Windows.Forms.TreeView>程式控制**SplitterPanel1** (的面板<xref:System.Windows.Forms.SplitContainer>控制標記**Panel1**)。  
  
    3.  拖曳<xref:System.Windows.Forms.ListView>程式控制**SplitterPanel2** (的面板<xref:System.Windows.Forms.SplitContainer>控制標記**Panel2**)。  
  
3. 按下 CTRL 鍵並依序按一下以選取所有的三個控制項。 當您選取<xref:System.Windows.Forms.SplitContainer>控制項中按一下 分隔器列，而不是面板。  
  
    > [!NOTE]
    >  請勿使用**全選**命令**編輯**功能表。 如果您這樣做，請在下一個步驟中所需的屬性不會出現在**屬性**視窗。  
  
4. 在 [屬性]  視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
5. 按 F5 執行應用程式。  
  
     此表單會顯示兩個部分使用者介面，類似於 Windows 檔案總管。  
  
    > [!NOTE]
    >  當您拖曳分隔器時，重新調整大小的面板本身。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [如何：利用 Windows Form 建立多窗格使用者介面](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [如何：定義調整大小和位置行為在分隔視窗](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [如何：水平分隔視窗](how-to-split-a-window-horizontally.md)
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
