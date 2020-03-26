---
title: 逐步解說：當地語系化混合應用程式
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111110"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>逐步解說：當地語系化混合應用程式

本演練將介紹如何當地語系化[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]基於 Windows 表單的混合應用程式中的元素。

這個逐步解說中所述的工作包括：

- 創建 Windows 表單主項目目。

- 新增可當地語系化的內容。

- 啟用當地語系化。

- 指派資源識別碼。

- 使用 LocBaml 工具產生附屬組件。

有關本演練中說明的任務的完整代碼清單，請參閱[當地語系化混合應用程式示例](https://go.microsoft.com/fwlink/?LinkID=160015)。

完成之後，就會有當地語系化的混合應用程式。

## <a name="prerequisites"></a>Prerequisites

您需要下列元件才能完成這個逐步解說：

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>建立 Windows Forms 主專案

第一步是創建 Windows 表單應用程式專案，並添加包含[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要當地語系化的內容的元素。

### <a name="to-create-the-host-project"></a>建立主專案

1. 創建名為`LocalizingWpfInWf`**的 WPF 應用**專案。  （**檔** > **新專案** > **Project** > **Classic Desktop** > **WPF Application****Visual Basic****Visual C#** 視覺化C#或視覺化基本經典桌面WPF應用程式）。 > 

2. 向專案[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl>添加調用`SimpleControl`的元素。

3. 使用<xref:System.Windows.Forms.Integration.ElementHost>控制項在表單上`SimpleControl`放置元素。 有關詳細資訊，請參閱[演練：在 Windows 表單中託管 3D WPF 複合控制項](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)。

## <a name="adding-localizable-content"></a>新增可當地語系化的內容

接下來，您將添加 Windows 表單標籤控制項，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]並將元素的內容設置為可當地語系化字串。

### <a name="to-add-localizable-content"></a>新增可當地語系化的內容

1. 在**解決方案資源管理器中**，按兩下**SimpleControl.xaml**以在 WPF 設計器中打開它。

2. 使用以下代碼設置<xref:System.Windows.Controls.Button>控制項的內容。

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. 在**解決方案資源管理器中**，按兩下**Form1**以在 Windows 表單設計器中打開它。

4. 打開**工具箱**並按兩下**標籤**以向表單添加標籤控制項。 將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性的值設定為 `"Hello"`。

5. 按**F5**生成並運行應用程式。

     元素`SimpleControl`和標籤控制項都顯示文本 **"你好"。**

## <a name="enabling-localization"></a>啟用當地語系化

Windows Forms 設計工具提供在附屬組件中啟用當地語系化的設定。

### <a name="to-enable-localization"></a>啟用當地語系化

1. 在**解決方案資源管理器**中，按兩下**Form1.cs**在 Windows 表單設計器中打開它。

2. 在 **"屬性"** 視窗中，將表單的**可當地語系化**屬性的值設置為`true`。

3. 在 **"屬性"** 視窗中，將**語言**屬性的值設置為**西班牙文（西班牙）。**

4. 在 [Windows Forms 設計工具] 中，選取 Label 控制項。

5. 在 **"屬性"** 視窗中，將<xref:System.Windows.Forms.Control.Text%2A>屬性的值設置為`"Hola"`。

     名為 Form1.es-ES.resx 的新資源檔會新增至專案。

6. 在**解決方案資源管理器**中，按右鍵**Form1.cs**並按一下 **"查看代碼**"以在代碼編輯器中打開它。

7. 將以下代碼複製到建構函式`Form1`中，在調用 之前到`InitializeComponent`。

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. 在**解決方案資源管理器中**，按右鍵 **"當地語系化 WpfinWf"，** 然後按一下 **"卸載專案**"。

     專案名稱標記為 **（不可用）。**

9. 按右鍵 **"當地語系化 WpfinWf**"，然後按一下 **"編輯當地語系化 WpfinWf.csproj**"。

     隨即在程式碼編輯器中開啟專案檔。

10. 將以下行複製到專案檔案中的第`PropertyGroup`一行。

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. 儲存並關閉專案檔。

12. 在**解決方案資源管理器中**，按右鍵 **"當地語系化 WpfinWf"，** 然後按一下 **"重新載入專案**"。

## <a name="assigning-resource-identifiers"></a>指派資源識別碼

您可以使用資源識別碼，將可當地語系化的內容對應至資源組件。 當您指定`updateuid`選項時，MsBuild.exe 應用程式會自動分配資源識別碼。

### <a name="to-assign-resource-identifiers"></a>指派資源識別碼

1. 從"開始"功能表中，打開視覺化工作室的開發人員命令提示。

2. 使用下列命令，將資源識別碼指派給可當地語系化的內容。

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. 在**解決方案資源管理器中**，按兩下**SimpleControl.xaml**以在代碼編輯器中打開它。 您將看到該`msbuild`命令已將`Uid`該屬性添加到所有元素。 這有助於透過資源識別碼指派進行當地語系化。

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. 按 **F6** 以建立方案。

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>使用 LocBaml 產生附屬組件

當地語系化的內容存儲在僅資源附屬*程式集*中。 使用命令列工具 LocBaml.exe 為您的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內容生成當地語系化程式集。

### <a name="to-produce-a-satellite-assembly"></a>產生附屬組件

1. 將 LocBaml.exe 複製至專案的 obj\Debug 資料夾。 有關詳細資訊，請參閱[當地語系化應用程式](how-to-localize-an-application.md)。

2. 在 [命令提示字元] 視窗中，使用下列命令來將資源字串擷取至暫存檔。

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. 使用 Visual Studio 或其他文字編輯器打開 temp.csv 檔。 將字串`"Hello"`替換為其西班牙文翻譯 。 `"Hola"`

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

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [將應用程式當地語系化](how-to-localize-an-application.md)
- [逐步解說：將 Windows Forms 當地語系化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
