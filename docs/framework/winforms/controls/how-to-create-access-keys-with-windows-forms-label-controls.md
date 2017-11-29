---
title: "如何：使用 Windows Form Label 控制項建立便捷鍵"
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
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ad6cd99a6399adea2e69cbf844b9f134d2e592e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>如何：使用 Windows Form Label 控制項建立便捷鍵
Windows Form<xref:System.Windows.Forms.Label>控制項可以用來定義其他控制項的便捷鍵。 當您定義便捷鍵的標籤控制項中時，使用者可以按 ALT 鍵加上您將焦點移至定位順序中在它後面的控制項，將指定的字元。 因為標籤不會收到焦點，焦點會自動移到定位順序中的下一個控制項。 使用這項技術，將文字方塊、 下拉式方塊、 清單方塊和資料格的存取金鑰。  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>若要指派給具有標籤控制項的便捷鍵  
  
1.  首先，繪製在標籤，然後繪製另一個控制項。  
  
     -或-  
  
     繪製控制項以任何順序，並設定<xref:System.Windows.Forms.Control.TabIndex%2A>屬性的其中一個小於另一個控制項的標籤。  
  
2.  設定標籤的<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性`true`。  
  
3.  使用連字號 (&) 中的標籤<xref:System.Windows.Forms.Label.Text%2A>屬性來指定標籤便捷鍵。 如需詳細資訊，請參閱[建立存取金鑰的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)。  
  
    > [!NOTE]
    >  您可能想要顯示的標籤控制項中的連字號，而不是使用它們來建立便捷鍵。 如果您將標籤控制項繫結至資料錄集中的資料，包括連字號的欄位，也可能會發生。 若要顯示的標籤控制項中的連字號，將<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性`false`。 如果您想要顯示連字號和也都有便捷鍵時，設定<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性`true`，表示一個連字號 ' 的存取金鑰 (&) 和連字號來顯示具有兩個連字號。  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：調整 Windows Forms Label 控制項大小以適合其內容](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [Label 控制項概觀](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Label 控制項](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
