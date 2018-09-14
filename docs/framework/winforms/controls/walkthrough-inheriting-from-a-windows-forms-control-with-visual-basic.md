---
title: 逐步解說：使用 Visual Basic 繼承自 Windows Form 控制項
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 6c70de1bf6a5340b6f5b2c652110ed9be5536665
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507806"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>逐步解說：使用 Visual Basic 繼承自 Windows Form 控制項
使用 Visual Basic 中，您可以建立功能強大的自訂控制項，透過*繼承*。 您可以透過繼承建立控制項，不僅保留標準 Windows Forms 控制項的所有固有功能，同時也納入自訂功能。 在本逐步解說中，您將會建立簡單的繼承控制項，名為 `ValueButton`。 此按鈕會繼承標準 Windows Form 的功能<xref:System.Windows.Forms.Button>控制項，並會公開 （expose） 的自訂屬性，稱為`ButtonValue`。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>建立專案  
 當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>若要建立 ValueButtonLib 控制項程式庫和 ValueButton 控制項  
  
1.  在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。  
  
2.  選取 [ **Windows Form 控制項程式庫**專案範本，從清單中的 Visual Basic 專案，然後輸入`ValueButtonLib`中**名稱**] 方塊中。  
  
     專案名稱，`ValueButtonLib`，預設也會指派給根命名空間。 根命名空間是用來限定組件中的元件名稱。 例如，如果兩個組件提供元件，名為 `ValueButton`，您可以使用 `ValueButtonLib.ValueButton` 指定您的 `ValueButton` 元件。 如需詳細資訊，請參閱 [Visual Basic 中的命名空間](~/docs/visual-basic/programming-guide/program-structure/namespaces.md)。  
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下 [UserControl1.vb]，然後從捷徑功能表選擇 [重新命名]。 將檔案名稱變更為 `ValueButton.vb`。 當系統詢問您是否要重新命名程式碼元素 'UserControl1' 的所有參考時，按一下 [是]按鈕。  
  
4.  在方案總管中，按一下 [顯示所有檔案] 按鈕。  
  
5.  開啟 [ValueButton.vb] 節點以顯示設計工具產生的程式碼檔案，**ValueButton.Designer.vb**。 在 [程式碼編輯器] 中開啟此檔案。  
  
6.  找出`Class`陳述式中， `Partial Public Class ValueButton`，並將變更從這個控制項繼承的型別<xref:System.Windows.Forms.UserControl>至<xref:System.Windows.Forms.Button>。 這可讓繼承的控制項繼承的所有功能<xref:System.Windows.Forms.Button>控制項。  
  
7.  找出`InitializeComponent`方法，並移除行，該指派<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>屬性。 這個屬性不存在於<xref:System.Windows.Forms.Button>控制項。  
  
8.  從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。  
  
     請注意，視覺化設計工具再也無法使用。 因為<xref:System.Windows.Forms.Button>控制項沒有自己的繪製，您就無法修改其外觀的設計工具中。 其視覺表示將會完全與它所繼承之類別的相同 (也就是<xref:System.Windows.Forms.Button>) 除非修改程式碼中。  
  
> [!NOTE]
>  您仍然可以將元件 (其中沒有任何 UI 元素) 新增至設計介面。  
  
## <a name="adding-a-property-to-your-inherited-control"></a>將屬性新增至繼承的控制項  
 繼承 Windows Forms 控制項的可能用法之一是建立外觀和行為 (外觀及操作) 與標準的 Windows Forms 控制項相同的控制項，但是公開自訂屬性。 在本節中，您會將名為 `ButtonValue` 的屬性新增至您的控制項。  
  
#### <a name="to-add-the-value-property"></a>若要新增 Value 屬性  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.vb]，然後從捷徑功能表按一下 [檢視程式碼]。  
  
2.  尋找 `Public Class ValueButton` 陳述式。 緊接在此陳述式底下，輸入下列程式碼：  
  
    ```vb  
    ' Creates the private variable that will store the value of your   
    ' property.  
    Private varValue as integer  
    ' Declares the property.  
    Property ButtonValue() as Integer  
    ' Sets the method for retrieving the value of your property.  
       Get  
          Return varValue  
       End Get  
    ' Sets the method for setting the value of your property.  
       Set(ByVal Value as Integer)  
          varValue = Value  
       End Set  
    End Property  
    ```  
  
     此程式碼會設定方法，系統會使用該方法來儲存和擷取 `ButtonValue` 屬性。 `Get` 陳述式會將傳回值設為儲存在私用變數 `varValue` 的值，而 `Set` 陳述式會使用 `Value` 關鍵字設定私用變數的值。  
  
3.  從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。  
  
## <a name="testing-your-control"></a>測試您的控制項  
 控制項不是獨立專案；它們必須裝載在容器中。 若要測試您的控制項，您必須提供測試專案讓控制項在其中執行。 您也必須藉由建置 (編譯) 控制項，讓控制項可供測試專案存取。 在本節中，您將會建置您的控制項，並且在 Windows Form 中進行測試。  
  
#### <a name="to-build-your-control"></a>若要建置您的控制項  
  
1.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。  
  
     建置應該會成功，沒有編譯器錯誤或警告。  
  
#### <a name="to-create-a-test-project"></a>若要建立測試專案  
  
1.  在 [檔案] 功能表上，指向 [新增]，然後選取 [新增專案]，以開啟 [加入新的專案]對話方塊。  
  
2.  選取 [Visual Basic] 專案節點，然後按一下**Windows Forms 應用程式**。  
  
3.  在 [名稱] 方塊中，輸入 `Test`。  
  
4.  在方案總管中，按一下 [顯示所有檔案] 按鈕。  
  
5.  在 [方案總管] 中，以滑鼠右鍵按一下測試專案的 [參考] 節點，然後從捷徑功能表選取 [加入參考]，以顯示 [加入參考] 對話方塊。  
  
6.  按一下 [專案] 索引標籤。  
  
7.  按一下標籤為 [專案] 的索引標籤。 您的 `ValueButtonLib` 專案會列在 [專案名稱] 底下。 按兩下專案以將參考新增至測試專案。  
  
8.  在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後選取 [建置]。  
  
#### <a name="to-add-your-control-to-the-form"></a>若要將控制項新增至表單  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [Form1.vb]，然後從捷徑功能表選擇 [檢視表設計工具]。  
  
2.  在 [工具箱] 中，按一下 [ValueButtonLib 元件]。 按兩下 [ValueButton]。  
  
     [ValueButton] 隨即出現在表單上。  
  
3.  以滑鼠右鍵按一下 [ValueButton]，然後從捷徑功能表選取 [屬性]。  
  
4.  在 [屬性] 視窗中，檢查此控制項的屬性。 請注意，它們與標準按鈕所公開的屬性相同，不同之處是有一個額外屬性，`ButtonValue`。  
  
5.  將 `ButtonValue` 屬性設定為 `5`。  
  
6.  上**所有的 Windows Form**索引標籤**工具箱**，連按兩下**標籤**新增<xref:System.Windows.Forms.Label>控制項至表單。  
  
7.  重新將標籤放置在表單的中央。  
  
8.  按兩下 `ValueButton1`。  
  
     在 [程式碼編輯器] 中開啟至 `ValueButton1_Click` 事件。  
  
9. 輸入下列程式碼行。  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. 在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後從捷徑功能表選擇 [設定為啟始專案]。  
  
11. 從 [偵錯] 功能表中，選取 [開始偵錯]。  
  
     `Form1` 隨即出現。  
  
12. 按一下 `Valuebutton1`。  
  
     數字 '5' 會顯示在 `Label1` 中，示範繼承的控制項之 `ButtonValue` 屬性已透過 `ValueButton1_Click` 方法傳遞至 `Label1`。 因此，`ValueButton` 控制項會繼承標準 Windows Forms 按鈕的所有功能，但是會公開額外的自訂屬性。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [操作說明：在選擇工具箱項目對話方塊中顯示控制項](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [使用 .NET Framework 開發自訂的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [繼承的基本概念 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [元件撰寫逐步解說](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
