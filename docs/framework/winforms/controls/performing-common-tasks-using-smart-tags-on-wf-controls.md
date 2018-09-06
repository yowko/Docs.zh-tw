---
title: 逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: d1c69d2e9e89e0a4fed767216e8743a0ac9ac81d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741129"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
您建構表單和控制項的 Windows Forms 應用程式時，有許多重複執行的工作。 以下是一些經常執行的工作就會發生：  
  
-   新增或移除工作索引標籤上<xref:System.Windows.Forms.TabControl>。  
  
-   將控制項固定到其父代。  
  
-   變更的方向<xref:System.Windows.Forms.SplitContainer>控制項。  
  
 若要加快開發的速度，許多控制項都提供智慧標籤，也就是可讓您在設計階段執行常見工作，像是這些功能是以單一軌跡的即時線上功能表。 這些工作會呼叫*智慧標籤動詞*。  
  
 智慧標籤的設計工具中的存留期保持附加至控制項執行個體，並永遠都可以使用。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案  
  
-   使用智慧標籤  
  
-   啟用和停用智慧標籤  
  
 完成後，您就會了解這些重要配置功能所扮演的角色。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立以 Windows 為基礎的應用程式專案，稱為 「 SmartTagsExample"(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。  
  
2.  選取中的表單**Windows Form 設計工具**。  
  
## <a name="using-smart-tags"></a>使用智慧標籤  
 在設計階段，它們提供的控制項上，都可以使用智慧標籤。  
  
#### <a name="to-use-smart-tags"></a>若要使用智慧標籤  
  
1.  拖曳<xref:System.Windows.Forms.TabControl>從**工具箱**拖曳至表單。 請注意智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，會出現在並存的<xref:System.Windows.Forms.TabControl>。  
  
2.  按一下智慧標籤圖像 （glyph）。 在字符旁邊會出現快顯功能表中，選取**加入索引標籤**項目。 觀察新的索引標籤頁加入<xref:System.Windows.Forms.TabControl>。  
  
3.  拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。  
  
4.  按一下智慧標籤圖像 （glyph）。 在字符旁邊會出現快顯功能表中，選取**加入資料行**項目。 觀察出新的資料行已經新增到<xref:System.Windows.Forms.TableLayoutPanel>控制項。  
  
5.  拖曳<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**拖曳至表單。  
  
6.  按一下智慧標籤圖像 （glyph）。 在字符旁邊會出現快顯功能表中，選取**水平分隔器方向**項目。 觀察<xref:System.Windows.Forms.SplitContainer>控制的分隔器列現在是水平方向。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [逐步解說： 將智慧標籤加入至 Windows Form 元件](https://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
