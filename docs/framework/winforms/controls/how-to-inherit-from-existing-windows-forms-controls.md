---
title: 從現有控制項繼承
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849376"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>如何：繼承自現有的 Windows Forms 控制項

如果您想要擴充現有控制項的功能，您可以透過繼承來建立衍生自現有控制項的控制項。 繼承自現有的控制項時，您會繼承該控制項的所有功能和視覺屬性。 例如，如果要創建從 繼承的<xref:System.Windows.Forms.Button>控制項，則新控制項的外觀和行為將完全類似于標準<xref:System.Windows.Forms.Button>控制項。 您就可以透過實作自訂方法和屬性，來擴充或修改新控制項的功能。 在某些控制項中，還可以通過重寫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法來更改繼承控制項的可視外觀。

## <a name="to-create-an-inherited-control"></a>建立繼承的控制項

1. 在視覺化工作室中，創建新的**Windows 表單應用程式**專案。

1. 從 [專案]**** 功能表選擇 [新增項目]****。

    [加入新項目] **** 對話方塊隨即出現。

1. 在 [新增項目]**** 對話方塊中，連按兩下 [自訂控制項]****。

    新的自訂控制項會新增至您的專案。

1. 如果您使用的是：

    - 視覺化基本，在**解決方案資源管理器**的頂部，按一下 **"顯示所有檔**"。 展開 CustomControl1.vb，然後在程式碼編輯器中開啟 CustomControl1.Designer.vb。
    - C#，在代碼編輯器中打開CustomControl1.cs。

1. 查找從<xref:System.Windows.Forms.Control>繼承的類聲明。

1. 將基底類別變更為您想要繼承的控制項。

     例如，如果要從<xref:System.Windows.Forms.Button>繼承 ，則將類聲明更改為以下內容：

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. 如果您使用 Visual Basic，請儲存並關閉 CustomControl1.Designer.vb。 在程式碼編輯器中開啟 CustomControl1.vb。

1. 實作您的控制項將併入的任何自訂方法或屬性。

1. 如果要修改控制項的圖形外觀，請重寫 方法<xref:System.Windows.Forms.Control.OnPaint%2A>。

    > [!NOTE]
    > 重寫<xref:System.Windows.Forms.Control.OnPaint%2A>將不允許修改所有控制項的外觀。 那些由 Windows 完成所有繪製的控制項（例如），<xref:System.Windows.Forms.TextBox>永遠不會調用其<xref:System.Windows.Forms.Control.OnPaint%2A>方法，因此永遠不會使用自訂代碼。 請參閱要修改的特定控制項的説明文檔，<xref:System.Windows.Forms.Control.OnPaint%2A>以查看該方法是否可用。 如需所有 Windows Forms 控制項的清單，請參閱[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)。 如果控制項未<xref:System.Windows.Forms.Control.OnPaint%2A>列為成員方法，則無法通過重寫此方法來更改其外觀。 如需自訂繪製的詳細資訊，請參閱[自訂控制項繪製和轉譯](custom-control-painting-and-rendering.md)。

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
- [操作說明：繼承自 Control 類別](how-to-inherit-from-the-control-class.md)
- [操作說明：繼承自 UserControl 類別](how-to-inherit-from-the-usercontrol-class.md)
- [操作說明：撰寫 Windows Forms 的控制項](how-to-author-controls-for-windows-forms.md)
- [Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [演練：從 Windows 表單控制項繼承](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
