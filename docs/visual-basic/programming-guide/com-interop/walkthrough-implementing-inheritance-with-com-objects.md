---
title: 逐步解說：實作 COM 物件的繼承 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b03b81c9e04e79f8ce7763ecf8a489d248ff480b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>逐步解說：實作 COM 物件的繼承 (Visual Basic)
您可以取得 Visual Basic 類別從`Public`中 COM 物件，即使這些舊版本的 Visual Basic 中建立的類別。 屬性和類別繼承自 COM 物件的方法可以覆寫或多載一樣屬性和任何其他基底類別的方法可以覆寫或多載。 從 COM 物件的繼承時，您有現有的類別程式庫，您不希望重新編譯。  
  
 下列程序示範如何使用 Visual Basic 6.0 中建立的 COM 物件，包含類別，並以它做為基底類別。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>若要建立這個逐步解說中所使用的 COM 物件  
  
1.  在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。 專案，名為`Project1`建立。 它具有名為類別`Class1`。  
  
2.  在**專案總管**，以滑鼠右鍵按一下**Project1**，然後按一下  **Project1 屬性**。 **專案屬性**對話方塊隨即出現。  
  
3.  在**一般** 索引標籤**專案屬性**對話方塊方塊中，輸入新的專案名稱`ComObject1`中**專案名稱**欄位。  
  
4.  在**專案總管**，以滑鼠右鍵按一下`Class1`，然後按一下 **屬性**。 **屬性**類別 視窗隨即出現。  
  
5.  變更`Name`屬性`MathFunctions`。  
  
6.  在**Project Explorer**，以滑鼠右鍵按一下`MathFunctions`，然後按一下 **檢視程式碼**。 **程式碼編輯器**隨即出現。  
  
7.  加入本機變數來保存屬性值：  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  將屬性加入`Let`和屬性`Get`屬性程序：  
  
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
  
9. 加入函式：  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 建立並註冊的 COM 物件，依序按一下**進行 ComObject1.dll**上**檔案**功能表。  
  
    > [!NOTE]
    >  雖然您也可以公開使用 Visual Basic 為 COM 物件建立的類別，它不是真正的 COM 物件，並不能用在這個逐步解說。 如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="interop-assemblies"></a>Interop 組件  
 在下列程序中，您將建立 interop 組件，可做為 unmanaged 程式碼 （例如 COM 物件） 與 Visual Studio 會使用 managed 程式碼之間的橋樑。 Visual Basic 建立的 interop 組件會處理許多細節，例如使用 COM 物件的*interop 封送處理*，封裝參數和傳回值為對等資料的程序類型，因為它們將移到和從 COM 物件。 在 Visual Basic 應用程式中的參考指向的 interop 組件不是實際的 COM 物件。  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>使用 COM 物件來與 Visual Basic 2005 和更新版本  
  
1.  開啟新的 Visual Basic Windows 應用程式專案。  
  
2.  在 [專案] 功能表上，按一下 [新增參考]。  
  
     [新增參考] 對話方塊隨即顯示。  
  
3.  在**COM**索引標籤上，按兩下`ComObject1`中**元件名稱**清單，然後按一下**確定**。  
  
4.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
     隨即顯示 [ 新增項目] 對話方塊。  
  
5.  在**範本**] 窗格中，按一下 [**類別**。  
  
     預設檔案名稱， `Class1.vb`，會出現在**名稱**欄位。 此欄位變更為 MathClass.vb，然後按一下**新增**。 這會建立名為類別`MathClass`，並顯示其程式碼。  
  
6.  將下列程式碼加入至頂端`MathClass`繼承自 COM 類別。  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  多載基底類別的公用方法加入下列程式碼以`MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  加入下列程式碼來擴充繼承的類別`MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 新類別會繼承基底類別中的 COM 物件的屬性、 多載方法，並定義新的方法來擴充類別。  
  
#### <a name="to-test-the-inherited-class"></a>若要測試繼承的類別  
  
1.  啟動表單，加入按鈕，然後按兩下以檢視其程式碼。  
  
2.  在按鈕的`Click`事件處理常式的程序，加入下列程式碼建立的執行個體`MathClass`呼叫多載的方法：  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  按 F5 執行專案。  
  
 當您按一下表單上的按鈕`AddNumbers`與第一次呼叫方法`Short`資料類型的數字，Visual Basic 中的基底類別選擇適當方法。 第二個呼叫`AddNumbers`導向至多載方法，從`MathClass`。 第三個呼叫呼叫`SubtractNumbers`方法，延伸的類別。 基底類別中的屬性已設定，而且將會顯示值。  
  
## <a name="next-steps"></a>後續步驟  
 您可能已注意到，多載`AddNumbers`函式看似具有相同的資料類型繼承自基底類別之 COM 物件的方法。 這是因為基底類別方法的參數與引數會定義為 Visual Basic 6.0 中的 16 位元整數，但這些元素會公開為 16 位元整數型別的`Short`在新版的 Visual Basic 中。 新的函式接受 32 位元整數，而且會多載基底類別函式。  
  
 當使用 COM 物件，請確定您確認的大小和資料類型的參數。 例如，當您使用接受做為引數的 Visual Basic 6.0 集合物件的 COM 物件時，您無法提供較新版的 Visual Basic 中的集合。  
  
 屬性和方法繼承自 COM 類別會覆寫，這表示您可以宣告區域屬性或方法，以取代屬性或繼承自基底 COM 類別的方法。 覆寫繼承的 COM 內容的規則是類似的規則覆寫其他的屬性和方法，但有下列例外狀況：  
  
-   如果您覆寫任何屬性或繼承自 COM 類別的方法，您必須覆寫所有其他繼承的屬性和方法。  
  
-   使用屬性`ByRef`無法覆寫參數。  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)
