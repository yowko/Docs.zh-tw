---
title: 逐步解說：使用 COM 物件（Visual Basic）來執行繼承
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 7cbf71d7a2bbd1e94864e785894fdea41d522486
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053339"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>逐步解說：使用 COM 物件（Visual Basic）來執行繼承

您可以從`Public` COM 物件中的類別衍生 Visual Basic 類別，即使在舊版的 Visual Basic 中建立的也一樣。 繼承自 COM 物件之類別的屬性和方法可以覆寫或多載，就像任何其他基類的屬性和方法可以覆寫或多載一樣。 當您有不想重新編譯的現有類別庫時，COM 物件的繼承就很有用。

下列程式顯示如何使用 Visual Basic 6.0 來建立包含類別的 COM 物件，然後將它當做基類使用。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>若要建立本逐步解說中使用的 COM 物件

1. 在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。 隨即建立名`Project1`為的專案。 它具有名為`Class1`的類別。

2. 在 [**專案管理器**] 中，以滑鼠右鍵按一下 [ **Project1**]，然後按一下 [ **Project1 屬性**]。 [**專案屬性**] 對話方塊隨即顯示。

3. 在 [**專案屬性**] 對話方塊的 [**一般**] 索引標籤上，于 [ `ComObject1` **專案名稱**] 欄位中輸入來變更專案名稱。

4. 在**Project Explorer**中，以滑鼠右鍵`Class1`按一下 []，然後按一下 [**屬性**]。 類別的 [**屬性**] 視窗隨即顯示。

5. 將屬性變更為`MathFunctions`。 `Name`

6. 在 [**專案管理器**] 中， `MathFunctions`以滑鼠右鍵按一下，然後按一下 [**查看程式碼**]。 隨即顯示 [程式**代碼編輯器**]。

7. 新增本機變數以保存屬性值：

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. 新增屬性`Let`和屬性`Get`程式：

    ```vb
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

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. 按一下 [檔案] 功能表上的 [**建立 ComObject1** **]，以**建立並註冊 COM 物件。

    > [!NOTE]
    > 雖然您也可以將使用 Visual Basic 建立的類別公開為 COM 物件，但它並不是真正的 COM 物件，而且無法在此逐步解說中使用。 如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。

## <a name="interop-assemblies"></a>Interop 元件

在下列程式中，您將建立 interop 元件，做為非受控程式碼（例如 COM 物件）與 managed 程式碼（Visual Studio 使用）之間的橋樑。 Visual Basic 建立的 interop 元件會處理許多使用 COM 物件的詳細資料，例如*interop 封送處理*、封裝參數的過程，以及將值傳回至 com 物件的相等資料類型。 Visual Basic 應用程式中的參考會指向 interop 元件，而不是實際的 COM 物件。

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>使用具有 Visual Basic 2005 和更新版本的 COM 物件

1. 開啟新的 Visual Basic Windows 應用程式專案。

2. 在 [專案] 功能表上，按一下 [新增參考]。

     [新增參考] 對話方塊隨即顯示。

3. 在 [ **COM** ] 索引標籤上`ComObject1` ，按兩下 [**元件名稱**] 清單，然後按一下 **[確定]** 。

4. 在 [專案] 功能表中，按一下 [加入新項目]。

     隨即顯示 [ 新增項目] 對話方塊。

5. 在 [**範本**] 窗格中，按一下 [**類別**]。

     預設檔案名`Class1.vb`會出現在 [**名稱**] 欄位中。 將此欄位變更為 MathClass，然後按一下 [**新增**]。 這會建立名為`MathClass`的類別，並顯示其程式碼。

6. 將下列程式碼加入`MathClass`至的頂端，以繼承自 COM 類別。

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. 藉由將下列程式碼新增至，來`MathClass`多載基類的公用方法：

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. 將下列程式碼新增至，以`MathClass`擴充繼承的類別：

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

新的類別會繼承 COM 物件中基類的屬性、多載方法，並定義新的方法來擴充類別。

### <a name="to-test-the-inherited-class"></a>測試繼承的類別

1. 將按鈕新增至您的啟動表單，然後按兩下它以查看其程式碼。

2. 在按鈕的`Click`事件處理常式中，加入下列程式碼來建立的`MathClass`實例，並呼叫多載的方法：

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. 按 F5 執行專案。

當您按一下表單上的按鈕時， `AddNumbers`會先使用`Short`資料類型數位來呼叫方法，然後 Visual Basic 從基類選擇適當的方法。 第二個呼叫`AddNumbers`會從`MathClass`導向至的多載方法。 第三個呼叫會`SubtractNumbers`呼叫方法，這會擴充類別。 已設定基類中的屬性，並顯示值。

## <a name="next-steps"></a>後續步驟

您可能已經注意到， `AddNumbers`多載函式的資料類型與繼承自 COM 物件基類的方法相同。 這是因為在 Visual Basic 6.0 中，基類方法的引數和參數會定義為16位整數，但是在較新版本的 Visual Basic 中，它們會公開`Short`為類型的16位整數。 新的函式會接受32位整數，並多載基類函數。

使用 COM 物件時，請務必確認參數的大小和資料類型。 例如，當您使用接受 Visual Basic 6.0 集合物件做為引數的 COM 物件時，您無法從較新版本的 Visual Basic 提供集合。

繼承自 COM 類別的屬性和方法可以覆寫，這表示您可以宣告本機屬性或方法，以取代繼承自基底 COM 類別的屬性或方法。 覆寫繼承 COM 屬性的規則類似于覆寫其他屬性和方法的規則，但有下列例外狀況：

- 如果您覆寫繼承自 COM 類別的任何屬性或方法，您必須覆寫所有其他繼承的屬性和方法。

- 無法覆寫`ByRef`使用參數的屬性。

## <a name="see-also"></a>另請參閱

- [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)
