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
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965687"
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider 元件概觀 (Windows Form)
Windows Forms [HelpProvider](helpprovider-component-windows-forms.md)元件是用來將 html help 1.x 說明檔 (使用 Html 說明研討會產生的 .chm 檔案或 .htm 檔案) 與您的 Windows 應用程式建立關聯。 您可以透過各種方式來提供說明:  
  
- 提供 Windows Forms 上控制項的即時線上說明。  
  
- 在特定對話方塊或對話方塊上的特定控制項上提供即時線上說明。  
  
- 開啟說明檔至特定區域, 例如目錄的主頁面、索引或搜尋函數。  
  
## <a name="using-the-help-provider"></a>使用說明提供者  
 將元件新增至您的 Windows form, 可讓表單上的其他控制項公開該<xref:System.Windows.Forms.HelpProvider>元件的說明屬性。 <xref:System.Windows.Forms.HelpProvider> 這可讓您為 Windows Form 上的控制項提供說明。 您可以<xref:System.Windows.Forms.HelpProvider> <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>使用屬性, 讓說明檔與元件產生關聯。 您可以藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>並提供<xref:System.Windows.Forms.HelpNavigator>來自指定控制項之列舉的值, 來指定所提供的說明類型。 藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>方法, 您可以提供關鍵字或主題來取得協助。  
  
 (選擇性) 若要讓特定的說明字串與另一個控制項<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>產生關聯, 請使用方法。 當使用者按下 F1 鍵時, 使用這個方法與控制項建立關聯的字串會顯示在快顯視窗中, 而控制項則具有焦點。  
  
 如果<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>尚未設定, 則您必須使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>來提供解說文字。 如果您同時<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>設定了和說明字串, 將會優先使用<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>以為基礎的說明。  
  
> [!NOTE]
> 在<xref:System.Windows.Forms.Help.ShowHelp%2A> <xref:System.Windows.Forms.HelpProvider>控制項的方法或<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性中指定說明檔的路徑時, 您可能會遇到使用相對路徑的問題。 因此, 請務必使用絕對檔案路徑來指定說明檔。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 應用程式中的說明系統](../advanced/help-systems-in-windows-forms-applications.md)
