---
title: HOW TO：鎖定 Windows Forms 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: ac02e825218f14f8479e67a79da0c86e1c9ffe11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117919"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>HOW TO：鎖定 Windows Forms 的控制項
當您設計您的 Windows 應用程式的使用者介面 (UI) 時，您可以在之後放置的位置正確，因此，您不小心移動或調整其大小設定其他屬性時，鎖定控制項。  
  
 此外，您可以鎖定及解除鎖定所有表單上的控制項，也就是很有幫助具有許多控制項的表單，或您可以解除鎖定個別控制項的功能。 一旦您已經置身在表單上放置所有控制項，可鎖定這些項目全都放在預防錯誤移動的位置。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-lock-a-control"></a>若要鎖定控制項  
  
1.  在 [**屬性**] 視窗中，按一下**鎖定**屬性，並選取`true`。 （按兩下名稱切換屬性設定）。  
  
     或者，以滑鼠右鍵按一下控制項，然後選擇**鎖定控制項**。  
  
    > [!NOTE]
    >  鎖定控制項可防止它們被拖曳至新的大小或位置，在設計介面上。 不過，您仍然可以變更的大小或位置的控制項，藉由**屬性**視窗或在程式碼。  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>若要鎖定在表單上的所有控制項  
  
1.  從**格式**功能表上，選擇**鎖定控制項**。  
  
    > [!NOTE]
    >  由於表單是控制項，此命令會鎖定，表單的大小。  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>若要解除鎖定表單上的所有鎖定的控制項  
  
1.  從**格式**功能表上，選擇**鎖定控制項**。  
  
     在表單上的所有先前鎖定的控制項現在已解除鎖定。  
  
### <a name="to-unlock-locked-controls-individually"></a>若要個別解除鎖定鎖定的控制項  
  
1.  在 [**屬性**] 視窗中，按一下**鎖定**屬性，並選取`false`。 （按兩下名稱切換屬性設定）。  
  
## <a name="see-also"></a>另請參閱

- [Windows Form 控制項](index.md)
- [排列 Windows Form 上的控制項](arranging-controls-on-windows-forms.md)
- [標記個別 Windows Form 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Form 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Form 控制項](windows-forms-controls-by-function.md)
