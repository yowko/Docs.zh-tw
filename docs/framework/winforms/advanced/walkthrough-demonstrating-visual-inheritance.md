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
ms.openlocfilehash: 32df98852b28963ffb748895156f7d9977c74b92
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046142"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>逐步解說：示範視覺化繼承

視覺化繼承可讓您查看基底表單上的控制項，並加入新的控制項。 在本逐步解說中，您將建立基底表單，並編譯為類別庫。 您將匯入此類別庫至另一個專案，並建立繼承自基底表單的新表單。 在這個逐步解說期間，您將了解如何：

- 建立包含基底表單的類別庫專案。

- 加入屬性可由基底表單衍生類別修改的按鈕。

- 加入無法由基底表單繼承者修改的按鈕。

- 建立包含繼承自 `BaseForm` 表單的專案。

最後，本逐步解說將示範繼承的表單上私用和受保護控制項之間的差異。

> [!CAUTION]
> 並非所有控制項都支援來自基底表單的視覺化繼承。 下列控制項並不支援在此逐步解說中所描述的案例：
>
> - <xref:System.Windows.Forms.WebBrowser>
>
> - <xref:System.Windows.Forms.ToolStrip>
>
> - <xref:System.Windows.Forms.ToolStripPanel>
>
> - <xref:System.Windows.Forms.TableLayoutPanel>
>
> - <xref:System.Windows.Forms.FlowLayoutPanel>
>
> - <xref:System.Windows.Forms.DataGridView>
>
> 繼承的表單中的這些控制項永遠唯讀，不論您使用的修飾詞為何 (`private``protected` 或 `public`)。

## <a name="create-a-class-library-project-containing-a-base-form"></a>建立包含基底表單的類別庫專案

1. 在 Visual Studio 中, 從 [檔案] 功能表選擇 [**新增** > **專案**], 開啟 [**新增專案**] 對話方塊。

2. 建立名為`BaseFormLibrary`的 Windows Forms 應用程式。

3. 若要建立類別庫, 而不是標準 Windows Forms 應用程式, 請在**方案總管**中, 以滑鼠右鍵按一下**baseformlibrary**專案節點, 然後選取 **屬性**。

4. 在專案的屬性中, 將 [**輸出類型**] 從 [ **Windows 應用程式**] 變更為 [**類別庫**]。

5. 從 [檔案] 功能表中, 選擇 [**全部儲存**], 將專案和檔案儲存到預設位置。

下面兩個程序將按鈕加入至基底表單。 為了示範視覺化繼承，您將藉由設定 `Modifiers` 屬性，授與這些按鈕不同存取層級。

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a>新增基底表單繼承者可以修改的按鈕

1. 在設計工具中，開啟 **Form1**。

2. 在 [**工具箱**] 的 [**所有 Windows Forms** ] 索引標籤上, 按兩下 [**按鈕**], 將按鈕新增至表單。 使用滑鼠來定位並調整按鈕的大小。

3. 在屬性視窗中設定下列按鈕屬性：

    - 將 [ **Text** ] 屬性設定為 [ **Hello**]。

    - 將 [ **(名稱)** ] 屬性設定為**btnProtected**。

    - 將 [修飾詞] 屬性設定為 [**受保護**]。 這讓繼承自**Form1**的表單能夠修改**btnProtected**的屬性。

4. 按兩下 [假設為**Hello** ] 按鈕, 以加入**click**事件的事件處理常式。

5. 將下列這行程式碼加入至事件處理常式：

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>加入無法由基底表單繼承者修改的按鈕

1. 按一下 [程式碼編輯器] 上方的 [form1.vb **[design]]、[Form1.cs [design]] 或 [form1.jsl [design]** ] 索引標籤, 或按 F7 鍵, 切換至設計檢視。

2. 加入第二個按鈕，並設定其屬性，如下所示：

    - 將 [ **Text** ] 屬性設定為 [**再見**]。

    - 將 [ **(名稱)** ] 屬性設定為**btnPrivate**。

    - 將 [修飾詞] 屬性設定為 [**私**用]。 這使得繼承自**Form1**的表單不可能修改**btnPrivate**的屬性。

3. 按兩下 [**說再見**] 按鈕, 以加入**click**事件的事件處理常式。 將下列這行程式碼放在事件程序：

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. 從 [**建立**] 功能表中, 選擇 [**組建 BaseForm 程式庫**] 以建立類別庫。

     一旦建立程式庫之後，您可建立新專案，其繼承自剛建立的表單。

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>建立專案, 其中包含繼承自基底表單的表單

1. 從 [檔案] 功能表中, 依序選擇 [**加入**] 和 [**新增專案**], 開啟 [**加入新的專案**] 對話方塊。

2. 建立名為`InheritanceTest`的 Windows Forms 應用程式。

## <a name="add-an-inherited-form"></a>加入繼承的表單

1. 在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案, 選取 **加入**, 然後選取 **新增專案**。

2. 在 [**加入新專案**] 對話方塊中, 選取 [ **Windows Forms** ] 類別 (如果您有一份類別清單), 然後選取 [**繼承的表單**] 範本。

3. 保留預設名稱`Form2` , 然後按一下 [**新增**]。

4. 在 **繼承選擇器** 對話方塊中, 從**baseformlibrary**專案選取  **Form1**  做為要繼承的表單, 然後按一下**確定**。

     這會在**inheritancetest**專案中建立衍生自**baseformlibrary**中表單的表單。

5. 按兩下設計工具中的繼承表單 (**Form2**), 如果尚未開啟, 請將它開啟。

    在設計工具中, 繼承的按鈕具有符號 (![Visual Basic 繼承符號的螢幕擷取畫面。](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)), 表示它們會被繼承。

6. 選取 [ **Hello** ] 按鈕, 並觀察調整大小控點。 因為此按鈕已受到保護，所以繼承者可以移動它、調整大小、變更標題和進行其他修改。

7. 選取 [私用] [**再見**] 按鈕, 並注意它沒有調整大小控點。 此外, 在 [**屬性**] 視窗中, 這個按鈕的屬性會呈現灰色, 表示無法修改它們。

8. 如果您使用的是C#視覺效果:

    1. 在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案中的  **Form1** , 然後選擇 **刪除**。 在出現的訊息方塊中, 按一下 **[確定]** 以確認刪除。

    2. 開啟 Program.cs 檔案並變更 `Application.Run(new Form1());` 為 `Application.Run(new Form2());`。

9. 在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案, 然後選取 **設定為啟始專案**。

10. 在**方案總管**中, 以滑鼠右鍵按一下**inheritancetest**專案, 然後選取 **屬性**。

11. 在  **inheritancetest**  屬性頁中, 將 **啟始物件** 設定為繼承的表單 (**Form2**)。

12. 按**F5**執行應用程式, 並觀察繼承表單的行為。

## <a name="next-steps"></a>後續步驟

使用者控制項的繼承以非常類似的方式運作。 開啟一個新的類別庫專案，並加入使用者控制項。 將構成控制項放在上面，然後編譯專案。 開啟另一個新的類別庫專案，並加入已編譯類別程式庫的參考。 此外, 請嘗試加入繼承的控制項 (透過 [**加入新專案**] 對話方塊) 至專案, 並使用 [**繼承選擇器**]。 加入使用者控制項, 並變更`Inherits` (`:`在 Visual C#) 語句中。 如需詳細資訊，請參閱[如何：繼承 Windows Forms](how-to-inherit-windows-forms.md)。

## <a name="see-also"></a>另請參閱

- [如何：繼承 Windows Forms](how-to-inherit-windows-forms.md)
- [Windows Forms 視覺繼承](windows-forms-visual-inheritance.md)
- [Windows Forms](../index.md)
