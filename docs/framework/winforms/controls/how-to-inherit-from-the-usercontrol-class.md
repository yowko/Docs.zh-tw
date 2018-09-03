---
title: 如何：繼承自 UserControl 類別
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 5a826b9fc68bebfa32049a38899ddffaacd25607
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488127"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>如何：繼承自 UserControl 類別
若要結合一或多個 Windows Forms 控制項的功能與自訂程式碼，您可以建立「使用者控制項」。 使用者控制項可結合快速控制項開發、標準 Windows Forms 控制項功能，以及自訂屬性和方法的各種用途。 當您開始建立使用者控制項時，您會看到吸引人的設計工具，您可以在其上放置標準 Windows Forms 控制項。 這些控制項會保留其所有固有功能，以及標準控制項的外觀和行為 (外觀及操作)。 不過，這些控制項一旦內建於使用者控制項，您就無法再透過程式碼使用它們。 使用者控制項會進行自己的繪製，也會處理與控制項相關聯的所有基本功能。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-create-a-user-control"></a>建立使用者控制項  
  
1.  建立新的 [Windows 控制項程式庫] 專案。  
  
     使用空白使用者控制項來建立新專案。  
  
2.  將控制項從 [工具箱] 的 [Windows Forms] 索引標籤拖曳到您的設計工具。  
  
3.  這些控制項的放置和設計方式應該依照您希望它們出現於最終使用者控制項的方式。 如果您想要讓開發人員存取組成控制項，您必須將它們宣告為公用，或選擇性地公開組成控制項的屬性。 如需詳細資訊，請參閱[如何：公開組成控制項的屬性](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)。  
  
4.  實作您的控制項將併入的任何自訂方法或屬性。  
  
5.  按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。 如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
## <a name="see-also"></a>另請參閱  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [操作說明：繼承自 Control 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [操作說明：繼承自現有的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [操作說明：撰寫 Windows Forms 的控制項](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [操作說明：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
