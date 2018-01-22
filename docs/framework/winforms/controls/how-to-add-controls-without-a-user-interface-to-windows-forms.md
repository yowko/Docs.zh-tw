---
title: "如何：將沒有使用者介面的控制項加入至 Windows Form"
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
f1_keywords: NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3abbf931cff9ad459e8c9221f91430ecccefa9cc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>如何：將沒有使用者介面的控制項加入至 Windows Form
隱藏式控制項 （或元件） 提供您的應用程式的功能。 不像其他控制項，並不提供給使用者的使用者介面元件，並因此不需要在 Windows Form 設計工具介面上顯示。 當元件加入至表單時，Windows Form 設計工具會顯示可調整大小的紙匣底端的表單顯示所有元件的位置。 一旦已將控制項加入至元件匣中，您可以選取的元件，並設定其屬性，就像處理任何其他控制項在表單上。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-add-a-component-to-a-windows-form"></a>若要將元件加入至 Windows Form  
  
1.  開啟表單。 如需詳細資訊，請參閱[如何： 顯示 Windows Form 設計工具中](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。  
  
2.  在**工具箱**、 按一下元件，並將它拖曳至表單。  
  
     您的元件會出現在元件匣中。  
  
 此外，元件可以在執行階段加入至表單。 這會是常見的案例中，尤其是因為元件沒有視覺化的運算式，不像具有使用者介面的控制項。 在下列範例中，<xref:System.Windows.Forms.Timer>在執行階段加入元件。 (請注意，[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]包含的不同計時器的數字; 在此情況下，使用 Windows Form<xref:System.Windows.Forms.Timer>元件。 如需中的不同計時器[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，請參閱[伺服器為基礎的計時器簡介](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。)  
  
> [!CAUTION]
>  元件通常具有必須設定元件，有效地運作的控制項特定屬性。 如果是<xref:System.Windows.Forms.Timer>元件下方，設定`Interval`屬性。 請記得，將元件加入至您的專案，確定您設定必要的屬性，該元件時。  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>若要以程式設計方式將元件加入至 Windows Form  
  
1.  建立的執行個體<xref:System.Windows.Forms.Timer>程式碼中的類別。  
  
2.  設定`Interval`屬性來判斷之計時器刻度之間的時間。  
  
3.  設定您的元件的任何其他必要屬性。  
  
     下列程式碼顯示建立<xref:System.Windows.Forms.Timer>具有其`Interval`屬性集。  
  
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
    >  藉由參考惡意的使用者控制項，您可能會公開本機電腦透過網路的安全性風險。 這只會考量使用者惡意破壞性的自訂控制項，且您不小心將其加入您專案的建立。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [操作說明：將 ActiveX 控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [操作說明：在 Windows Forms 之間複製控制項](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [將控制項加入 Windows Forms](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [標記個別 Windows Forms 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [依功能區分 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
