---
title: HOW TO：建立 Windows Forms 控制項的便捷鍵
ms.date: 03/30/2017
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
ms.openlocfilehash: e6c829553163359301bad2cd896fc43562ee8069
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334454"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>HOW TO：建立 Windows Forms 控制項的便捷鍵
*便捷鍵*是功能表、 功能表項目，或按鈕等控制項的標籤文字中加上底線的字元。 使用存取金鑰，使用者可以 「 按一下 」 按鈕在組合中按 ALT 鍵，以預先定義的存取金鑰。 例如，如果按鈕會執行將表單，列印程序，因此其`Text`屬性設定為"Print"，將新增連字號，再以字母"P"會導致字母"P"中加上底線按鈕的文字在執行階段。 使用者可以執行命令與按鈕關聯，藉由按下 ALT + P。 您不能有無法接收焦點的控制項的便捷鍵。  
  
### <a name="to-create-an-access-key-for-a-control"></a>若要建立控制項的便捷鍵  
  
1. 設定`Text`屬性設為字串，包含連字號 (&) 會快顯的字母前面。  
  
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
    >  若要包含在標題中的連字號，而不需建立存取金鑰，包含兩個連字號 (& &)。 單一連字號會顯示在標題中並沒有字元加上底線。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Button>
- [HOW TO：回應 Windows Forms 按鈕的按一下動作](how-to-respond-to-windows-forms-button-clicks.md)
- [HOW TO：設定 Windows Forms 控制項所顯示的文字](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [標記個別 Windows Form 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
