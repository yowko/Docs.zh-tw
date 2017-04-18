---
title: "逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "集合, 序列化"
  - "集合, 標準類型"
  - "DesiginerSerializationVisibilityAttribute 類別"
  - "序列化, 集合"
  - "標準類型, 集合"
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合
您的自訂控制項有時候會將集合公開 \(Expose\) 為屬性。  這個逐步解說示範如何使用 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> 類別控制集合在設計階段序列化的方式。  套用 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> 值至您的集合屬性，能確保序列化該屬性。  
  
 若要將此主題中的程式碼複製為一份清單，請參閱 [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 若要完成這個逐步解說，您必須要有：  
  
-   擁有足夠的使用權限，可以在安裝 Visual Studio 的電腦上建立並執行 Windows Form 應用程式專案。  
  
## 建立具有可序列化集合的控制項  
 第一步是建立具有可序列化集合做為屬性的控制項。  您可以使用 \[**集合編輯器**\] 編輯此集合的內容 \(可以從 \[**屬性**\] 視窗存取集合編輯器\)。  
  
#### 若要建立有序列化集合的控制項  
  
1.  建立名為 `SerializationDemoControlLib` 的 Windows 控制項程式庫專案。  如需詳細資訊，請參閱 [Windows Control Library Template](http://msdn.microsoft.com/zh-tw/722f4e2d-1310-4ed5-8f33-593337ab66b4)。  
  
2.  將 `UserControl1` 重新命名為 `SerializationDemoControl`。  如需詳細資訊，請參閱 [How to: Rename Identifiers](http://msdn.microsoft.com/zh-tw/2430f732-2b70-4516-8cf6-a7bb71cc9724)。  
  
3.  在 \[**屬性**\] 視窗中，將 <xref:System.Windows.Forms.Padding.All%2A?displayProperty=fullName> 屬性值設定為 `10`。  
  
4.  在 `SerializationDemoControl` 中放置 <xref:System.Windows.Forms.TextBox> 控制項。  
  
5.  選取 <xref:System.Windows.Forms.TextBox> 控制項。  在 \[**屬性**\] 視窗中，檢視下列屬性。  
  
    |屬性|變更為|  
    |--------|---------|  
    |**Multiline**|`true`|  
    |**Dock**|<xref:System.Windows.Forms.DockStyle>|  
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars>|  
    |**ReadOnly**|`true`|  
  
6.  在 \[**程式碼編輯器**\] 中，在 `SerializationDemoControl` 中宣告名為 `stringsValue` 的字串陣列欄位。  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  定義 `SerializationDemoControl` 上的 `Strings` 屬性。  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> 值是用來啟用集合的序列化。  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  按下 F5 鍵以建置專案，並在 \[**使用者控制項測試容器**\] 中執行控制項。  
  
2.  在 \[**UserControl Test Container**\] 的 <xref:System.Windows.Forms.PropertyGrid> 中尋找 `Strings` 屬性。  按一下 `Strings` 屬性，然後按一下省略號 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕以開啟 \[**字串集合編輯器**\]。  
  
3.  在 \[**字串集合編輯器**\] 中輸入數個字串。  在每個字串的結尾按下 ENTER 鍵，藉此分隔各個字串。  當您輸入完字串後，請按一下 \[**確定**\]。  
  
> [!NOTE]
>  您輸入的字串會顯示在 `SerializationDemoControl` 的 <xref:System.Windows.Forms.TextBox> 中。  
  
## 序列化集合屬性  
 若要測試控制項的序列化行為，請將控制項放置在表單上，並使用 \[**集合編輯器**\] 變更集合的內容。  您可藉由查看特殊的設計工具檔來檢視序列化集合狀態，\[**Windows Form 設計工具**\] 會對此設計工具檔發出程式碼。  
  
#### 若要序列化集合  
  
1.  將 Windows 應用程式專案加入至方案。  將專案命名為 `SerializationDemoControlTest`。  
  
2.  在 \[**工具箱**\] 中尋找名為 \[**SerializationDemoControlLib Components**\] 的索引標籤。  在此索引標籤中您會找到 `SerializationDemoControl`。  如需詳細資訊，請參閱[逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。  
  
3.  將 `SerializationDemoControl` 放置到表單上。  
  
4.  在 \[**屬性**\] 視窗中尋找 `Strings` 屬性。  按一下 `Strings` 屬性，然後按一下省略號 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) 按鈕以開啟 \[**字串集合編輯器**\]。  
  
5.  在 \[**字串集合編輯器**\] 中輸入數個字串。  在每個字串的結尾按下 ENTER 鍵，藉此分隔各個字串。  當您輸入完字串後，請按一下 \[**確定**\]。  
  
> [!NOTE]
>  您輸入的字串會顯示在 `SerializationDemoControl` 的 <xref:System.Windows.Forms.TextBox> 中。  
  
1.  在 \[**方案總管**\] 中按一下 \[**顯示所有檔案**\] 按鈕。  
  
2.  開啟 \[**Form1**\] 節點。  在該節點下方是稱為 \[**Form1.Designer.cs**\] 或 \[**Form1.Designer.vb**\] 的檔案。  \[**Windows Form 設計工具**\] 會將代表表單和子控制項設計階段狀態的程式碼發出至這個檔案。  在 \[**程式碼編輯器**\] 中開啟這個檔案。  
  
3.  開啟稱為 \[**Windows Form 設計工具產生的程式碼**\] 的區域，並尋找標記為 \[**serializationDemoControl1**\] 的區段。  在這個標籤底下，是代表控制項序列化狀態的程式碼。  您在步驟 5 輸入的字串會顯示於對 `Strings` 屬性的指派。  下列程式碼範例示範在輸入字串「red」、「orange」和「yellow」時會看見的類似程式碼。  
  
4.  \[Visual Basic\]  
  
    ```  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```  
  
5.  \[C\#\]  
  
    ```  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
  
6.  在 \[**程式碼編輯器**\] 中，將 `Strings` 屬性上 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> 的值變更為 <xref:System.ComponentModel.DesignerSerializationVisibility>。  
  
7.  \[Visual Basic\]  
  
    ```  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
8.  \[C\#\]  
  
    ```  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
  
9. 重新建置方案，並重複步驟 4 到 8。  
  
> [!NOTE]
>  在這種情況下，\[**Windows Form 設計工具**\] 不會發出任何指派給 `Strings` 屬性。  
  
## 後續步驟  
 一旦您知道如何序列化標準型別的集合，請考慮將自訂控制項更深入整合到設計階段環境中。  下列主題會描述如何增強自訂控制項的設計階段整合：  
  
-   [Design\-Time Architecture](../Topic/Design-Time%20Architecture.md)  
  
-   [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Designer Serialization Overview](../Topic/Designer%20Serialization%20Overview.md)  
  
-   [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## 請參閱  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>   
 [Designer Serialization Overview](../Topic/Designer%20Serialization%20Overview.md)   
 [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)   
 [逐步解說：自動將自訂元件填入工具箱](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)