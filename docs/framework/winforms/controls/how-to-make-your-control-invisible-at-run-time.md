---
title: HOW TO：在執行階段隱藏控制項
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
ms.openlocfilehash: e9af529541a40a951d6defea180dbbef04c8f3be
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345894"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>HOW TO：在執行階段隱藏控制項
有些的時候您可能想要建立在執行階段不會察覺的使用者控制項。 例如，警示時鐘控制項可能除了警示已響起時不可見。 這可以輕鬆地藉由設定<xref:System.Windows.Forms.Control.Visible%2A>屬性。 如果<xref:System.Windows.Forms.Control.Visible%2A>屬性是`true`，您的控制項將會出現如往常。 如果`false`，將隱藏控制項。 雖然在控制項中的程式碼仍可能在隱藏時執行，但是您不能透過使用者介面控制項互動。 如果您想要建立不可見的控制項，仍會回應使用者輸入 （例如滑鼠點按），您應該建立透明的控制項。 如需詳細資訊，請參閱 <<c0> [ 為您的控制項提供透明背景](how-to-give-your-control-a-transparent-background.md)。  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>若要在執行階段隱藏控制項  
  
1. 將 <xref:System.Windows.Forms.Control.Visible%2A> 屬性設定為 `false`。  
  
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

- <xref:System.Windows.Forms.Control.Visible%2A>
- [使用 .NET Framework 開發自訂的 Windows Form 控制項](developing-custom-windows-forms-controls.md)
- [HOW TO：為控制項提供透明背景](how-to-give-your-control-a-transparent-background.md)
