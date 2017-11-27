---
title: "如何：在 Windows Form 建立 Windows 檔案總管樣式的介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96f2ca8189d6840bc68f063ef9b97539c24b0e6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>如何：在 Windows Form 建立 Windows 檔案總管樣式的介面
Windows 檔案總管 是常見的使用者介面方式的應用程式，因為其程度。  
  
 基本上，Windows 檔案總管已<xref:System.Windows.Forms.TreeView>控制項和<xref:System.Windows.Forms.ListView>個別面板上的控制項。 面板是透過分隔器建立可調整大小。 此控制項的排列方式可有效地顯示及瀏覽資訊。  
  
 下列步驟顯示如何排列在 Windows 檔案總管類似的表單中的控制項。 他們不要顯示如何將檔案瀏覽功能的 Windows 檔案總管應用程式。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>若要建立 Windows 檔案總管樣式的 Windows Form  
  
1.  建立新的 Windows 應用程式專案。 如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  從**工具箱**:  
  
    1.  拖曳<xref:System.Windows.Forms.SplitContainer>控制項拖曳至表單。  
  
    2.  拖曳<xref:System.Windows.Forms.TreeView>控制項放入**SplitterPanel1** (的面板<xref:System.Windows.Forms.SplitContainer>控制項標示**Panel1**)。  
  
    3.  拖曳<xref:System.Windows.Forms.ListView>控制項放入**SplitterPanel2** (的面板<xref:System.Windows.Forms.SplitContainer>控制項標示**Panel2**)。  
  
3.  按下 CTRL 鍵並依序按一下來選取所有的三個控制項。 當您選取<xref:System.Windows.Forms.SplitContainer>控制，請按一下分割線，而不是在面板。  
  
    > [!NOTE]
    >  請勿使用**全選**命令**編輯**功能表。 如果您這樣做，請在下一個步驟所需的屬性不會出現在**屬性**視窗。  
  
4.  在**屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>。  
  
5.  按 F5 執行應用程式。  
  
     此表單顯示兩個部分的使用者介面，類似於 Windows 檔案總管。  
  
    > [!NOTE]
    >  當您拖曳分隔器時，面板自動調整。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.SplitContainer>  
 [逐步解說：利用 Windows Forms 建立多窗格使用者介面](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [操作說明：定義分隔視窗的調整大小和位置行為](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [操作說明：水平分隔視窗](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
