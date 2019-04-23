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
ms.openlocfilehash: 0768f811653543b3370310ccc0b59890273baf52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330099"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>HOW TO：將沒有使用者介面的控制項新增至 Windows Forms
非視覺控制項 （或元件） 提供您的應用程式的功能。 不像其他控制項，並不提供給使用者的使用者介面元件，並因此不需要在 Windows Form 設計工具介面上顯示。 當元件加入至表單時，Windows Form 設計工具會顯示可調整大小的紙匣底端的表單，其中會顯示所有元件。 控制項新增至元件匣之後, 您可以選取的元件，並設定其屬性，如同任何其他控制項在表單上。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-a-component-to-a-windows-form"></a>若要將元件新增至 Windows 表單  
  
1. 開啟表單。 如需詳細資訊，請參閱[如何：在設計工具中顯示 Windows Form](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))。  
  
2. 在 **工具箱**、 按一下元件，並將它拖曳至表單。  
  
     您的元件會出現在元件匣中。  
  
 此外，元件可以在執行階段新增到表單。 這會是常見的案例中，特別是因為元件並沒有視覺的運算式，不像使用者介面的控制項。 在下列範例中，<xref:System.Windows.Forms.Timer>元件會在執行階段加入。 (請注意，Visual Studio 包含幾個不同的計時器的; 在此案例中，使用 Windows Form<xref:System.Windows.Forms.Timer>元件。 如需在 Visual Studio 中的不同計時器的詳細資訊，請參閱[伺服器為基礎的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。)  
  
> [!CAUTION]
>  元件通常具有必須設定元件能有效運作的控制項特定屬性。 若是<xref:System.Windows.Forms.Timer>元件下方，設定`Interval`屬性。 請務必，將元件新增至您的專案，，您設定必要的屬性，該元件時。  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>若要以程式設計方式將元件新增至 Windows 表單  
  
1. 建立的執行個體<xref:System.Windows.Forms.Timer>在程式碼中的類別。  
  
2. 設定`Interval`屬性來判斷計時器的刻度之間的時間。  
  
3. 設定其他任何必要屬性，為您的元件。  
  
     下列程式碼顯示如何建立<xref:System.Windows.Forms.Timer>具有其`Interval`屬性集。  
  
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
    >  藉由參考惡意的使用者控制項，您可能會公開本機電腦透過網路的安全性風險。 這只會在惡意人士建立破壞性的自訂控制項，且您不小心將它新增至您的專案的情況下需要考量。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](index.md)
- [如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)
- [如何：將 ActiveX 控制項新增至 Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [如何：Windows Form 之間複製控制項](how-to-copy-controls-between-windows-forms.md)
- [將控制項加入 Windows Forms](putting-controls-on-windows-forms.md)
- [標記個別 Windows Forms 控制項並提供其捷徑](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
- [依功能區分 Windows Forms 控制項](windows-forms-controls-by-function.md)
