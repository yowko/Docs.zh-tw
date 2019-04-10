---
title: HOW TO：使用 Windows Forms Label 控制項建立便捷鍵
ms.date: 03/30/2017
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
ms.openlocfilehash: ff603ee784978a8b2bab2cccd4610fc50b45d477
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171713"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>HOW TO：使用 Windows Forms Label 控制項建立便捷鍵
Windows Form<xref:System.Windows.Forms.Label>控制項可以用來定義其他控制項的便捷鍵。 當您在標籤控制項中定義的存取金鑰時，使用者可以按 ALT 鍵加上您指定要將焦點移至之控制項的定位順序中接在後面的字元。 因為標籤不會收到焦點，焦點就會自動移至定位順序中的下一個控制項中。 您可以使用這項技術，將文字方塊、 下拉式方塊、 清單方塊和資料格的存取金鑰。  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>若要指派至標籤控制項的便捷鍵  
  
1.  首先，繪製標籤，然後繪製另一個控制項。  
  
     -或-  
  
     以任何順序繪製控制項，並設定<xref:System.Windows.Forms.Control.TabIndex%2A>到小於另一個控制項標籤的屬性。  
  
2.  設定標籤<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性設`true`。  
  
3.  使用連字號 (&) 中的標籤<xref:System.Windows.Forms.Label.Text%2A>指派標籤的存取金鑰的屬性。 如需詳細資訊，請參閱 <<c0> [ 建立存取金鑰的 Windows Form 控制項](how-to-create-access-keys-for-windows-forms-controls.md)。  
  
    > [!NOTE]
    >  您可能想要在一個 label 控制項，顯示連字號，而不是使用它們來建立存取金鑰。 如果您將標籤控制項繫結至資料錄集中的資料，包括連字號的欄位，也可能會發生。 若要在標籤控制項中顯示連字號，設定<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性設`false`。 如果您想要顯示連字號，並也都有便捷鍵時，設定<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性設`true`並指出存取金鑰與一個連字號 (&) 和連字號來顯示具有兩個連字號。  
  
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

- [HOW TO：調整 Windows Forms Label 控制項的大小使符合其內容](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Label 控制項概觀](label-control-overview-windows-forms.md)
- [Label 控制項](label-control-windows-forms.md)
