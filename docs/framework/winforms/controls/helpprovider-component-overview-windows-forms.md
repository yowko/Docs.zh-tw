---
title: "HelpProvider 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23a9db5f7c5286eaab50f2499845f7294af878ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a>HelpProvider 元件概觀 (Windows Form)
Windows Form [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)元件可用來將 HTML 說明 1.x 說明檔 （以 HTML Help Workshop 產生的.chm 檔案或.htm 檔） 與 Windows 應用程式產生關聯。 您可以提供各種不同的方式說明：  
  
-   提供 Windows Form 上控制項的即時線上說明。  
  
-   提供特定的對話方塊或在對話方塊中的特定控制項上的即時線上說明。  
  
-   開啟說明檔案以特定區域，例如目錄、 索引或搜尋函式的主頁面。  
  
## <a name="using-the-help-provider"></a>使用說明提供者  
 加入<xref:System.Windows.Forms.HelpProvider>加入 Windows Form 的元件可讓要公開 （expose） 的說明內容的表單上的其他控制項<xref:System.Windows.Forms.HelpProvider>元件。 這可讓您提供關於 Windows Form 上控制項的說明。 您可以建立關聯的說明檔案<xref:System.Windows.Forms.HelpProvider>元件使用<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性。 您指定的呼叫所提供的說明類型<xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A>並提供的值從<xref:System.Windows.Forms.HelpNavigator>列舉指定之控制項。 您提供的關鍵字或主題的說明藉由呼叫<xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>方法。  
  
 （選擇性） 若要將特定的 [說明] 字串與另一個控制項產生關聯，請使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>方法。 當使用者按下 F1 鍵，且焦點在控制項時，您會使用這個方法的控制項關聯的字串會顯示快顯視窗中。  
  
 如果<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>是否尚未設定，您必須使用<xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>提供說明文字。 如果您同時設定<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>的說明字串，說明根據<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>更高的優先順序。  
  
> [!NOTE]
>  您可能會遇到問題使用相對路徑時指定的說明檔的路徑中<xref:System.Windows.Forms.Help.ShowHelp%2A>方法或<xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>屬性<xref:System.Windows.Forms.HelpProvider>控制項。 在這種情況，請務必使用指定的說明檔的絕對檔案路徑。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 應用程式中的說明系統](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)
