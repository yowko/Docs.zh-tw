---
title: 開發控制項的基本概念
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: fab0a76e2f9fdb7e2f89e9d6a10dd9c522a6d8e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739912"
---
# <a name="windows-forms-control-development-basics"></a>Windows Form 控制項開發的基本概念
Windows Forms 控制項是直接或間接衍生自 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>的類別。 下列清單說明開發 Windows Forms 控制項的常見案例：  
  
- 結合現有的控制項來撰寫複合控制項。  
  
     複合控制項會封裝可重複使用為控制項的使用者介面。 複合控制項的一個範例是由一個文字方塊和一個 [重設] 按鈕所組成的控制項。 視覺化設計工具提供建立複合控制項的豐富支援。 若要撰寫複合控制項，請從 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>衍生。 基類 <xref:System.Windows.Forms.UserControl> 會提供子控制項的鍵盤路由，並可讓子控制項當做群組來使用。 如需詳細資訊，請參閱[開發複合 Windows Forms 控制項](developing-a-composite-windows-forms-control.md)。  
  
- 擴充現有的控制項以進行自訂，或加入其功能。  
  
     無法變更其色彩的按鈕，以及具有額外屬性的按鈕，以追蹤已按下的次數，這是擴充控制項的範例。 您可以自訂任何 Windows Forms 控制項，方法是從它衍生並覆寫或加入屬性、方法和事件。  
  
- 撰寫不會結合或擴充現有控制項的控制項。  
  
     在此案例中，從基類 <xref:System.Windows.Forms.Control>衍生您的控制項。 您可以新增和覆寫基類的屬性、方法和事件。 若要開始使用，請參閱[如何：開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)。  
  
 Windows Forms 控制項 <xref:System.Windows.Forms.Control>的基類，可提供在用戶端 Windows 應用程式中顯示視覺效果所需的管道。 <xref:System.Windows.Forms.Control> 提供視窗控制碼、處理訊息路由，並提供滑鼠和鍵盤事件，以及其他許多使用者介面事件。 它提供了「先進的版面配置」，並具有視覺顯示特有的屬性，例如 <xref:System.Windows.Forms.Control.ForeColor%2A>、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.Height%2A>、<xref:System.Windows.Forms.Control.Width%2A>及其他許多專案。 此外，它還提供與 ActiveX 控制項的安全性、執行緒支援和互通性。 因為基底類別提供了非常多的基礎結構，所以開發您自己的 Windows Forms 控制項相對容易。  
  
## <a name="see-also"></a>請參閱

- [操作說明：開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)
- [開發複合 Windows Forms 控制項](developing-a-composite-windows-forms-control.md)
- [操作說明：建立顯示進度的 Windows Forms 控制項](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
