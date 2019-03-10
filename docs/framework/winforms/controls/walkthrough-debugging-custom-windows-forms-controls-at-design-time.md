---
title: 逐步解說：在設計階段偵錯自訂的 Windows Form 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
ms.openlocfilehash: 9bd3f822e5a1f8572ebb7f5991abccde904150b8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717826"
---
# <a name="walkthrough-debugging-custom-windows-forms-controls-at-design-time"></a>逐步解說：在設計階段偵錯自訂的 Windows Form 控制項
當您建立自訂控制項時，通常會發現它需要偵錯它的設計階段行為。 這是特別有用，如果您撰寫自訂的設計工具為您的自訂控制項。 如需詳細資訊，請參閱[逐步解說：建立 Windows Form 會充分利用 Visual Studio 設計階段功能的控制項](creating-a-wf-control-design-time-features.md)。  
  
 就像您會偵錯任何其他.NET Framework 類別，您可以偵錯使用 Visual Studio 中，您的自訂控制項。 差別在於您要偵錯 Visual Studio 執行您的自訂控制項程式碼的個別執行個體  
  
 這個逐步解說中所述的工作包括：  
  
-   建立 Windows Forms 專案來裝載您的自訂控制項  
  
-   建立控制項程式庫專案  
  
-   將屬性加入至您的自訂控制項  
  
-   將您的自訂控制項加入至主應用程式表單  
  
-   設定設計階段偵錯的專案  
  
-   在設計階段偵錯您的自訂控制項  
  
 當您完成時，您將了解偵錯自訂控制項的設計階段行為的必要工作。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>建立專案  
 第一個步驟是建立應用程式專案。 您將使用此專案來建置應用程式裝載自訂的控制項。  
  
#### <a name="to-create-the-project"></a>若要建立專案  
  
-   建立 Windows 應用程式專案，稱為 「 DebuggingExample"(**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。  
  
## <a name="creating-a-control-library-project"></a>建立控制項程式庫專案  
 下一個步驟是建立控制項程式庫專案並設定自訂的控制項。  
  
#### <a name="to-create-the-control-library-project"></a>若要建立控制項程式庫專案  
  
1.  新增**Windows 控制項程式庫**專案加入方案。  
  
2.  加入新**UserControl** DebugControlLibrary 專案項目。 如需詳細資訊，請參閱[如何：加入新的專案項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))。 提供新的來源檔案的"DebugControl 」 的基底名稱。  
  
3.  使用**方案總管**，刪除專案的預設控制項的基底名稱的程式碼檔案中刪除 「`UserControl1`"。 如需詳細資訊，請參閱[如何：移除，請刪除，並排除項目](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))。  
  
4.  建置方案。  
  
## <a name="checkpoint"></a>檢查點  
 此時，您可以在此處查看您的自訂控制項中**工具箱**。  
  
#### <a name="to-check-your-progress"></a>若要檢查您的進度  
  
-   找到稱為 [新增] 索引標籤**DebugControlLibrary 元件**並按一下以選取它。 當它開啟時，您會看到控制項列為**DebugControl**與它旁邊的預設圖示。  
  
## <a name="adding-a-property-to-your-custom-control"></a>將屬性加入至您的自訂控制項  
 若要示範自訂控制項的程式碼會執行設計階段，您會將屬性加入，並實作屬性的程式碼中設定中斷點。  
  
#### <a name="to-add-a-property-to-your-custom-control"></a>若要將屬性加入至您的自訂控制項  
  
1.  開啟**DebugControl**中**程式碼編輯器**。 將下列程式碼新增至類別定義：  
  
    ```vb  
    Private demoStringValue As String = Nothing  
    <BrowsableAttribute(true)>  
    Public Property DemoString() As String  
  
        Get  
            Return Me.demoStringValue  
        End Get  
  
        Set(ByVal value As String)  
            Me.demoStringValue = value  
        End Set  
  
    End Property  
    ```  
  
    ```csharp  
    private string demoStringValue = null;  
    [Browsable(true)]  
    public string DemoString  
    {  
        get  
        {  
            return this.demoStringValue;  
        }  
        set  
        {  
            demoStringValue = value;  
        }  
    }  
    ```  
  
2.  建置方案。  
  
## <a name="adding-your-custom-control-to-the-host-form"></a>將您的自訂控制項加入至主應用程式表單  
 偵錯您的自訂控制項的設計階段行為，您將在主表單上放置自訂控制項類別的執行個體。  
  
#### <a name="to-add-your-custom-control-to-the-host-form"></a>若要將您的自訂控制項加入至主表單  
  
1.  在 「 DebuggingExample 」 專案中，開啟 [] 中的 Form1 **Windows Form 設計工具**。  
  
2.  在 **工具箱**，開啟**DebugControlLibrary 元件**索引標籤，然後拖曳**DebugControl**拖曳至表單的執行個體。  
  
3.  尋找`DemoString`中的自訂屬性**屬性**視窗。 請注意，您就可以變更其值，如同任何其他屬性。 也請注意，當`DemoString`中選取屬性、 屬性的描述字串會出現在底部**屬性**視窗。  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a>設定設計階段偵錯的專案  
 若要偵錯您的自訂控制項的設計階段行為，您要偵錯執行您的自訂控制項程式碼的 Visual Studio 的個別執行個體。  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a>若要設定設計階段偵錯的專案  
  
1.  以滑鼠右鍵按一下**DebugControlLibrary**專案中**方案總管**，然後選取**屬性**。  
  
2.  在 [ **DebugControlLibrary**屬性工作表，選取**偵錯**] 索引標籤。  
  
     在 **起始動作**區段中，選取**啟動外部程式**。 您將會讓偵錯個別的執行個體的 Visual Studio 中，按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕來瀏覽 Visual Studio IDE。 可執行檔的名稱是**devenv.exe**，且如果您安裝的預設位置，其路徑為 %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe。  
  
3.  按一下 [確定]  關閉對話方塊。  
  
4.  以滑鼠右鍵按一下**DebugControlLibrary**專案，然後選取**設定為啟始專案**來啟用這個偵錯組態。  
  
## <a name="debugging-your-custom-control-at-design-time"></a>在設計階段偵錯您的自訂控制項  
 現在您已經準備好要偵錯您的自訂控制項，因為它會在設計模式中執行。 當您啟動偵錯工作階段時，將建立 Visual Studio 的新執行個體，以及您將使用它來載入 「 DebuggingExample 」 方案。 當您開啟中的 Form1 **Form 設計工具**，您的自訂控制項的執行個體將會建立，而且將會開始執行。  
  
#### <a name="to-debug-your-custom-control-at-design-time"></a>若要在設計階段偵錯您的自訂控制項  
  
1.  開啟**DebugControl**原始程式檔中的**程式碼編輯器**，並將中斷點放在`Set`存取子`DemoString`屬性。  
  
2.  按下 f5 鍵啟動偵錯工作階段。 請注意，已建立 Visual Studio 的新執行個體。 您可以區分兩種方式中的執行個體：  
  
    -   偵錯的執行個體中包含文字**執行**其標題列中  
  
    -   偵錯的執行個體已**開始**按鈕及其**偵錯**停用工具列  
  
     在 偵錯的執行個體已設定您的中斷點。  
  
3.  在 Visual Studio 的新執行個體，開啟 「 DebuggingExample 」 方案。 您可以選取，以輕鬆地尋找方案**最近使用的專案**從**檔案**功能表。 會列出 「 DebuggingExample.sln"方案檔，因為最近使用過的檔案。  
  
4.  開啟中的 Form1 **Form 設計工具**，然後選取**DebugControl**控制項。  
  
5.  變更 `DemoString` 屬性的值。 請注意，當您認可變更時，Visual Studio 偵錯執行個體取得焦點，在中斷點停止執行。 您可以逐步執行屬性存取子就如同您將任何其他程式碼。  
  
6.  當您完成與偵錯工作階段，您可以結束關閉裝載 Visual Studio 執行個體，或按一下**停止偵錯**偵錯執行個體中的按鈕。  
  
## <a name="next-steps"></a>後續步驟  
 現在，您可以在設計階段進行偵錯您的自訂控制項，有許多可能性，擴充您的控制項與 Visual Studio IDE 之間的互動。  
  
-   您可以使用<xref:System.ComponentModel.Component.DesignMode%2A>屬性<xref:System.ComponentModel.Component>類別來撰寫程式碼，只會在設計階段執行。 如需詳細資訊，請參閱 <xref:System.ComponentModel.Component.DesignMode%2A>。  
  
-   有幾個屬性可套用至控制項的屬性，來操作您的自訂控制項互動與設計工具。 您可以找到這些屬性在<xref:System.ComponentModel?displayProperty=nameWithType>命名空間。  
  
-   您可以撰寫自訂的設計工具為您的自訂控制項。 這可讓您使用 Visual Studio 所公開的可擴充設計工具基礎結構的設計經驗的完整控制。 如需詳細資訊，請參閱[逐步解說：建立 Windows Form 會充分利用 Visual Studio 設計階段功能的控制項](creating-a-wf-control-design-time-features.md)。  
  
## <a name="see-also"></a>另請參閱
- [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](creating-a-wf-control-design-time-features.md)
- [如何：存取設計階段服務](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171822(v=vs.120))
- [如何：在 Windows Forms 中存取設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171827(v=vs.120))
