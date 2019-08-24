---
title: 逐步解說：在設計階段偵錯自訂 Windows Forms 控制項
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 824d8a7de8e9e37899cb84d6cee9621f84a5bc65
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015690"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a>逐步解說：在設計階段時, Debug 自訂 Windows Forms 控制項

當您建立自訂控制項時, 您通常會發現有必要將它的設計階段行為進行調試。 如果您要撰寫自訂控制項的自訂設計工具, 更是如此。 如需詳細資訊[, 請參閱逐步解說:建立 Windows Forms 控制項, 利用 Visual Studio 的設計階段功能](creating-a-wf-control-design-time-features.md)。

您可以使用 Visual Studio 來進行自訂控制項的偵錯工具, 就像處理任何其他 .NET Framework 類別一樣。 差別在於, 您將會對執行自訂控制項程式碼的個別 Visual Studio 實例進行偵錯工具。

## <a name="create-the-project"></a>建立專案

第一個步驟是建立應用程式專案。 您將使用此專案來建立裝載自訂控制項的應用程式。

在 Visual Studio 中, 建立 Windows 應用程式專案, 並將其命名為**DebuggingExample**。

## <a name="create-the-control-library-project"></a>建立控制項程式庫專案

1. 將**Windows 控制項程式庫**專案新增至方案。

2. 將新的**UserControl**專案新增至 DebugControlLibrary 專案。 將它命名為**DebugControl**。

3. 在**方案總管**中, 藉由刪除基底名稱為 UserControl1 的程式碼檔案, 刪除專案的預設控制項。

4. 建置方案。

## <a name="checkpoint"></a>檢查點

此時, 您將能夠在 [**工具箱**] 中看到您的自訂控制項。

若要檢查您的進度, 請尋找名為 [ **DebugControlLibrary 元件**] 的新索引標籤, 然後按一下以選取它。 開啟時, 您會看到您的控制項列為**DebugControl** , 旁邊有預設圖示。

## <a name="add-a-property-to-your-custom-control"></a>將屬性新增至您的自訂控制項

為了示範您自訂控制項的程式碼在設計階段執行, 您會在執行屬性的程式碼中加入屬性並設定中斷點。

1. 在程式**代碼編輯器**中開啟**DebugControl** 。 將下列程式碼新增至類別定義:

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

2. 建置方案。

## <a name="add-your-custom-control-to-the-host-form"></a>將自訂控制項新增至主機表單

若要對自訂控制項的設計階段行為進行偵錯工具, 您要將自訂控制項類別的實例放在主表單上。

1. 在 "DebuggingExample" 專案中, 開啟  **Windows Form 設計工具**中的 Form1。

2. 在 [**工具箱**] 中, 開啟 [ **DebugControlLibrary 元件**] 索引標籤, 並將**DebugControl**實例拖曳至表單上。

3. 在 [**屬性**] 視窗中尋找自訂屬性。`DemoString` 請注意, 您可以變更它的值, 就像任何其他屬性一樣。 另請注意, 當`DemoString`您選取屬性時, 屬性的描述字串會顯示在 [**屬性**] 視窗的底部。

## <a name="set-up-the-project-for-design-time-debugging"></a>設定專案以進行設計階段的偵錯工具

若要在自訂控制項的設計階段行為中進行偵錯工具, 您將會對執行自訂控制項程式碼的個別 Visual Studio 實例進行偵錯工具。

1. 以滑鼠右鍵按一下 **方案總管**中的  **DebugControlLibrary**  專案, 然後選取 **屬性**。

2. 在 [ **DebugControlLibrary** ] 屬性工作表中, 選取 [ **Debug** ] 索引標籤。

     在 [**起始動作**] 區段中, 選取 [**啟動外部程式**]。 您將會 Visual Studio 的個別實例進行偵錯工具, 因此請按一下省略號![([Visual Studio](./media/visual-studio-ellipsis-button.png)屬性視窗中的省略號按鈕 (...)] 按鈕, 以流覽 Visual Studio 的 IDE。 可執行檔的名稱為**devenv**, 如果您安裝到預設位置, 其路徑為 *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\ \<edition > \Common7\IDE*。

3. 選取 [確定] 關閉對話方塊。

4. 以滑鼠右鍵按一下 [ **DebugControlLibrary** ] 專案, 然後選取 [**設定為啟始專案**], 以啟用此調試設定。

## <a name="debug-your-custom-control-at-design-time"></a>在設計階段時, 對自訂控制項進行偵錯工具

現在您已準備好在設計模式中執行自訂控制項。 當您啟動調試階段時, 將會建立 Visual Studio 的新實例, 而您會使用它來載入 "DebuggingExample" 方案。 當您在**表單設計**工具中開啟 Form1 時, 將會建立自訂控制項的實例, 而且會開始執行。

1. 在程式**代碼編輯器**中開啟**DebugControl**原始程式檔, 並將中斷點放`Set`在`DemoString`屬性的存取子上。

2. 按**F5**啟動「調試」會話。 建立 Visual Studio 的新實例。 您可以透過兩種方式來區別實例:

    - 偵錯工具實例的標題列中有執行的單字

    - 偵錯工具實例在其**調試**程式工具列上的 [**啟動**] 按鈕已停用

   您的中斷點是在偵錯工具實例中設定。

3. 在 Visual Studio 的新實例中, 開啟 "DebuggingExample" 解決方案。 您可以從 [檔案] 功能表選取 [**最近使用**的專案], 輕鬆地找到解決方案。 "DebuggingExample" 方案檔會列為最近使用的檔案。

4. 在**表單設計**工具中開啟 Form1, 然後選取 [ **DebugControl** ] 控制項。

5. 變更 `DemoString` 屬性的值。 當您認可變更時, Visual Studio 的偵錯工具實例會取得焦點, 而執行則會在您的中斷點停止。 您可以單一步驟逐步執行屬性存取子, 就如同您對任何其他程式碼一樣。

6. 若要停止調試, 請結束 Visual Studio 的主控實例, 或在調試實例中選取 [**停止調試**] 按鈕。

## <a name="next-steps"></a>後續步驟

現在您可以在設計階段進行自訂控制項的偵錯工具, 展開控制項與 Visual Studio IDE 的互動有許多可能性。

- 您可以使用<xref:System.ComponentModel.Component>類別<xref:System.ComponentModel.Component.DesignMode%2A>的屬性來撰寫只會在設計階段執行的程式碼。 如需詳細資訊，請參閱 <xref:System.ComponentModel.Component.DesignMode%2A>。

- 您可以將數個屬性套用至控制項的屬性, 以操作自訂控制項與設計工具的互動。 您可以在<xref:System.ComponentModel?displayProperty=nameWithType>命名空間中找到這些屬性。

- 您可以撰寫自訂控制項的自訂設計工具。 這可讓您使用 Visual Studio 所公開的可擴充設計工具基礎結構, 完全掌控設計經驗。 如需詳細資訊[, 請參閱逐步解說:建立 Windows Forms 控制項, 利用 Visual Studio 的設計階段功能](creating-a-wf-control-design-time-features.md)。

## <a name="see-also"></a>另請參閱

- [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項](creating-a-wf-control-design-time-features.md)
