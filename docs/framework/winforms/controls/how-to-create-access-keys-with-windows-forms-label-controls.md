---
title: 作法：使用 Windows Forms Label 控制項建立便捷鍵
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
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950529"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>作法：使用 Windows Forms Label 控制項建立便捷鍵
Windows Forms <xref:System.Windows.Forms.Label>控制項可以用來定義其他控制項的存取金鑰。 當您在 [標籤] 控制項中定義存取金鑰時, 使用者可以按下 ALT 鍵加上您指定的字元, 將焦點移至定位順序中後面的控制項。 因為標籤無法接收焦點, 所以焦點會自動移至定位順序中的下一個控制項。 使用這項技術可將存取金鑰指派給文字方塊、下拉式方塊、清單方塊和資料格。  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>若要將存取金鑰指派給具有標籤的控制項  
  
1. 先繪製標籤, 然後再繪製另一個控制項。  
  
     -或-  
  
     以任何順序繪製控制項, 並將卷<xref:System.Windows.Forms.Control.TabIndex%2A>標的屬性設定為小於另一個控制項。  
  
2. 將標籤的<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性設定`true`為。  
  
3. 在標籤的<xref:System.Windows.Forms.Label.Text%2A>屬性中使用連字號 (&), 以指派標籤的存取金鑰。 如需詳細資訊, 請參閱[建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)。  
  
    > [!NOTE]
    > 您可能想要在標籤控制項中顯示符號, 而不是使用它們來建立存取金鑰。 如果您將標籤控制項系結至資料集記錄集中的欄位 (其中包含了符號), 就可能發生這種情況。 若要在標籤控制項中顯示符號, <xref:System.Windows.Forms.Label.UseMnemonic%2A>請將`false`屬性設定為。 如果您想要顯示符號, 而且也有存取金鑰, 請將<xref:System.Windows.Forms.Label.UseMnemonic%2A>屬性設定`true`為, 並使用一個連字號 (&) 和連字號來顯示具有兩個符號的存取金鑰。  
  
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

- [如何：調整 Windows Forms 標籤控制項的大小以符合其內容](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Label 控制項概觀](label-control-overview-windows-forms.md)
- [Label 控制項](label-control-windows-forms.md)
