---
title: 逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f051d7a51a5f4ff8debf40fafbb8acfd8f7098f5
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182623"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>逐步解說：序列化標準類型的集合

您的自訂控制項有時會將集合公開為屬性。 本逐步解說示範如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>類別，控制如何在設計階段序列化集合。 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>將值套用至集合屬性，可確保將會序列化屬性。

若要將此主題中的程式碼複製為單一清單，請參閱[如何：使用 Designerserializationvisibilityattribute 序列化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))序列化標準類型的集合。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="create-a-control-with-a-serializable-collection"></a>建立具有可序列化集合的控制項

第一個步驟是建立具有可序列化集合做為屬性的控制項。 您可以使用 [**集合編輯器**] （可從 [**屬性**] 視窗存取）來編輯此集合的內容。

1. 在 Visual Studio 中，建立 Windows 控制項程式庫專案，並將其命名為**SerializationDemoControlLib**。

2. 將`UserControl1`重新`SerializationDemoControl`命名為。 如需詳細資訊，請參閱[重新命名程式碼符號重構](/visualstudio/ide/reference/rename)。

3. 在 [**屬性**] 視窗中，將<xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType>屬性的值設定為**10**。

4. 將控制項放在中`SerializationDemoControl`。 <xref:System.Windows.Forms.TextBox>

5. 選取 <xref:System.Windows.Forms.TextBox> 控制項。 在 [**屬性**] 視窗中，設定下列屬性。

    |屬性|變更為|
    |--------------|---------------|
    |**多行**|`true`|
    |**站**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |[ScrollBars]|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. 在 [程式**代碼編輯器**] 中，宣告名為`stringsValue`的`SerializationDemoControl`字串陣列欄位。

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. 在上定義`Strings`屬性。 `SerializationDemoControl`

   > [!NOTE]
   > <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>值是用來啟用集合的序列化。

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. 按**F5**以建立專案，並在**UserControl 測試容器**中執行您的控制項。

9. 在**UserControl 測試容器**的中<xref:System.Windows.Forms.PropertyGrid> ，尋找 [**字串**] 屬性。 選取 [**字串**] 屬性，然後選取省略號（![[Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕（...）] 按鈕，以開啟 [**字串集合編輯器**]。

10. 在 [**字串集合編輯器**] 中輸入數個字串。 請在每個字串的結尾按**enter**鍵來分隔它們。 完成輸入字串後，請按一下 **[確定]** 。

   > [!NOTE]
   > 您輸入的字串會出現在<xref:System.Windows.Forms.TextBox> `SerializationDemoControl`的。

## <a name="serialize-a-collection-property"></a>序列化集合屬性

若要測試控制項的序列化行為，請將它放在表單上，並使用 [**集合編輯器**] 來變更集合的內容。 您可以查看序列化的集合狀態，方法是查看**Windows Form 設計工具**發出程式碼的特殊設計工具檔案。

1. 將 Windows 應用程式專案新增至方案。 將專案命名為 `SerializationDemoControlTest`。

2. 在 [**工具箱**] 中，尋找名為 [ **SerializationDemoControlLib 元件**] 的索引標籤。 在此索引標籤中，您`SerializationDemoControl`會發現。 如需詳細資訊，請參閱[逐步解說：自動將自訂群組件](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)填入工具箱。

3. 將放`SerializationDemoControl`在您的表單上。

4. 在 [**屬性**] 視窗中尋找屬性。`Strings` 按一下屬性，然後按一下省略號（![ ](./media/visual-studio-ellipsis-button.png)[屬性視窗中 Visual Studio] 按鈕的省略號按鈕（...），以開啟 [**字串集合編輯器**]。 `Strings`

5. 在 [**字串集合編輯器**] 中輸入數個字串。 請在每個字串結尾按**enter**鍵來分隔它們。 完成輸入字串後，請按一下 **[確定]** 。

    > [!NOTE]
    > 您輸入的字串會出現在<xref:System.Windows.Forms.TextBox> `SerializationDemoControl`的。

6. 在方案總管中，按一下 [顯示所有檔案] 按鈕。

7. 開啟 [ **Form1** ] 節點。 其底下是名為**Form1.Designer.cs** **或 form1.vb 的檔案。** 這是**Windows Form 設計工具**發出程式碼的檔案，代表表單和其子控制項的設計階段狀態。 在 [程式碼編輯器] 中開啟此檔案。

8. 開啟名為 [ **Windows Form 設計工具產生**的程式碼] 的區域，然後尋找標示為**serializationDemoControl1**的區段。 此標籤底下的程式碼代表控制項的序列化狀態。 您在步驟5中輸入的字串會出現在`Strings`屬性的指派中。 下列程式碼範例C#和 Visual Basic 中，會顯示類似于您輸入 "red"、"橙色" 和 "黃色" 字串的程式碼。

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. 在 [程式**代碼編輯器**] 中，將<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> `Strings`屬性的值變更為<xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>。

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. 重建方案並重複步驟3和4。

> [!NOTE]
> 在此情況下， **Windows Form 設計工具**不會對`Strings`屬性發出任何指派。

## <a name="next-steps"></a>後續步驟

一旦您知道如何序列化標準類型的集合，請考慮將自訂控制項更深入地整合到設計階段環境中。 下列主題說明如何增強自訂控制項的設計階段整合：

- [設計階段架構](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Windows Forms 控制項中的屬性](attributes-in-windows-forms-controls.md)

- [設計工具序列化總覽](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Forms 控制項](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [逐步解說：使用自訂群組件自動填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
