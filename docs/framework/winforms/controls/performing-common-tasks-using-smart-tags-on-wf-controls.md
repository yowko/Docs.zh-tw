---
title: 逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作
Windows Form 應用程式中建構表單和控制項，有許多工作，您將會重複執行。 以下是一些經常執行的工作，您將會遇到的：  
  
-   新增或移除索引標籤上<xref:System.Windows.Forms.TabControl>。  
  
-   將控制項固定到其父代。  
  
-   變更的方向<xref:System.Windows.Forms.SplitContainer>控制項。  
  
 為加速開發，許多控制項都提供智慧標籤，也就是即時線上功能表可讓您在設計階段執行常見工作，像是在單一的筆勢。 這些工作會呼叫*智慧標籤動詞*。  
  
 智慧標籤在設計工具中的存留期間保持附加至控制項的執行個體，並永遠都可以使用。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案  
  
-   使用智慧標籤  
  
-   啟用和停用智慧標籤  
  
 完成後，您就會了解這些重要配置功能所扮演的角色。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
1.  建立 Windows 架構應用程式專案，稱為 「 SmartTagsExample"。 如需詳細資訊，請參閱[如何：建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  選取的表單中**Windows Form 設計工具**。  
  
## <a name="using-smart-tags"></a>使用智慧標籤  
 控制項提供設計階段，仍可以使用智慧標籤。  
  
#### <a name="to-use-smart-tags"></a>若要使用智慧標籤  
  
1.  拖曳<xref:System.Windows.Forms.TabControl>從**工具箱**拖曳至表單。 請注意智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 出現在並存的<xref:System.Windows.Forms.TabControl>。  
  
2.  按一下智慧標籤圖像 （glyph）。 在字符旁邊會出現快顯功能表中選取**加入索引標籤**項目。 觀察，加入新的索引標籤頁面<xref:System.Windows.Forms.TabControl>。  
  
3.  拖曳<xref:System.Windows.Forms.TableLayoutPanel>控制項從**工具箱**拖曳至表單。  
  
4.  按一下智慧標籤圖像 （glyph）。 在字符旁邊會出現快顯功能表中選取**加入資料行**項目。 觀察，加入新的資料行<xref:System.Windows.Forms.TableLayoutPanel>控制項。  
  
5.  拖曳<xref:System.Windows.Forms.SplitContainer>控制項從**工具箱**拖曳至表單。  
  
6.  按一下智慧標籤圖像 （glyph）。 在字符旁邊會出現快顯功能表中選取**水平分隔器方向**項目。 觀察<xref:System.Windows.Forms.SplitContainer>控制項的分隔列現在是水平方向。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [逐步解說： 加入 Windows Form 元件中的智慧標籤](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
