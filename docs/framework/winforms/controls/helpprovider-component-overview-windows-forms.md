---
title: HelpProvider 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: 9e8dc2ee2773b26a7bfef1da209399a8b49de9ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624117"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider 元件概觀 (Windows Form)
Windows Forms [HelpProvider](helpprovider-component-windows-forms.md)元件可用來將 HTML 說明 1.x 說明檔 （.chm 檔案，以 HTML Help Workshop 產生或.htm 檔） 與 Windows 應用程式產生關聯。 您可以提供說明各種不同的方式：  
  
- Windows Form 上的控制項提供即時線上說明。  
  
- 提供特定的對話方塊中或在對話方塊中的特定控制項上的即時線上說明。  
  
- 開啟至特定的區域，例如目錄、 索引或搜尋函式的主頁面的說明檔。  
  
## <a name="using-the-help-provider"></a>使用服務提供者  
 新增<xref:System.Windows.Forms.HelpProvider>至您的 Windows 表單的元件可讓要公開 （expose） 的說明內容的表單上的其他控制項<xref:System.Windows.Forms.HelpProvider>元件。 這可讓您提供關於您的 Windows Form 上控制項的說明。 您可以建立關聯的說明檔案<xref:System.Windows.Forms.HelpProvider>元件使用<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性。 您指定的呼叫所提供的說明類型<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>並提供值，以從<xref:System.Windows.Forms.HelpNavigator>列舉指定的控制項。 您提供的關鍵字或主題的說明藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>方法。  
  
 （選擇性） 若要將特定的說明字串與另一個控制項產生關聯，請使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>方法。 當使用者按下 F1 鍵，且焦點在控制項時，會顯示快顯視窗中使用這個方法的控制項與相關聯的字串。  
  
 如果<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>尚未設定，您必須使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>提供說明文字。 如果您已將兩者<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>和 [說明] 字串，說明根據<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>會優先使用。  
  
> [!NOTE]
>  您可能會遇到問題時指定的路徑中的說明檔案，請使用相對路徑<xref:System.Windows.Forms.Help.ShowHelp%2A>方法或<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性<xref:System.Windows.Forms.HelpProvider>控制項。 因此，請務必使用指定的說明檔的絕對檔案路徑。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 應用程式中的說明系統](../advanced/help-systems-in-windows-forms-applications.md)
