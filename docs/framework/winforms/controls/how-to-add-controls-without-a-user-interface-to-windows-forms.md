---
title: HOW TO：將沒有使用者介面的控制項新增至 Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987106"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>作法：將沒有使用者介面的控制項新增至 Windows Forms

非視覺化的控制項 (或元件) 會為您的應用程式提供功能。 不同于其他控制項, 元件不會提供使用者介面給使用者, 因此不需要在 Windows Form 設計工具表面上顯示。 將元件新增至表單時, Windows Form 設計工具會在顯示所有元件的表單底部顯示可調整大小的紙匣。 一旦控制項加入至元件匣, 您就可以選取元件, 並設定其屬性, 就像您在表單上的任何其他控制項一樣。

## <a name="add-a-component-to-a-windows-form"></a>將元件新增至 Windows Form

1. 在 Visual Studio 中開啟表單。 如需詳細資訊，請參閱[如何：在設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))工具中顯示 Windows Forms。

2. 在 [**工具箱**] 中, 按一下元件, 並將它拖曳至您的表單。

     您的元件會出現在元件匣中。

此外, 您可以在執行時間將元件加入至表單。 這是常見的案例, 特別是因為元件沒有視覺運算式, 不同于具有使用者介面的控制項。 在下列範例中, <xref:System.Windows.Forms.Timer>會在執行時間新增元件。 (請注意, Visual Studio 包含許多不同的計時器, 在此情況下, 請使用<xref:System.Windows.Forms.Timer> Windows Forms 元件。 如需 Visual Studio 中不同計時器的詳細資訊, 請參閱[以伺服器為基礎的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)))。

> [!CAUTION]
> 元件通常會有控制項特有的屬性, 必須設定此元件才能有效地運作。 在下面的<xref:System.Windows.Forms.Timer>元件案例中, 您可以`Interval`設定屬性。 請確定在將元件加入至專案時, 您會設定該元件所需的屬性。

## <a name="add-a-component-to-a-windows-form-programmatically"></a>以程式設計方式將元件新增至 Windows Form

1. 在程式碼中建立<xref:System.Windows.Forms.Timer>類別的實例。

2. `Interval`設定屬性, 以決定計時器的刻度之間的時間。

3. 為您的元件設定任何其他必要的屬性。

     下列程式碼示範如何<xref:System.Windows.Forms.Timer>建立, 並將其`Interval`屬性設定為。

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > 藉由參考惡意的 UserControl, 您可能會透過網路來公開本機電腦的安全性風險。 這只是在惡意人士建立損毀的自訂控制項, 然後誤將它新增至專案時的問題。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
- [如何：將 ActiveX 控制項新增至 Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [將控制項加入 Windows Forms](putting-controls-on-windows-forms.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
