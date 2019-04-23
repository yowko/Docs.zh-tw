---
title: Windows Form 應用程式中的說明系統
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: 1a02271d59a59f0a6e06a652a34922ba5dcdf1f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087266"
---
# <a name="help-systems-in-windows-forms-applications"></a>Windows Form 應用程式中的說明系統
其中一個最重要的優待的您的應用程式，開發人員可以提供您的使用者是裁判的 [說明] 系統。 這是他們將會在其中開啟時使用者感到混淆、 求助對象。 提供以 Windows 為基礎的應用程式中的 [說明] 系統很容易，利用[HelpProvider 元件](../controls/helpprovider-component-windows-forms.md)。  
  
## <a name="different-types-of-help"></a>不同類型的說明  
 Windows Form <xref:System.Windows.Forms.HelpProvider> 元件用來將 HTML 說明 1.x 說明檔 (以 HTML Help Workshop 產生的 .chm 檔案，或 .htm 檔) 與 Windows 架構應用程式產生關聯。 <xref:System.Windows.Forms.HelpProvider>元件可用來提供即時線上說明 Windows Forms 上的控制項或特定的控制項。 此外，<xref:System.Windows.Forms.HelpProvider>元件可以開啟至特定的區域，例如內容、 索引或搜尋函式的資料表的主頁面的說明檔。 如需一般資訊<xref:System.Windows.Forms.HelpProvider>元件，請參閱 < [HelpProvider 元件概觀](../controls/helpprovider-component-overview-windows-forms.md)。 如需有關如何使用資訊<xref:System.Windows.Forms.HelpProvider>元件，以在 Windows Form 上顯示快顯說明請參閱[How to:顯示快顯說明](how-to-display-pop-up-help.md)。 如需使用<xref:System.Windows.Forms.ToolTip>元件，以顯示特定控制項的說明，請參閱[控制項協助使用工具提示](control-help-using-tooltips.md)。  
  
 您可以產生 HTML Help Workshop HTML 說明 1.x 檔案。 如需有關 HTML 說明檔的詳細資訊，請參閱 「 HTML Help Workshop 」 或在 MSDN 中的其他 [HTML 說明] 主題。  
  
## <a name="see-also"></a>另請參閱

- [整合 Windows Forms 中的使用者說明](integrating-user-help-in-windows-forms.md)
- [HelpProvider 元件](../controls/helpprovider-component-windows-forms.md)
- [ToolTip 元件](../controls/tooltip-component-windows-forms.md)
- [Windows Forms 概觀](../windows-forms-overview.md)
- [Windows Forms](../index.md)
