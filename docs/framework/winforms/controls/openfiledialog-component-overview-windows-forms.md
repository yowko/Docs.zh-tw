---
title: "OpenFileDialog 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35c947e3efbb9b2e5df775f83ffc6068e49c84e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.OpenFileDialog> 元件是預先設定的對話方塊。 它會是相同**開啟檔案**Windows 作業系統所公開的對話方塊。 它繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。  
  
## <a name="using-this-component"></a>使用此元件  
 作為此元件在 Windows 架構應用程式內的簡單解決方案就不需設定您自己的對話方塊中的檔案選取。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。 不過，要注意，當使用<xref:System.Windows.Forms.OpenFileDialog>元件，您必須撰寫您自己的檔案開啟邏輯。  
  
 使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示對話方塊。 您可以讓使用者多重選取的檔案，以使用開啟<xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>屬性。 此外，您可以使用<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>屬性來判斷是否唯讀核取方塊會出現在對話方塊中。 <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A>屬性會指出是否選取唯讀核取方塊。 最後，<xref:System.Windows.Forms.FileDialog.Filter%2A>屬性會設定目前檔案名稱篩選字串，以決定出現在 [檔案類型] 方塊中，在對話方塊中的選擇。  
  
 當加入至表單，<xref:System.Windows.Forms.OpenFileDialog>元件會出現在 Windows Form 設計工具底部的紙匣。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog 元件](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
