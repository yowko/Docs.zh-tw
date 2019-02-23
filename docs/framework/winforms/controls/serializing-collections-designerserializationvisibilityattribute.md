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
ms.openlocfilehash: 5ec32f5c365162883797b3f3f9ece4305dce7551
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747660"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合
您的自訂控制項有時候會公開為屬性的集合。 本逐步解說示範如何使用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>類別來控制如何在設計階段序列化集合。 套用<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>集合屬性的值可確保會序列化屬性。  
  
 若要將此主題中的程式碼複製為單一清單，請參閱[如何：序列化標準類型使用 DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您將需要：  
  
-   若要能夠建立和安裝 Visual Studio 的電腦上執行 Windows Form 應用程式專案有足夠的權限。  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>建立控制項都有一個可序列化的集合  
 第一個步驟是建立具有可序列化的集合，做為屬性的控制項。 您可以編輯此集合使用的內容**集合編輯器**，您可以從存取**屬性**視窗。  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>若要建立具有可序列化集合的控制項  
  
1.  建立 Windows 控制項程式庫專案，稱為`SerializationDemoControlLib`。 如需詳細資訊，請參閱 < [Windows 控制項程式庫範本](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))。  
  
2.  重新命名`UserControl1`至`SerializationDemoControl`。 如需詳細資訊，請參閱 <<c0> [ 重新命名重構程式碼符號](/visualstudio/ide/reference/rename)。  
  
3.  在 **屬性**視窗中，設定的值<xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType>屬性設`10`。  
  
4.  地方<xref:System.Windows.Forms.TextBox>控制在`SerializationDemoControl`。  
  
5.  選取 <xref:System.Windows.Forms.TextBox> 控制項。 在 [**屬性**] 視窗中，設定下列屬性。  
  
    |屬性|變更為|  
    |--------------|---------------|  
    |**多行**|`true`|  
    |**Dock**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |[ScrollBars]|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**ReadOnly**|`true`|  
  
6.  在 **程式碼編輯器**，宣告名為字串陣列欄位`stringsValue`在`SerializationDemoControl`。  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  定義`Strings`屬性上的`SerializationDemoControl`。  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>值用來啟用集合的序列化。  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。  
  
2.  尋找`Strings`中的屬性<xref:System.Windows.Forms.PropertyGrid>的**UserControl 測試容器**。 按一下 `Strings`屬性，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，即可開啟**字串集合編輯器**.  
  
3.  輸入中的數個字串**字串集合編輯器**。 藉由按下 ENTER 鍵，每個字串的結尾分隔。 按一下 **確定**當您完成輸入字串。  
  
> [!NOTE]
>  您所輸入的字串會出現在<xref:System.Windows.Forms.TextBox>的`SerializationDemoControl`。  
  
## <a name="serializing-a-collection-property"></a>序列化集合屬性  
 若要測試您的控制項的序列化行為，您會將它放在表單上，並變更集合的內容**集合編輯器**。 您可以看到序列化的集合的狀態，藉由查看特殊的設計工具檔案，其中**Windows Form 設計工具**會發出程式碼。  
  
#### <a name="to-serialize-a-collection"></a>將序列化集合  
  
1.  將 Windows 應用程式專案加入方案。 將專案命名為 `SerializationDemoControlTest`。  
  
2.  在 **工具箱**，尋找名為  索引標籤**SerializationDemoControlLib 元件**。 在此索引標籤中，您會發現`SerializationDemoControl`。 如需詳細資訊，請參閱[逐步解說：自動將 [工具箱] 中的以自訂元件填入](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。  
  
3.  位置`SerializationDemoControl`您的表單上。  
  
4.  尋找`Strings`中的屬性**屬性**視窗。 按一下 `Strings`屬性，然後按一下省略符號 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕，即可開啟**字串集合編輯器**.  
  
5.  輸入中的數個字串**字串集合編輯器**。 藉由按下 ENTER 鍵，每個字串的結尾分隔。 按一下 **確定**當您完成輸入字串。  
  
> [!NOTE]
>  您所輸入的字串會出現在<xref:System.Windows.Forms.TextBox>的`SerializationDemoControl`。  
  
1.  在方案總管中，按一下 [顯示所有檔案] 按鈕。  
  
2.  開啟**Form1**節點。 這是檔案，呼叫的下方**Form1.Designer.cs**或是**Form1.Designer.vb**。 這是在其中的檔案**Windows Form 設計工具**會發出程式碼表示您的表單和其子控制項的設計階段狀態。 在 [程式碼編輯器] 中開啟此檔案。  
  
3.  開啟區域稱為**Windows 表單設計工具產生的程式碼**並尋找 [標記] 區段**serializationDemoControl1**。 此標籤之下是代表您控制項的序列化的狀態的程式碼。 您在步驟 5 輸入的字串會出現在指派至`Strings`屬性。 C# 和 Visual Basic 中的下列程式碼範例顯示程式碼類似於您將會看到您輸入字串"red"、 「 橙色 」 和 「 黃色 」。  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  在 **程式碼編輯器**，變更的值<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>上`Strings`屬性設<xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>。  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. 重建方案，然後重複步驟 3 和 4。  
  
> [!NOTE]
>  在此情況下， **Windows Form 設計工具**不發出的任何指派`Strings`屬性。  
  
## <a name="next-steps"></a>後續步驟  
 一旦您知道如何序列化標準類型的集合，請考慮將您的自訂控制項更深入整合至設計階段環境。 下列主題說明如何增強您的自訂控制項的設計階段整合：  
  
-   [設計階段架構](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))  
  
-   [Windows Forms 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [設計工具序列化概觀](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))  
  
-   [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [設計工具序列化概觀](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))
- [如何：序列化標準類型使用 DesignerSerializationVisibilityAttribute 的集合](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
- [逐步解說：自動填入 [工具箱] 中的以自訂元件](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
