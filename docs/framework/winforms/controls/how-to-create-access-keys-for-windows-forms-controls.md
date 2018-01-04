---
title: "如何：建立 Windows Form 控制項的便捷鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81aa68a65d09b073b117f4d96dfc06e614d68aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>如何：建立 Windows Form 控制項的便捷鍵
*便捷鍵*是功能表或功能表項目，例如按鈕控制項的標籤文字中加底線的字元。 便捷鍵，使用者可以 「 按一下 」 按鈕，然後按下 ALT 鍵組合中的預先定義的存取金鑰。 例如，按鈕會執行程序來列印表單時，如果，因此其`Text`屬性設定為"Print"，將新增連字號，再字母"P"讓字母"P"會在執行階段上底線的按鈕文字。 使用者可以執行命令與按鈕按下 ALT + P 關聯。 您不能有無法接收焦點的控制項的便捷鍵。  
  
### <a name="to-create-an-access-key-for-a-control"></a>若要建立控制項的便捷鍵  
  
1.  設定`Text`屬性為字串，包含連字號 (&) 會快顯的字母前面。  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  若要包含標題中的連字號，而不需要建立便捷鍵，包含兩個連字號 (（& s) （& s))。 單一連字號會顯示在標題中，而且沒有字元加上底線。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Button>  
 [操作說明：回應 Windows Forms Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [操作說明：設定由 Windows Forms 控制項所顯示的文字](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
