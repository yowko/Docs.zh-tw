---
title: 逐步解說：當地語系化混合應用程式
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b406d539f2446824027e9462c8ecbe20c18cfb27
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794133"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>逐步解說：當地語系化混合應用程式

本逐步解說將示範如何在 Windows Forms 型混合式應用程式中，將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素當地語系化。

這個逐步解說中所述的工作包括：

- 建立 Windows Forms 主專案。

- 新增可當地語系化的內容。

- 啟用當地語系化。

- 指派資源識別碼。

- 使用 LocBaml 工具產生附屬組件。

如需本逐步解說中所述工作的完整程式代碼清單，請參閱[當地語系化混合式應用程式範例](https://go.microsoft.com/fwlink/?LinkID=160015)。

完成之後，就會有當地語系化的混合應用程式。

## <a name="prerequisites"></a>必要條件：

您需要下列元件才能完成此逐步解說：

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>建立 Windows Forms 主專案

第一個步驟是建立 Windows Forms 應用程式專案，並新增包含您要當地語系化之內容的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素。

### <a name="to-create-the-host-project"></a>建立主專案

1. 建立名為 `LocalizingWpfInWf`的**WPF 應用程式**專案。  （**檔案** > **新**的 ** > 專案** > **Visual C#** 或**Visual Basic** > **傳統桌面** > **WPF 應用程式**）。

2. 將名為 `SimpleControl` 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> 元素新增至專案。

3. 使用 <xref:System.Windows.Forms.Integration.ElementHost> 控制項，將 `SimpleControl` 元素放在表單上。 如需詳細資訊，請參閱[逐步解說：在 Windows Forms 中裝載立體 WPF 複合控制項](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)。

## <a name="adding-localizable-content"></a>新增可當地語系化的內容

接下來，您將加入 Windows Forms 標籤控制項，並將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元素的內容設定為可當地語系化的字串。

### <a name="to-add-localizable-content"></a>新增可當地語系化的內容

1. 在**方案總管**中，按兩下**SIMPLECONTROL.XAML** ，在 WPF 設計工具中開啟它。

2. 使用下列程式碼來設定 <xref:System.Windows.Controls.Button> 控制項的內容。

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. 在**方案總管**中，按兩下 [ **Form1** ]，在 Windows Form 設計工具中將它開啟。

4. 開啟 [**工具箱**] 並按兩下 [**標籤**]，將標籤控制項新增至表單。 將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性的值設定為 `"Hello"`。

5. 按 **F5** 鍵建置並執行應用程式。

     `SimpleControl` 元素和標籤控制項都會顯示 **"Hello"** 文字。

## <a name="enabling-localization"></a>啟用當地語系化

Windows Forms 設計工具提供在附屬組件中啟用當地語系化的設定。

### <a name="to-enable-localization"></a>啟用當地語系化

1. 在**方案總管**中，按兩下**Form1.cs**以在 Windows Form 設計工具中加以開啟。

2. 在 [**屬性**] 視窗中，將表單可**當地語系化**屬性的值設定為 `true`。

3. 在 [**屬性**] 視窗中，將 [ **Language** ] 屬性的值設定為 [**西班牙文（西班牙）** ]。

4. 在 [Windows Forms 設計工具] 中，選取 Label 控制項。

5. 在 [**屬性**] 視窗中，將 [<xref:System.Windows.Forms.Control.Text%2A>] 屬性的值設定為 [`"Hola"`]。

     名為 Form1.es-ES.resx 的新資源檔會新增至專案。

6. 在**方案總管**中，以滑鼠右鍵按一下**Form1.cs** ，然後按一下 [**查看程式碼**]，在程式碼編輯器中開啟它。

7. 在呼叫 `InitializeComponent`之前，將下列程式碼複製到 `Form1` 的函式中。

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. 在**方案總管**中，以滑鼠右鍵按一下**LocalizingWpfInWf** ，然後按一下 **[卸載專案**]。

     專案名稱已標記為 **（無法使用）** 。

9. 以滑鼠右鍵按一下 [ **LocalizingWpfInWf**]，然後按一下 [**編輯 LocalizingWpfInWf**]。

     隨即在程式碼編輯器中開啟專案檔。

10. 將下面這一行複製到專案檔中的第一個 `PropertyGroup`。

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. 儲存並關閉專案檔。

12. 在**方案總管**中，以滑鼠右鍵按一下**LocalizingWpfInWf** ，然後按一下 [**重載專案**]。

## <a name="assigning-resource-identifiers"></a>指派資源識別碼

您可以使用資源識別碼，將可當地語系化的內容對應至資源組件。 當您指定 `updateuid` 選項時，Msbuild.exe 應用程式會自動指派資源識別碼。

### <a name="to-assign-resource-identifiers"></a>指派資源識別碼

1. 在 [開始] 功能表中，開啟 Visual Studio 的 [開發人員命令提示字元]。

2. 使用下列命令，將資源識別碼指派給可當地語系化的內容。

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. 在**方案總管**中，按兩下**simplecontrol.xaml** ，在程式碼編輯器中開啟它。 您會看到 `msbuild` 命令已將 `Uid` 屬性新增至所有元素。 這有助於透過資源識別碼指派進行當地語系化。

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. 按**F6**以建立方案。

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>使用 LocBaml 產生附屬組件

您的當地語系化內容會儲存在僅限資源的*附屬元件*中。 使用命令列工具 LocBaml，為您的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容產生當地語系化的元件。

### <a name="to-produce-a-satellite-assembly"></a>產生附屬組件

1. 將 LocBaml.exe 複製至專案的 obj\Debug 資料夾。 如需詳細資訊，請參閱[將應用程式當地語系化](how-to-localize-an-application.md)。

2. 在 [命令提示字元] 視窗中，使用下列命令來將資源字串擷取至暫存檔。

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. 使用 Visual Studio 或其他文字編輯器開啟 temp .csv 檔案。 將字串 `"Hello"` 取代為其西班牙文翻譯，`"Hola"`。

4. 儲存 temp.csv 檔案。

5. 使用下列命令來產生已當地語系化的資源檔。

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     LocalizingWpfInWf.g.es-ES.resources 檔案會在 obj\Debug 資料夾中建立。

6. 使用下列命令來建置已當地語系化的附屬組件。

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     LocalizingWpfInWf.resources.dll 檔案會在 obj\Debug 資料夾中建立。

7. 將 LocalizingWpfInWf.resources.dll 檔案複製至專案的 bin\Debug\es-ES 資料夾。 取代現有檔案。

8. 執行 LocalizingWpfInWf.exe，其位於專案的 bin\Debug 資料夾中。 請不要重建應用程式，否則將會覆寫附屬組件。

     應用程式會顯示當地語系化字串，而不是英文字串。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [將應用程式當地語系化](how-to-localize-an-application.md)
- [逐步解說：當地語系化 Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
