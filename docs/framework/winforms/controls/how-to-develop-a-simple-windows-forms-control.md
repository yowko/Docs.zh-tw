---
title: HOW TO：開發簡單的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: a190d86f5ebe258427ac4a73c16c7f271462b69c
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807919"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>HOW TO：開發簡單的 Windows Forms 控制項

本節將逐步引導您完成撰寫自訂 Windows Forms 控制項的重要步驟。 在本逐步解說中開發的簡單控制項允許的對齊方式與其<xref:System.Windows.Forms.Control.Text%2A>来變更屬性。 它不會引發或處理事件。

### <a name="to-create-a-simple-custom-control"></a>建立簡單自訂控制項

1. 定義衍生自 <xref:System.Windows.Forms.Control?displayProperty=nameWithType> 的類別。

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. 定義屬性。 (您不需要定義屬性，因為控制項繼承許多屬性，從<xref:System.Windows.Forms.Control>類別，但大部分的自訂控制項通常會定義其他屬性。)下列程式碼片段會定義名為的屬性`TextAlignment`所`FirstControl`使用的顯示格式<xref:System.Windows.Forms.Control.Text%2A>屬性繼承自<xref:System.Windows.Forms.Control>。 如需有關定義屬性的詳細資訊，請參閱[屬性概觀](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120))。

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     當您設定可變更控制項的視覺顯示屬性時，您必須叫用<xref:System.Windows.Forms.Control.Invalidate%2A>方法來重繪控制項。 <xref:System.Windows.Forms.Control.Invalidate%2A> 定義於基底類別<xref:System.Windows.Forms.Control>。

3. 覆寫受保護<xref:System.Windows.Forms.Control.OnPaint%2A>方法繼承自<xref:System.Windows.Forms.Control>提供呈現邏輯移至您的控制項。 如果您不會覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>，您的控制項將無法繪製本身。 在下列程式碼片段中，<xref:System.Windows.Forms.Control.OnPaint%2A>方法會顯示<xref:System.Windows.Forms.Control.Text%2A>屬性繼承自<xref:System.Windows.Forms.Control>所指定的對齊`alignmentValue`欄位。

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. 為您的控制項提供屬性 (attribute)。 屬性可讓視覺化設計工具在設計階段適當地顯示您的控制項及其屬性與事件。 下列程式碼片段會將屬性 (attribute) 套用至 `TextAlignment` 屬性 (property)。 Visual Studio 中，例如設計工具中<xref:System.ComponentModel.CategoryAttribute.Category%2A>屬性 （如程式碼片段所示） 會造成屬性會顯示在邏輯類別之下。 <xref:System.ComponentModel.DescriptionAttribute.Description%2A>屬性會造成描述性字串顯示在底部**屬性** 視窗時`TextAlignment`選取屬性。 如需屬性的詳細資訊，請參閱[元件的設計階段屬性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))。

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. (選擇性) 為您的控制項提供資源。 您可以使用編譯器選項 (`/res` 適用於 C#) 來封裝資源與您的控制項，為您的控制項提供資源 (例如點陣圖)。 在執行階段，資源可以使用擷取的方法<xref:System.Resources.ResourceManager>類別。 如需有關建立和使用資源的詳細資訊，請參閱[桌面應用程式中的資源](../../resources/index.md)。

6. 編譯及部署您的控制項。 若要編譯及部署 `FirstControl,`，請執行下列步驟︰

    1. 將下列範例中的程式碼儲存至原始程式檔 (SimpleForm.cs 或 SimpleForms.vb)。

    2. 將原始程式碼編譯成組件，並將它儲存在您應用程式的目錄中。 若要達成此目的，請從包含原始程式檔的目錄執行下列命令。

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         `/t:library` 編譯器選項會告知編譯器您所建立的組件是程式庫 (而不是可執行檔)。 `/out` 選項指定組件的路徑和名稱。 `/r` 選項會提供您的程式碼所參考的組件名稱。 在此範例中，您會建立只有您的應用程式可以使用的私人組件。 因此，您必須將它儲存在您應用程式的目錄中。 如需有關封裝和部署控制項以供散發的詳細資訊，請參閱[部署](../../deployment/index.md)。

下列範例顯示 `FirstControl` 的程式碼。 控制項會包含在 `CustomWinControls` 命名空間中。 命名空間會提供相關類型的邏輯分組。 您可以在新的或現有命名空間中建立您的控制項。 在 C# 中，`using` 宣告 (在 Visual Basic 中為 `Imports`) 允許從命名空間存取類型，而不需使用完整的類型名稱。 在下列範例中，`using`宣告可讓程式碼，以存取該類別<xref:System.Windows.Forms.Control>從<xref:System.Windows.Forms?displayProperty=nameWithType>只要<xref:System.Windows.Forms.Control>而不需使用完整格式的名稱<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>在表單上使用自訂控制項

下列範例顯示一個使用 `FirstControl` 的簡單表單。 它會建立三個 `FirstControl` 執行個體，各有不同的 `TextAlignment` 值。

#### <a name="to-compile-and-run-this-sample"></a>若要編譯和執行這個範例

1. 將下列範例中的程式碼儲存至原始程式檔 (SimpleForm.cs 或 SimpleForms.vb)。

2. 從包含原始程式檔的目錄執行下列命令，將原始程式檔編譯成可執行檔的組件。

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     CustomWinControls.dll 是包含類別的組件`FirstControl`。 此組件所在的目錄必須與存取該組件之表單的原始程式檔 (SimpleForm.cs 或 SimpleForms.vb) 相同。

3. 使用下列命令執行 SimpleForm.exe。

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項中的屬性](properties-in-windows-forms-controls.md)
- [Windows Forms 控制項中的事件](events-in-windows-forms-controls.md)
