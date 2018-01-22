---
title: "如何：使用設計工具，以 Windows Form 建立多窗格使用者介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1752691b3cc6809f1a5da54a01e81de2d4037d19
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>如何：使用設計工具，以 Windows Form 建立多窗格使用者介面
在下列程序中，您將建立類似搭配使用 Microsoft Outlook 中的多窗格使用者介面**資料夾** 清單中，**訊息** 窗格中，與**預覽**窗格。 這種排列方式被達成透過停駐控制項的表單來達成。  
  
 將控制項停駐，您決定哪一個父容器的邊緣控制項視窗固定至。 因此，如果您設定<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Right>，控制項的右邊緣會停駐於其父控制項的右邊緣。 此外，停駐控制項的邊緣會調整大小以符合其容器控制項。 如需有關如何<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性雖然有效，請參閱[How to： 在 Windows Form 上的停駐控制項](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)。  
  
 此程序著重於排列<xref:System.Windows.Forms.SplitContainer>和其他控制項在表單上，而非新增功能，讓模擬 Microsoft Outlook 應用程式。  
  
 若要建立此使用者介面，您將放內的所有控制項<xref:System.Windows.Forms.SplitContainer>控制項，其中包含<xref:System.Windows.Forms.TreeView>左側面板中的控制項。 右手邊的面板<xref:System.Windows.Forms.SplitContainer>控制項包含第二個<xref:System.Windows.Forms.SplitContainer>用來控制<xref:System.Windows.Forms.ListView>上述控制項<xref:System.Windows.Forms.RichTextBox>控制項。 這些<xref:System.Windows.Forms.SplitContainer>控制項可讓獨立調整表單上其他控制項的大小。 您可以調整此程序以您自己的特殊功能的自訂使用者介面中的技術。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>若要在設計階段建立的 Outlook 樣式使用者介面  
  
1.  建立新的 Windows 應用程式專案。 如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  拖曳<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**至表單。 在**屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>。  
  
3.  拖曳<xref:System.Windows.Forms.TreeView>控制項從**工具箱**的左側面板<xref:System.Windows.Forms.SplitContainer>控制項。 在**屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Left>即可顯示向下箭頭按一下時的值編輯器中的左面板。  
  
4.  拖曳其他<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**; 將它放在右側面板<xref:System.Windows.Forms.SplitContainer>控制項加入至表單。 在**屬性**視窗中，將<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Fill>和<xref:System.Windows.Forms.SplitContainer.Orientation%2A>屬性<xref:System.Windows.Forms.Orientation.Horizontal>。  
  
5.  拖曳<xref:System.Windows.Forms.ListView>控制項從**工具箱**上方面板的第二個<xref:System.Windows.Forms.SplitContainer>控制項加入至表單。 將 <xref:System.Windows.Forms.ListView> 控制項的 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
6.  拖曳<xref:System.Windows.Forms.RichTextBox>控制項從**工具箱**下方面板的第二個<xref:System.Windows.Forms.SplitContainer>控制項。 將 <xref:System.Windows.Forms.RichTextBox> 控制項的 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設為 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
     此時，如果您按 F5 執行應用程式時，此表單會顯示三個部分的使用者介面，類似於 Microsoft Outlook。  
  
    > [!NOTE]
    >  將滑鼠指標放在其中一個內分隔<xref:System.Windows.Forms.SplitContainer>控制項，您可以調整大小的內部的維度。  
  
     此時您已經在應用程式開發中，製作複雜的使用者介面。 下一個步驟是進行程式設計的應用程式本身，可能是藉由連接<xref:System.Windows.Forms.TreeView>控制項和<xref:System.Windows.Forms.ListView>某種資料來源的控制項。 如需控制項連接到資料的詳細資訊，請參閱[資料繫結和 Windows Form](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
