---
title: 如何：鎖定 Windows Form 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: f05da53f134f13bf5edbbe7ab8c5973f79bbca4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-lock-controls-to-windows-forms"></a>如何：鎖定 Windows Form 的控制項
當您設計 Windows 應用程式的使用者介面 (UI) 時，您可以在之後的位置正確，如此您不小心移動或調整其大小，設定其他屬性時，鎖定控制項。  
  
 此外，您可以鎖定與解除鎖定所有表單上的控制項，這可能會很有幫助的表單具有許多控制項，或您可以解除鎖定個別控制項。 一旦您在表單上所需的位置放置所有控制項，可鎖定這些所有方式可避免錯誤的移動。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-lock-a-control"></a>若要鎖定控制項  
  
1.  在**屬性**視窗中，按一下 **鎖定**屬性，並選取`true`。 （按兩下名稱切換屬性設定）。  
  
     或者，以滑鼠右鍵按一下控制項，然後選擇**鎖定控制項**。  
  
    > [!NOTE]
    >  鎖定控制項可防止它們在設計介面上拖曳至新的大小或位置。 不過，您仍然可以變更的大小或位置的控制項，藉由**屬性**視窗或在程式碼。  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>鎖定在表單上的所有控制項  
  
1.  從**格式**功能表上，選擇**鎖定控制項**。  
  
    > [!NOTE]
    >  由於表單是控制項，此命令會鎖定，表單的大小。  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>若要解除鎖定所有鎖定的表單上的控制項  
  
1.  從**格式**功能表上，選擇**鎖定控制項**。  
  
     在表單上的所有先前鎖定的控制項現在會解除鎖定。  
  
### <a name="to-unlock-locked-controls-individually"></a>若要個別解除鎖定的控制項  
  
1.  在**屬性**視窗中，按一下 **鎖定**屬性，並選取`false`。 （按兩下名稱切換屬性設定）。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [排列 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [依功能區分 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
