---
title: "逐步解說：使用 Visual C# 繼承自 Windows Form 控制項 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 繼承"
  - "繼承, 控制項"
  - "繼承, 自訂控制項"
  - "繼承, 逐步解說"
  - "Windows Form 控制項, 繼承"
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 逐步解說：使用 Visual C# 繼承自 Windows Form 控制項
您可以使用 [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)]，透過「*繼承*」\(Inheritance\) 建立強大的自訂控制項。  經由繼承，您可以建立保留標準 Windows Form 控制項所有繼承功能的控制項，但同時可整合自訂功能。  在這個逐步解說中，您將建立名為 `ValueButton` 的簡單繼承控制項。  這個按鈕將從標準 Windows Form <xref:System.Windows.Forms.Button> 控制項繼承功能，並將公開 \(Expose\) 名為 `ButtonValue` 的自訂屬性。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 建立新專案時，您指定新專案名稱以便設定預設命名空間、組件名稱及專案名稱，同時也可確定預設元件會在正確的命名空間中。  
  
#### 若要建立 ValueButtonLib 控制項程式庫和 ValueButton 控制項  
  
1.  在 \[**檔案**\] 功能表上指向 \[**新增**\]，然後按一下 \[**專案**\] 以開啟 \[**新增專案**\] 對話方塊。  
  
2.  從 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 專案清單中選取 \[**Windows Form 控制項程式庫**\] 專案範本，然後在 \[**名稱**\] 方塊中輸入 `ValueButtonLib`。  
  
     依照預設，專案名稱 `ValueButtonLib` 也會指派到根命名空間。  預設命名空間是用來限定組件中的元件名稱。  例如，若有兩個組件提供名為 `ValueButton` 的元件，您就可以使用 `ValueButtonLib.ValueButton` 指定 `ValueButton` 元件。  如需詳細資訊，請參閱[命名空間](../Topic/Namespaces%20\(C%23%20Programming%20Guide\).md)。  
  
3.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**UserControl1.cs**\]，然後從捷徑功能表選擇 \[**重新命名**\]。  將檔案名稱變更為 `ValueButton.cs`。  當詢問您是否要重新命名對程式碼項目「`UserControl1`」的所有參考時，請按一下 \[**是**\] 按鈕。  
  
4.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**ValueButton.cs**\]，然後選取 \[**檢視程式碼**\]。  
  
5.  找到 `class` 陳述式行 `public partial class ValueButton`，並將這個控制項繼承自 <xref:System.Windows.Forms.UserControl> 的型別變更為 <xref:System.Windows.Forms.Button>。  這讓您的繼承控制項可以繼承 <xref:System.Windows.Forms.Button> 控制項的所有功能。  
  
6.  在 \[**方案總管**\] 中開啟 \[**ValueButton.cs**\] 節點，以顯示設計工具所產生的程式碼檔 \[**ValueButton.Designer.cs**\]。  在 \[**程式碼編輯器**\] 中開啟這個檔案。  
  
7.  尋找 `InitializeComponent` 方法，並移除指派 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> 屬性的程式碼行。  這個屬性不存在於 <xref:System.Windows.Forms.Button> 控制項。  
  
8.  從 \[**檔案**\] 功能表中選擇 \[**全部儲存**\] 以儲存專案。  
  
    > [!NOTE]
    >  視覺化設計工具已經無法使用。  由於 <xref:System.Windows.Forms.Button> 按鈕會自行繪製，因此您無法在設計工具中修改它的外觀。  它的視覺外觀會與它繼承類別的視覺外觀完全相同 \(也就是 <xref:System.Windows.Forms.Button>\)，除非在程式碼中有修改。  您仍然可以將沒有 UI 項目的元件加入至設計介面。  
  
## 加入屬性到繼承控制項  
 繼承的 Windows Form 控制項其中一個可能的用途是建立與標準 Windows Form 控制項外觀與感覺完全相同的控制項，但會公開自訂屬性。  在本章節中，您會將稱為 `ButtonValue` 的屬性加入至控制項。  
  
#### 若要加入 Value 屬性  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**ValueButton.cs**\]，然後按一下捷徑功能表上的 \[**檢視程式碼**\]。  
  
2.  找出 `class` 陳述式。  緊接在 `{` 之後，輸入下列程式碼：  
  
     \[C\#\]  
  
    ```  
    // Creates the private variable that will store the value of your   
    // property.  
    private int varValue;  
    // Declares the property.  
    public int ButtonValue  
    {  
       // Sets the method for retrieving the value of your property.  
       get  
       {  
          return varValue;  
       }  
       // Sets the method for setting the value of your property.  
       set  
       {  
          varValue = value;  
       }  
    }  
    ```  
  
     這個程式碼設定儲存及擷取 `ButtonValue` 屬性的方法。  `get` 陳述式將傳回的值設定為儲存在私用變數 `varValue` 中的值，而 `set` 陳述式使用 `value` 關鍵字來設定私用變數的值。  
  
3.  從 \[**檔案**\] 功能表中選擇 \[**全部儲存**\] 以儲存專案。  
  
## 測試控制項  
 控制項不是獨立的專案，必須裝載在容器中。  若要測試控制項，您必須提供用於執行控制項的測試專案。  也必須建置 \(編譯\) 控制項，讓測試專案能夠存取它。  在本章節中，您將建立自己的控制項，並在 Windows Form 中加以測試。  
  
#### 若要建置自己的控制項  
  
1.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     此時建置應會成功，不會有編譯器錯誤或警告。  
  
#### 若要建立測試專案  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**新增專案**\] 以開啟 \[**加入新的專案**\] 對話方塊。  
  
2.  選取 \[**Visual C\#**\] 節點下方的 \[**Windows**\] 節點，然後按一下 \[**Windows Form 應用程式**\]。  
  
3.  在 \[**名稱**\] 方塊中輸入 `Test`。  
  
4.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下測試專案的 \[**參考**\] 節點，然後從捷徑功能表中選取 \[**加入參考**\]，以便顯示 \[**加入參考**\] 對話方塊。  
  
5.  按一下標示為 \[**專案**\] 的索引標籤。  您的 `ValueButtonLib` 專案將列在 \[**專案名稱**\] 下。  按兩下專案，將參考加入至測試專案。  
  
6.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**測試**\]，然後選取 \[**建置**\]。  
  
#### 若要將控制項加入至表單  
  
1.  在 \[**方案總管**\] 中以滑鼠右鍵按一下 \[**Form1.cs**\]，然後從捷徑功能表選擇 \[**設計工具檢視**\]。  
  
2.  在 \[**工具箱**\] 中，按一下 \[**ValueButtonLib 元件**\]。  按兩下 \[**ValueButton**\]。  
  
     \[**ValueButton**\] 會出現在表單上。  
  
3.  以滑鼠右鍵按一下 \[**ValueButton**\]，然後從捷徑功能表選取 \[**屬性**\]。  
  
4.  在 \[**屬性**\] 視窗中，檢查這個控制項的屬性。  請注意除了多了一個屬性 `ButtonValue` 之外，這些屬性與標準按鈕公開的屬性完全相同。  
  
5.  將 `ButtonValue` 屬性設定為 `5`。  
  
6.  在 \[**工具箱**\] 的 \[**所有 Windows Form**\] 索引標籤中，按兩下 \[**Label**\]，將 <xref:System.Windows.Forms.Label> 控制項加入至表單。  
  
7.  重新將標籤放置到表單中央。  
  
8.  按兩下 `valueButton1`。  
  
     \[**程式碼編輯器**\] 會開啟至 `valueButton1_Click` 事件。  
  
9. 加入下列程式碼行。  
  
     \[C\#\]  
  
    ```  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. 在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**測試**\]，然後從捷徑功能表中選擇 \[**設定為啟始專案**\]。  
  
11. 從 \[**偵錯**\] 功能表中選取 \[**開始偵錯**\]。  
  
     `Form1` 便會出現。  
  
12. 按一下 `valueButton1`。  
  
     數字「5」會顯示在 `label1` 內，顯示繼承控制項的 `ButtonValue` 屬性已經由 `valueButton1_Click` 方法傳遞給 `label1`。  因此，您的 `ValueButton` 控制項繼承了標準 Windows Form 按鈕的所有功能，但公開了額外的自訂屬性。  
  
## 請參閱  
 [使用元件進行程式設計](../Topic/Programming%20with%20Components.md)   
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)   
 [如何：在選擇工具箱項目對話方塊中顯示控制項](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)   
 [逐步解說：使用 Visual C\# 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)