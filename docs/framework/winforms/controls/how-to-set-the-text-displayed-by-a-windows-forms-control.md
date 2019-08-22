---
title: HOW TO：設定 Windows Forms 控制項所顯示的文字
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 887aa5ec9b97770903cd87459d6df5adc3f7ddf0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666146"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>作法：設定 Windows Forms 控制項所顯示的文字

Windows Forms 控制項通常會顯示一些與控制項主要功能相關的文字。 例如, <xref:System.Windows.Forms.Button>控制項通常會顯示一個標題, 指出按一下按鈕時將執行的動作。 針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。 您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。

您也可以使用[設計](#designer)工具來設定文字。

## <a name="programmatic"></a>化

1. 將 <xref:System.Windows.Forms.Control.Text%2A> 屬性設為字串。

   若要建立加底線的存取金鑰, 請在將成為存取金鑰的字母之前包含連字號 (&)。

2. 將 <xref:System.Windows.Forms.Control.Font%2A> 屬性設為 <xref:System.Drawing.Font> 類型的物件。

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > 您可以在使用者介面項目中使用逸出字元來顯示特殊字元，這些使用者介面項目 (例如功能表項目) 通常會以不同方式來解譯該字元。 例如, 下面這行程式碼會將功能表項目的文字設定為「立即 & 完全不同」的內容:

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a>Designer

1. 在 Visual Studio 的 [**屬性**] 視窗中, 將控制項的 [ **Text** ] 屬性設定為適當的字串。

   若要建立加底線的快速鍵, 請在將做為快速鍵的字母之前包含連字號 (&)。

2. 在 **屬性**] 視窗中, 選取 [![**字型**] 屬性旁邊的省略號按鈕 ([Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...))。

   在 [標準字型] 對話方塊中, 選取字型、字型樣式、大小、效果 (例如刪除線或底線), 以及您想要的腳本。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [如何：建立 Windows Forms 控制項的存取金鑰](how-to-create-access-keys-for-windows-forms-controls.md)
- [如何：回應 Windows Forms 按鈕點擊](how-to-respond-to-windows-forms-button-clicks.md)
