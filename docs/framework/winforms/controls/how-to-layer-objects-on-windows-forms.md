---
title: 如何：將 Windows Form 上的物件分層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 1a2a25f2e7eaa6618c0bf535a34f7dc6a28d51fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533682"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>如何：將 Windows Form 上的物件分層
當您建立複雜的使用者介面，或使用多個文件介面 (MDI) 表單時，您通常要控制項和子表單，以建立更複雜的使用者介面 (UI) 層級。 若要移動並追蹤的控制項和 windows 群組的內容中，您管理他們的疊置順序。 *疊置順序*會沿著表單 z （深度） 的表單上控制項的視覺化圖層。 視窗頂端的疊置順序，與所有其他 windows 重疊。 所有其他視窗重疊視窗底部的疊置順序。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-layer-controls-at-design-time"></a>在設計階段的圖層控制項  
  
1.  選取您想要在圖層的控制項。  
  
2.  在**格式**功能表上，指向**順序**，然後按一下 **提到最上層**或**下層**。  
  
### <a name="to-layer-controls-programmatically"></a>以程式設計方式將層級控制  
  
-   使用<xref:System.Windows.Forms.Control.BringToFront%2A>和<xref:System.Windows.Forms.Control.SendToBack%2A>管理控制項疊置順序的方法。  
  
     例如，如果<xref:System.Windows.Forms.TextBox>控制項， `txtFirstName`，是下面另一個控制項，而且您想要有在最上層，請使用下列程式碼：  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Form 支援*控制項內含項目*。 控制項內含項目都放多個控制項中包含的控制項，例如數目<xref:System.Windows.Forms.RadioButton>內控制<xref:System.Windows.Forms.GroupBox>控制項。 您可以再圖層內包含的控制項的控制項。 移動群組方塊移動了控制項，因為它們包含在它之內。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [依功能區分 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
