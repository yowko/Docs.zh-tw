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
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="d3a6c-102">逐步解說：使用 COM 物件（Visual Basic）來執行繼承</span><span class="sxs-lookup"><span data-stu-id="d3a6c-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="d3a6c-103">您可以從`Public` COM 物件中的類別衍生 Visual Basic 類別，即使在舊版的 Visual Basic 中建立的也一樣。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="d3a6c-104">繼承自 COM 物件之類別的屬性和方法可以覆寫或多載，就像任何其他基類的屬性和方法可以覆寫或多載一樣。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="d3a6c-105">當您有不想重新編譯的現有類別庫時，COM 物件的繼承就很有用。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="d3a6c-106">下列程式顯示如何使用 Visual Basic 6.0 來建立包含類別的 COM 物件，然後將它當做基類使用。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="d3a6c-107">若要建立本逐步解說中使用的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d3a6c-107">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="d3a6c-108">在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="d3a6c-109">隨即建立名`Project1`為的專案。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-109">A project named `Project1` is created.</span></span> <span data-ttu-id="d3a6c-110">它具有名為`Class1`的類別。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-110">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="d3a6c-111">在 [**專案管理器**] 中，以滑鼠右鍵按一下 [ **Project1**]，然後按一下 [ **Project1 屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="d3a6c-112">[**專案屬性**] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-112">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="d3a6c-113">在 [**專案屬性**] 對話方塊的 [**一般**] 索引標籤上，于 [ `ComObject1` **專案名稱**] 欄位中輸入來變更專案名稱。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="d3a6c-114">在**Project Explorer**中，以滑鼠右鍵`Class1`按一下 []，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="d3a6c-115">類別的 [**屬性**] 視窗隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-115">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="d3a6c-116">將屬性變更為`MathFunctions`。 `Name`</span><span class="sxs-lookup"><span data-stu-id="d3a6c-116">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="d3a6c-117">在 [**專案管理器**] 中， `MathFunctions`以滑鼠右鍵按一下，然後按一下 [**查看程式碼**]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="d3a6c-118">隨即顯示 [程式**代碼編輯器**]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-118">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="d3a6c-119">新增本機變數以保存屬性值：</span><span class="sxs-lookup"><span data-stu-id="d3a6c-119">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="d3a6c-120">新增屬性`Let`和屬性`Get`程式：</span><span class="sxs-lookup"><span data-stu-id="d3a6c-120">Add Property `Let` and Property `Get` property procedures:</span></span>

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

9. <span data-ttu-id="d3a6c-121">新增函式：</span><span class="sxs-lookup"><span data-stu-id="d3a6c-121">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="d3a6c-122">按一下 [檔案] 功能表上的 [**建立 ComObject1** **]，以**建立並註冊 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d3a6c-123">雖然您也可以將使用 Visual Basic 建立的類別公開為 COM 物件，但它並不是真正的 COM 物件，而且無法在此逐步解說中使用。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="d3a6c-124">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="d3a6c-125">Interop 元件</span><span class="sxs-lookup"><span data-stu-id="d3a6c-125">Interop Assemblies</span></span>

<span data-ttu-id="d3a6c-126">在下列程式中，您將建立 interop 元件，做為非受控程式碼（例如 COM 物件）與 managed 程式碼（Visual Studio 使用）之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="d3a6c-127">Visual Basic 建立的 interop 元件會處理許多使用 COM 物件的詳細資料，例如*interop 封送處理*、封裝參數的過程，以及將值傳回至 com 物件的相等資料類型。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="d3a6c-128">Visual Basic 應用程式中的參考會指向 interop 元件，而不是實際的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="d3a6c-129">使用具有 Visual Basic 2005 和更新版本的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d3a6c-129">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="d3a6c-130">開啟新的 Visual Basic Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-130">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="d3a6c-131">在 [專案] 功能表上，按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-131">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="d3a6c-132">[新增參考] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-132">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="d3a6c-133">在 [ **COM** ] 索引標籤上`ComObject1` ，按兩下 [**元件名稱**] 清單，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="d3a6c-134">在 [專案] 功能表中，按一下 [加入新項目]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-134">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="d3a6c-135">隨即顯示 [ 新增項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-135">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="d3a6c-136">在 [**範本**] 窗格中，按一下 [**類別**]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-136">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="d3a6c-137">預設檔案名`Class1.vb`會出現在 [**名稱**] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="d3a6c-138">將此欄位變更為 MathClass，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="d3a6c-139">這會建立名為`MathClass`的類別，並顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-139">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="d3a6c-140">將下列程式碼加入`MathClass`至的頂端，以繼承自 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="d3a6c-141">藉由將下列程式碼新增至，來`MathClass`多載基類的公用方法：</span><span class="sxs-lookup"><span data-stu-id="d3a6c-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="d3a6c-142">將下列程式碼新增至，以`MathClass`擴充繼承的類別：</span><span class="sxs-lookup"><span data-stu-id="d3a6c-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="d3a6c-143">新的類別會繼承 COM 物件中基類的屬性、多載方法，並定義新的方法來擴充類別。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

### <a name="to-test-the-inherited-class"></a><span data-ttu-id="d3a6c-144">測試繼承的類別</span><span class="sxs-lookup"><span data-stu-id="d3a6c-144">To test the inherited class</span></span>

1. <span data-ttu-id="d3a6c-145">將按鈕新增至您的啟動表單，然後按兩下它以查看其程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-145">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="d3a6c-146">在按鈕的`Click`事件處理常式中，加入下列程式碼來建立的`MathClass`實例，並呼叫多載的方法：</span><span class="sxs-lookup"><span data-stu-id="d3a6c-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="d3a6c-147">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-147">Run the project by pressing F5.</span></span>

<span data-ttu-id="d3a6c-148">當您按一下表單上的按鈕時， `AddNumbers`會先使用`Short`資料類型數位來呼叫方法，然後 Visual Basic 從基類選擇適當的方法。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="d3a6c-149">第二個呼叫`AddNumbers`會從`MathClass`導向至的多載方法。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="d3a6c-150">第三個呼叫會`SubtractNumbers`呼叫方法，這會擴充類別。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="d3a6c-151">已設定基類中的屬性，並顯示值。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-151">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d3a6c-152">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d3a6c-152">Next Steps</span></span>

<span data-ttu-id="d3a6c-153">您可能已經注意到， `AddNumbers`多載函式的資料類型與繼承自 COM 物件基類的方法相同。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="d3a6c-154">這是因為在 Visual Basic 6.0 中，基類方法的引數和參數會定義為16位整數，但是在較新版本的 Visual Basic 中，它們會公開`Short`為類型的16位整數。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="d3a6c-155">新的函式會接受32位整數，並多載基類函數。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="d3a6c-156">使用 COM 物件時，請務必確認參數的大小和資料類型。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="d3a6c-157">例如，當您使用接受 Visual Basic 6.0 集合物件做為引數的 COM 物件時，您無法從較新版本的 Visual Basic 提供集合。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="d3a6c-158">繼承自 COM 類別的屬性和方法可以覆寫，這表示您可以宣告本機屬性或方法，以取代繼承自基底 COM 類別的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="d3a6c-159">覆寫繼承 COM 屬性的規則類似于覆寫其他屬性和方法的規則，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d3a6c-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="d3a6c-160">如果您覆寫繼承自 COM 類別的任何屬性或方法，您必須覆寫所有其他繼承的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="d3a6c-161">無法覆寫`ByRef`使用參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3a6c-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3a6c-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3a6c-162">See also</span></span>

- [<span data-ttu-id="d3a6c-163">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="d3a6c-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="d3a6c-164">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="d3a6c-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="d3a6c-165">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="d3a6c-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
