---
title: "Windows Form 控制項開發的基本概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcf06f4dc0d8c70ae85d5add5a2fee078238d5e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-control-development-basics"></a>Windows Form 控制項開發的基本概念
Windows Form 控制項是一個類別，是直接或間接衍生自<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。 下列清單描述開發 Windows Form 控制項的常見案例：  
  
-   若要撰寫複合控制項結合現有的控制。  
  
     複合控制項封裝可以重複使用，做為控制項的使用者介面。 複合控制項的範例是包含文字方塊和重設按鈕控制項。 視覺化設計工具提供豐富的支援，如建立複合控制項。 若要撰寫複合控制項，衍生自<xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>。 基底類別<xref:System.Windows.Forms.UserControl>提供鍵盤路徑的子控制項，並讓做為群組的子控制項。 如需詳細資訊，請參閱[開發複合 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)。  
  
-   擴充現有控制項進行自訂，或加入至其功能。  
  
     無法變更其色彩的按鈕和按鈕有額外的屬性，以追蹤已按下的次數會擴充控制項的範例。 您可以自訂任何 Windows Form 控制項衍生自它和覆寫或新增屬性、 方法和事件。  
  
-   撰寫不結合或擴充現有控制項的控制項。  
  
     在此案例中，衍生您的控制項的基底類別從<xref:System.Windows.Forms.Control>。 您可以新增，以及覆寫屬性、 方法和事件的基底類別。 若要開始使用，請參閱[How to： 開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)。  
  
 Windows Form 控制項的基底類別<xref:System.Windows.Forms.Control>，提供所需的用戶端 Windows 架構應用程式中的視覺顯示。 <xref:System.Windows.Forms.Control>提供的視窗控制代碼，會處理訊息路由，並可提供滑鼠和鍵盤事件，以及許多其他的使用者介面事件。 它提供進階的版面配置，而且有特定的視覺顯示 屬性，例如<xref:System.Windows.Forms.Control.ForeColor%2A>， <xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.Height%2A>， <xref:System.Windows.Forms.Control.Width%2A>，及其他等等。 此外，它會提供安全性，執行緒處理的支援，以及 ActiveX 控制項與互通性。 因為基底類別提供了非常多的基礎結構，所以開發您自己的 Windows Forms 控制項相對容易。  
  
## <a name="see-also"></a>請參閱  
 [操作說明：開發簡單的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [開發複合 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [操作說明：建立顯示進度的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
