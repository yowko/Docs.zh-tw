---
title: 逐步解說：實作 COM 物件 (Visual Basic) 的繼承
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 79d80a1a91911a361bd21f1f3f74424f4f656a18
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620047"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>逐步解說：實作 COM 物件 (Visual Basic) 的繼承
您可以衍生從 Visual Basic 類別`Public`中 COM 物件，即使在舊版的 Visual Basic 中建立的類別。 屬性和方法，從 COM 物件繼承的類別可以覆寫或多載，就如同屬性和任何其他基底類別的方法可以覆寫或多載。 當您有現有的類別程式庫，您不希望重新編譯時，適合使用 COM 物件的繼承。  
  
 下列程序示範如何使用 Visual Basic 6.0 中建立 COM 物件，包含類別，並將它作為基底類別。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>若要建立本逐步解說中使用的 COM 物件  
  
1. 在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。 專案，命名為`Project1`建立。 它有一個名為類別`Class1`。  
  
2. 在**專案總管**，以滑鼠右鍵按一下**Project1**，然後按一下**Project1 屬性**。 **專案屬性**對話方塊隨即出現。  
  
3. 在上**一般**索引標籤**專案屬性**對話方塊方塊中，輸入變更專案名稱`ComObject1`中**專案名稱**欄位。  
  
4. 在**專案總管**，以滑鼠右鍵按一下`Class1`，然後按一下**屬性**。 **屬性**類別 視窗隨即顯示。  
  
5. 變更`Name`屬性設`MathFunctions`。  
  
6. 在**專案總管**，以滑鼠右鍵按一下`MathFunctions`，然後按一下**檢視程式碼**。 **程式碼編輯器**隨即出現。  
  
7. 新增本機變數來保存屬性值：  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8. 將屬性加入`Let`和屬性`Get`屬性程序：  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. 新增函式：  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 建立並登錄的 COM 物件，依序按一下**讓 ComObject1.dll**上**檔案**功能表。  
  
    > [!NOTE]
    >  雖然您也可以公開使用的 COM 物件的 Visual Basic 建立的類別，它不是真正的 COM 物件，並不能在此逐步解說。 如需詳細資訊，請參閱 < [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="interop-assemblies"></a>Interop 組件  
 在下列程序中，您將建立 interop 組件，做為 unmanaged 程式碼 （例如 COM 物件） 與 Visual Studio 會使用 managed 程式碼之間的橋樑。 Visual Basic 建立 interop 組件會處理許多這類使用 COM 物件的詳細資料*interop 封送處理*，封裝參數和傳回值，對等資料的程序類型，因為它們將移至和從 COM 物件。 Visual Basic 應用程式中的參考會指向 interop 組件，而不是實際的 COM 物件。  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>若要使用 Visual Basic 2005 和更新版本中的 COM 物件  
  
1. 開啟新的 Visual Basic Windows 應用程式專案。  
  
2. 在 [專案] 功能表上，按一下 [新增參考]。  
  
     [新增參考] 對話方塊隨即顯示。  
  
3. 在上**COM**索引標籤上，按兩下`ComObject1`中**元件名稱**清單，然後按一下**確定**。  
  
4. 在 [專案]  功能表中，按一下 [加入新項目] 。  
  
     隨即顯示 [ 新增項目] 對話方塊。  
  
5. 在 **範本**窗格中，按一下**類別**。  
  
     預設檔案名稱， `Class1.vb`，會出現在**名稱**欄位。 將此欄位變更為 MathClass.vb，然後按一下 **新增**。 這會建立名為類別`MathClass`，並顯示其程式碼。  
  
6. 將下列程式碼加入至頂端`MathClass`從 COM 類別繼承。  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7. 多載基底類別的公用方法，藉由新增下列程式碼`MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8. 新增下列程式碼來擴充繼承的類別`MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 新的類別會繼承基底類別中的 COM 物件的屬性、 多載方法，並定義新方法來擴充類別。  
  
#### <a name="to-test-the-inherited-class"></a>若要測試繼承的類別  
  
1. 將按鈕加入您的啟動表單，然後按兩下以檢視其程式碼。  
  
2. 在按鈕的`Click`事件處理常式的程序，新增下列程式碼，建立的執行個體`MathClass`呼叫多載的方法：  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3. 按 F5 執行專案。  
  
 當您按一下表單上的按鈕`AddNumbers`與第一次呼叫方法`Short`資料類型的數字和 Visual Basic 會選擇適當的方法基底類別。 第二次呼叫`AddNumbers`會導向至多載方法，從`MathClass`。 第三個呼叫呼叫`SubtractNumbers`擴充類別的方法。 設定基底類別中的屬性，並在顯示的值。  
  
## <a name="next-steps"></a>後續步驟  
 您可能已經注意到，多載`AddNumbers`函式似乎有相同的資料類型從 COM 物件的基底類別繼承的方法。 這是因為引數和基底類別方法的參數會定義為 Visual Basic 6.0 中的 16 位元整數，但它們會公開為 16 位元整數類型的`Short`在新版的 Visual Basic 中。 新的函式會接受 32 位元整數，並多載基底類別函式。  
  
 使用 COM 物件，請確定您已驗證的大小和資料類型的參數。 例如，當您使用接受做為引數的 Visual Basic 6.0 集合物件的 COM 物件時，您就無法提供更新版本的 Visual Basic 中的集合。  
  
 屬性和方法繼承自 COM 類別可以覆寫，這表示您可以宣告區域屬性或方法，以取代屬性或繼承自基底的 COM 類別的方法。 覆寫其他的屬性和方法，但有下列例外狀況的規則覆寫繼承的 COM 屬性的規則如下：  
  
- 如果您覆寫任何屬性或繼承自 COM 類別的方法，您必須覆寫所有其他繼承的屬性和方法。  
  
- 使用屬性`ByRef`無法覆寫參數。  
  
## <a name="see-also"></a>另請參閱

- [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)
