---
title: Windows Form 控制項開發的基本概念
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: 21b8b08e56e8b4d48fb738b86247d3f04dc4150b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086438"
---
# <a name="windows-forms-control-development-basics"></a>Windows Form 控制項開發的基本概念
將 Windows Forms 控制項是直接或間接衍生自類別<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。 下列清單描述開發 Windows Form 控制項的常見案例：  
  
-   合併現有的控制要撰寫複合控制項。  
  
     複合控制項封裝可以重複使用，做為控制項的使用者介面。 複合控制項的範例是包含文字方塊和重設 按鈕的控制項。 視覺化設計工具提供用於建立複合控制項的豐富支援。 若要撰寫複合控制項，衍生自<xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>。 基底類別<xref:System.Windows.Forms.UserControl>提供鍵盤路由子控制項，並讓子系控制項做為群組運作。 如需詳細資訊，請參閱[開發複合 Windows Forms 控制項](developing-a-composite-windows-forms-control.md)。  
  
-   擴充現有控制項來自訂它或將其功能。  
  
     無法變更其色彩的按鈕和一個按鈕，有額外的屬性會追蹤已按下的次數是擴充控制項的範例。 您可以從中衍生並覆寫或新增屬性、 方法和事件，以自訂任何 Windows Form 控制項。  
  
-   撰寫控制項不會合併或擴充現有的控制項。  
  
     在此案例中，您的控制項的基底類別衍生<xref:System.Windows.Forms.Control>。 您可以新增，以及覆寫屬性、 方法和事件的基底類別。 若要開始，請參閱[How to:開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)。  
  
 Windows Form 控制項的基底類別<xref:System.Windows.Forms.Control>，提供所需的用戶端以 Windows 為基礎的應用程式中的視覺顯示的配管。 <xref:System.Windows.Forms.Control> 提供視窗控制代碼，會處理訊息路由，並提供滑鼠和鍵盤事件，以及許多其他的使用者介面事件。 它提供進階版面配置，並且有特定的視覺顯示 屬性，例如<xref:System.Windows.Forms.Control.ForeColor%2A>， <xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.Height%2A>， <xref:System.Windows.Forms.Control.Width%2A>，和許多其他因素。 此外，還會提供安全性，執行緒支援，以及將 ActiveX 控制項的互通性。 因為基底類別提供了非常多的基礎結構，所以開發您自己的 Windows Forms 控制項相對容易。  
  
## <a name="see-also"></a>另請參閱

- [如何：開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)
- [開發複合 Windows Forms 控制項](developing-a-composite-windows-forms-control.md)
- [如何：建立顯示進度的 Windows Form 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
