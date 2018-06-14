---
title: 如何：在執行階段期間隱藏控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
ms.openlocfilehash: 51e804c7f01b55ed7504837042b6c32bf47d9405
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532408"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>如何：在執行階段期間隱藏控制項
但有些的時候，當您可能想要建立使用者控制項在執行階段不可見。 例如，鬧鐘控制項可能不可見，除了當警示已響起。 輕鬆達成設定<xref:System.Windows.Forms.Control.Visible%2A>屬性。 如果<xref:System.Windows.Forms.Control.Visible%2A>屬性是`true`，控制項將顯示為一般。 如果`false`，將隱藏控制項。 雖然在隱藏時，仍可執行程式碼，在控制項中的，您無法透過使用者介面控制項互動。 如果您想要建立不可見的控制項仍然會回應使用者輸入 （例如滑鼠點按動作），您應該建立透明的控制項。 如需詳細資訊，請參閱[為您的控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)。  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>若要在執行階段隱藏控制項  
  
1.  將 <xref:System.Windows.Forms.Control.Visible%2A> 屬性設定為 `false`。  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [使用 .NET Framework 開發自訂的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [操作說明：為控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
