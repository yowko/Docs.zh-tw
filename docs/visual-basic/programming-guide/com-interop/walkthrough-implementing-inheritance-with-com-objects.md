---
title: "逐步解說︰ 實作 COM 物件 (Visual Basic) 的繼承 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inheritance, COM reusability
- base classes, COM reusability
- inheritance, walkthroughs
- derived classes, COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa7753847619f14600c924cba01e55651c4f17c2
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>逐步解說：實作 COM 物件的繼承 (Visual Basic)
您可以從 Visual Basic 類別來取得`Public`即使在舊版中建立的 COM 物件中的類別[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。 屬性和方法的類別繼承自 COM 物件可以覆寫或多載，就像屬性和任何其他基底類別的方法可以覆寫或多載。 從 COM 物件的繼承時，您有現有的類別程式庫不想重新編譯。  
  
 下列程序示範如何使用 Visual Basic 6.0 中建立的 COM 物件，包含類別，並以它做為基底類別。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>若要建立這個逐步解說中所使用的 COM 物件  
  
1.  在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。 專案，名為`Project1`建立。 它具有名為的類別`Class1`。  
  
2.  在**專案總管] 中**，以滑鼠右鍵按一下**Project1**，然後按一下 [ **Project1 屬性**。 **專案屬性**對話方塊隨即出現。  
  
3.  在**一般** 索引標籤的**專案屬性**對話方塊方塊中，輸入變更專案名稱`ComObject1`中**專案名稱**欄位。  
  
4.  在**專案總管] 中**，以滑鼠右鍵按一下`Class1`，然後按一下 [**屬性**。 **屬性**類別 視窗隨即出現。  
  
5.  變更`Name`屬性`MathFunctions`。  
  
6.  在**專案總管] 中**，以滑鼠右鍵按一下`MathFunctions`，然後按一下 [**檢視程式碼**。 **程式碼編輯器**隨即出現。  
  
7.  加入區域變數來存放屬性值︰  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  將屬性加入`Let`和屬性`Get`屬性程序︰  
  
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
  
9. 將函式︰  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 建立並註冊的 COM 物件，即可**讓 ComObject1.dll**上**檔案**功能表。  
  
    > [!NOTE]
    >  雖然您也可以公開類別，以建立[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]為 COM 物件，它不是真正的 COM 物件，並不能用在這個逐步解說。 如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="interop-assemblies"></a>Interop 組件  
 在下列程序中，您將建立 interop 組件，可做為 unmanaged 程式碼 （例如 COM 物件） 和 managed 程式碼之間的橋樑[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]使用。 Interop 組件，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建立控制代碼使用 COM 的詳細資料的許多物件，例如*interop 封送處理*，封裝參數和傳回值，對等資料的程序類型移動的 COM 物件。 在參考[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式指向 interop 組件，而不是實際的 COM 物件。  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>若要使用 Visual Basic 2005 和更新版本的 COM 物件  
  
1.  開啟新[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows 應用程式專案。  
  
2.  在**專案**] 功能表上，按一下 [**加入參考**。  
  
     **加入參考**對話方塊隨即出現。  
  
3.  在**COM**索引標籤上，按兩下`ComObject1`中**元件名稱**清單中，按一下**確定**。  
  
4.  在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。  
  
     **加入新項目**對話方塊隨即出現。  
  
5.  在**範本**] 窗格中，按一下 [**類別**。  
  
     預設檔案名稱， `Class1.vb`，會出現在**名稱**欄位。 變更此欄位，然後按一下 MathClass.vb**新增**。 這會建立名為的類別`MathClass`，並顯示其程式碼。  
  
6.  將下列程式碼加入至頂端`MathClass`從 COM 類別繼承。  
  
     [!code-vb[VbVbalrInterop #&31;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  加入下列程式碼來多載基底類別的公用方法`MathClass`:  
  
     [!code-vb[VbVbalrInterop #&32;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  加入下列程式碼來擴充繼承的類別`MathClass`:  
  
     [!code-vb[VbVbalrInterop #&33;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 新的類別會繼承基底類別中的 COM 物件的屬性、 多載方法，並定義新的方法來擴充類別。  
  
#### <a name="to-test-the-inherited-class"></a>若要測試繼承的類別  
  
1.  將按鈕加入至啟動表單，並按兩下來檢視其程式碼。  
  
2.  在按鈕的`Click`事件處理常式的程序，新增下列程式碼建立的執行個體`MathClass`呼叫多載的方法︰  
  
     [!code-vb[VbVbalrInterop #&34;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  按 F5 執行專案。  
  
 當您按一下表單上的按鈕`AddNumbers`與第一次呼叫方法`Short`資料類型的數字和[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]從基底類別選擇適當的方法。 第二次呼叫`AddNumbers`導向至多載方法，從`MathClass`。 第三個呼叫呼叫`SubtractNumbers`方法，延伸類別。 設定基底類別中的屬性，並會顯示的值。  
  
## <a name="next-steps"></a>後續步驟  
 您可能已經注意到，多載`AddNumbers`函式都會具有相同的資料類型繼承自基底類別的 COM 物件的方法。 這是因為引數和基底類別方法的參數會定義為 16 位元整數，在 Visual Basic 6.0 中，但它們會以 16 位元整數型別的`Short`在新版的 Visual Basic 中。 新的函式會接受 32 位元整數，而且會多載基底類別函式。  
  
 當使用 COM 物件，請務必確認參數的大小和資料類型。 例如，當您使用 Visual Basic 6.0 集合物件做為引數會接受 COM 物件時，無法提供更新版本的 Visual Basic 中的集合。  
  
 屬性和方法繼承自 COM 類別可以覆寫，這表示您可以宣告區域屬性或方法，以取代屬性或繼承自基底的 COM 類別的方法。 覆寫繼承的 COM 屬性的規則是類似的規則覆寫其他屬性和方法有下列例外︰  
  
-   如果您覆寫任何屬性或方法繼承自 COM 類別，您必須覆寫所有其他繼承的屬性和方法。  
  
-   使用屬性`ByRef`無法覆寫參數。  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)
