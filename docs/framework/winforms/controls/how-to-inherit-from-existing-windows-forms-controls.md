---
title: 作法：繼承現有的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fcf95e08296f5a8ec5a386ac614482c034e72c8b
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373242"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>HOW TO：繼承現有的 Windows Forms 控制項

如果您想要擴充現有控制項的功能，您可以透過繼承來建立衍生自現有控制項的控制項。 繼承自現有的控制項時，您會繼承該控制項的所有功能和視覺屬性。 例如，如果您要建立繼承自<xref:System.Windows.Forms.Button>的控制項，新控制項的外觀和作用就和標準<xref:System.Windows.Forms.Button>控制項完全一樣。 您就可以透過實作自訂方法和屬性，來擴充或修改新控制項的功能。 在某些控制項中，您也可以藉由覆寫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法來變更繼承控制項的視覺外觀。

## <a name="to-create-an-inherited-control"></a>建立繼承的控制項

1. 在 Visual Studio 中，建立新的**Windows Forms 應用程式**專案。

1. 從 [專案] 功能表選擇 [新增項目]。

    [新增項目] 對話方塊隨即出現。

1. 在 [新增項目] 對話方塊中，連按兩下 [自訂控制項]。

    新的自訂控制項會新增至您的專案。

1. 如果您使用：

    - Visual Basic 中，按一下**方案總管**頂端的 [**顯示所有**檔案]。 展開 CustomControl1.vb，然後在程式碼編輯器中開啟 CustomControl1.Designer.vb。
    - C#，在程式碼編輯器中開啟 CustomControl1.cs。

1. 找出繼承自<xref:System.Windows.Forms.Control>的類別宣告。

1. 將基底類別變更為您想要繼承的控制項。

     例如，如果您想要繼承自<xref:System.Windows.Forms.Button>，請將類別宣告變更為下列內容：

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. 如果您使用 Visual Basic，請儲存並關閉 CustomControl1.Designer.vb。 在程式碼編輯器中開啟 CustomControl1.vb。

1. 實作您的控制項將併入的任何自訂方法或屬性。

1. 如果您想要修改控制項的圖形外觀，請覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。

    > [!NOTE]
    > 覆<xref:System.Windows.Forms.Control.OnPaint%2A>寫將不允許您修改所有控制項的外觀。 所有由 Windows 完成其繪製的控制項（例如， <xref:System.Windows.Forms.TextBox>）永遠不會呼叫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法，因此永遠不會使用自訂程式碼。 請參閱您想要修改之特定控制項的說明文件，以查看該<xref:System.Windows.Forms.Control.OnPaint%2A>方法是否可用。 如需所有 Windows Forms 控制項的清單，請參閱[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)。 如果控制項未<xref:System.Windows.Forms.Control.OnPaint%2A>列為成員方法，您就無法藉由覆寫這個方法來改變其外觀。 如需自訂繪製的詳細資訊，請參閱[自訂控制項繪製和轉譯](custom-control-painting-and-rendering.md)。

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

1. 儲存並測試您的控制項。

## <a name="see-also"></a>另請參閱

- [各種自訂控制項](varieties-of-custom-controls.md)
- [如何：繼承自控制項類別](how-to-inherit-from-the-control-class.md)
- [如何：繼承自 UserControl 類別](how-to-inherit-from-the-usercontrol-class.md)
- [如何：Windows Forms 的作者控制項](how-to-author-controls-for-windows-forms.md)
- [Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [逐步解說：繼承自 Windows Forms 控制項](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
