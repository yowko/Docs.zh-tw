---
title: 逐步解說：示範視覺化繼承
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: b17de01c4a5e89051393aa3c6bb2d0079535dbf6
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746201"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>逐步解說：示範視覺化繼承
視覺化繼承可讓您查看基底表單上的控制項，並加入新的控制項。 在本逐步解說中，您將建立基底表單，並編譯為類別庫。 您將匯入此類別庫至另一個專案，並建立繼承自基底表單的新表單。 在這個逐步解說期間，您將了解如何：  
  
-   建立包含基底表單的類別庫專案。  
  
-   加入屬性可由基底表單衍生類別修改的按鈕。  
  
-   加入無法由基底表單繼承者修改的按鈕。  
  
-   建立包含繼承自 `BaseForm` 表單的專案。  
  
 最後，本逐步解說將示範繼承的表單上私用和受保護控制項之間的差異。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
> [!CAUTION]
>  並非所有控制項都支援來自基底表單的視覺化繼承。 下列控制項並不支援在此逐步解說中所描述的案例：  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  繼承的表單中的這些控制項永遠唯讀，不論您使用的修飾詞為何 (`private``protected` 或 `public`)。  
  
## <a name="scenario-steps"></a>案例步驟  
 第一個步驟是建立基底表單。  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>建立包含基底表單的類別庫專案：  
  
1.  從**檔案**功能表上，選擇**新增**，然後**專案**以開啟**新專案**對話方塊。  
  
2.  建立名為 Windows Forms 應用程式`BaseFormLibrary`。  
  
3.  在中建立類別庫，而不是標準的 Windows Forms 應用程式中，**方案總管**，以滑鼠右鍵按一下**BaseFormLibrary**專案節點，然後選取**屬性**.  
  
4.  在專案屬性中，變更**輸出型別**從**Windows 應用程式**來**類別庫**。  
  
5.  從**檔案**功能表上，選擇**全部儲存**，將專案和檔案儲存至預設位置。  
  
 下面兩個程序將按鈕加入至基底表單。 為了示範視覺化繼承，您將藉由設定 `Modifiers` 屬性，授與這些按鈕不同存取層級。  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>加入基底表單繼承者可以修改的按鈕：  
  
1.  開啟**Form1**設計工具中。  
  
2.  在上**所有的 Windows Form**索引標籤**工具箱**，按兩下**按鈕**將按鈕新增至表單。 使用滑鼠來定位並調整按鈕的大小。  
  
3.  在屬性視窗中設定下列按鈕屬性：  
  
    -   設定**文字**屬性設**Say Hello**。  
  
    -   設定 **（名稱）** 屬性設**為 btnProtected**。  
  
    -   設定**修飾詞**屬性設**受保護**。 這可讓繼承的表單**Form1**若要修改的屬性**為 btnProtected**。  
  
4.  按兩下**Say Hello**按鈕以新增事件處理常式**按一下**事件。  
  
5.  將下列這行程式碼加入至事件處理常式：  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>加入無法由基底表單繼承者修改的按鈕：  
  
1.  切換到設計檢視，即可**Form1.vb [設計]]、 [Form1.cs [Design] 或 [Form1.jsl [Design]** ] 索引標籤上方的程式碼編輯器中，或按下 f7 鍵。  
  
2.  加入第二個按鈕，並設定其屬性，如下所示：  
  
    -   設定**文字**屬性設**Say Goodbye**。  
  
    -   設定 **（名稱）** 屬性設**為 btnPrivate**。  
  
    -   設定**修飾詞**屬性設**私人**。 這無法讓繼承的表單**Form1**若要修改的屬性**為 btnPrivate**。  
  
3.  按兩下**Say Goodbye**按鈕以新增事件處理常式**按一下**事件。 將下列這行程式碼放在事件程序：  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  從**建置**功能表上，選擇**建置 BaseForm 程式庫**建置類別庫。  
  
     一旦建立程式庫之後，您可建立新專案，其繼承自剛建立的表單。  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>若要建立包含表單的專案，其表單繼承自基底表單  
  
1.  從**檔案**功能表上，選擇**新增**，然後**新專案**以開啟**加入新的專案** 對話方塊。  
  
2.  建立名為 Windows Forms 應用程式`InheritanceTest`。  
  
#### <a name="to-add-an-inherited-form"></a>若要加入繼承的表單  
  
1.  在**方案總管**，以滑鼠右鍵按一下**InheritanceTest**專案，然後選取**新增**，然後選取**新項目**。  
  
2.  在 **加入新項目**對話方塊中，選取**Windows Forms**類別目錄 （如果您有一個類別目錄清單），然後選取**繼承的表單**範本。  
  
3.  保留預設名稱`Form2`，然後按一下 **新增**。  
  
4.  在 **繼承選取器**對話方塊中，選取**Form1**從**BaseFormLibrary**表單繼承，並按一下 專案**確定**.  
  
     這會建立在表單**InheritanceTest**衍生自的表單中的專案**BaseFormLibrary**。  
  
5.  開啟繼承的表單 (**Form2**) 在設計工具中按兩下它，如果它尚未開啟。  
  
     在設計師中，繼承的按鈕有符號 (![VisualBasicInheritanceSymbol 螢幕擷取畫面](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) 在其上方角落，表示受到繼承。  
  
6.  選取  **Say Hello**按鈕，並觀察調整大小控點。 因為此按鈕已受到保護，所以繼承者可以移動它、調整大小、變更標題和進行其他修改。  
  
7.  選取 私用**Say Goodbye**按鈕，並注意它沒有調整大小控點。 此外，在**屬性** 視窗中，這個按鈕的屬性會呈現灰色，表示無法修改它們。  
  
8.  如果您使用的 Visual C#:  
  
    1.  在 **方案總管**，以滑鼠右鍵按一下**Form1**中**InheritanceTest**專案，然後選擇**刪除**。 在隨即出現訊息方塊中，按一下**確定**以確認刪除。  
  
    2.  開啟 Program.cs 檔案並變更 `Application.Run(new Form1());` 為 `Application.Run(new Form2());`。  
  
9. 在 **方案總管**，以滑鼠右鍵按一下**InheritanceTest**專案，然後選取**設定為啟始專案**。  
  
10. 在 **方案總管**，以滑鼠右鍵按一下**InheritanceTest**專案，然後選取**屬性**。  
  
11. 在  **InheritanceTest**屬性頁，設定**啟始物件**要繼承的表單 (**Form2**)。  
  
12. 按 F5 執行應用程式，並觀察繼承的表單之行為。  
  
## <a name="next-steps"></a>後續步驟  
 使用者控制項的繼承以非常類似的方式運作。 開啟一個新的類別庫專案，並加入使用者控制項。 將構成控制項放在上面，然後編譯專案。 開啟另一個新的類別庫專案，並加入已編譯類別程式庫的參考。 此外，請嘗試加入繼承的控制項 (透過**加入新項目** 對話方塊中) 至專案並使用**繼承選取器**。 將使用者控制項，並將變更`Inherits`(`:` Visual C#) 陳述式。 如需詳細資訊，請參閱 <<c0> [ 如何： 繼承 Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：繼承 Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Windows Forms 視覺繼承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
