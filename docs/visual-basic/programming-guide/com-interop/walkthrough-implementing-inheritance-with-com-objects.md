---
title: 逐步解說：實作 COM 物件的繼承 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: a1c1b7c247d3277c6614a4774395650c4c069c2f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929994"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="ee397-102">逐步解說：實作 COM 物件的繼承 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee397-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="ee397-103">您可以衍生從 Visual Basic 類別`Public`中 COM 物件，即使在舊版的 Visual Basic 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="ee397-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="ee397-104">屬性和方法，從 COM 物件繼承的類別可以覆寫或多載，就如同屬性和任何其他基底類別的方法可以覆寫或多載。</span><span class="sxs-lookup"><span data-stu-id="ee397-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="ee397-105">當您有現有的類別程式庫，您不希望重新編譯時，適合使用 COM 物件的繼承。</span><span class="sxs-lookup"><span data-stu-id="ee397-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="ee397-106">下列程序示範如何使用 Visual Basic 6.0 中建立 COM 物件，包含類別，並將它作為基底類別。</span><span class="sxs-lookup"><span data-stu-id="ee397-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="ee397-107">若要建立本逐步解說中使用的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="ee397-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="ee397-108">在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。</span><span class="sxs-lookup"><span data-stu-id="ee397-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="ee397-109">專案，命名為`Project1`建立。</span><span class="sxs-lookup"><span data-stu-id="ee397-109">A project named `Project1` is created.</span></span> <span data-ttu-id="ee397-110">它有一個名為類別`Class1`。</span><span class="sxs-lookup"><span data-stu-id="ee397-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="ee397-111">在**專案總管**，以滑鼠右鍵按一下**Project1**，然後按一下**Project1 屬性**。</span><span class="sxs-lookup"><span data-stu-id="ee397-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="ee397-112">**專案屬性**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ee397-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="ee397-113">在上**一般**索引標籤**專案屬性**對話方塊方塊中，輸入變更專案名稱`ComObject1`中**專案名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="ee397-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="ee397-114">在**專案總管**，以滑鼠右鍵按一下`Class1`，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ee397-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="ee397-115">**屬性**類別 視窗隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="ee397-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="ee397-116">變更`Name`屬性設`MathFunctions`。</span><span class="sxs-lookup"><span data-stu-id="ee397-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="ee397-117">在**專案總管**，以滑鼠右鍵按一下`MathFunctions`，然後按一下**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="ee397-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="ee397-118">**程式碼編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="ee397-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="ee397-119">新增本機變數來保存屬性值：</span><span class="sxs-lookup"><span data-stu-id="ee397-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="ee397-120">將屬性加入`Let`和屬性`Get`屬性程序：</span><span class="sxs-lookup"><span data-stu-id="ee397-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
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
  
9. <span data-ttu-id="ee397-121">新增函式：</span><span class="sxs-lookup"><span data-stu-id="ee397-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="ee397-122">建立並登錄的 COM 物件，依序按一下**讓 ComObject1.dll**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="ee397-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee397-123">雖然您也可以公開使用的 COM 物件的 Visual Basic 建立的類別，它不是真正的 COM 物件，並不能在此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="ee397-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="ee397-124">如需詳細資訊，請參閱 < [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="ee397-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="ee397-125">Interop 組件</span><span class="sxs-lookup"><span data-stu-id="ee397-125">Interop Assemblies</span></span>  
 <span data-ttu-id="ee397-126">在下列程序中，您將建立 interop 組件，做為 unmanaged 程式碼 （例如 COM 物件） 與 Visual Studio 會使用 managed 程式碼之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="ee397-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="ee397-127">Visual Basic 建立 interop 組件會處理許多這類使用 COM 物件的詳細資料*interop 封送處理*，封裝參數和傳回值，對等資料的程序類型，因為它們將移至和從 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="ee397-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="ee397-128">Visual Basic 應用程式中的參考會指向 interop 組件，而不是實際的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="ee397-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="ee397-129">若要使用 Visual Basic 2005 和更新版本中的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="ee397-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="ee397-130">開啟新的 Visual Basic Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="ee397-130">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="ee397-131">在 [專案] 功能表上，按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="ee397-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="ee397-132">[新增參考] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="ee397-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="ee397-133">在上**COM**索引標籤上，按兩下`ComObject1`中**元件名稱**清單，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ee397-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="ee397-134">在 [專案]  功能表中，按一下 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="ee397-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="ee397-135">隨即顯示 [ 新增項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ee397-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="ee397-136">在 **範本**窗格中，按一下**類別**。</span><span class="sxs-lookup"><span data-stu-id="ee397-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="ee397-137">預設檔案名稱， `Class1.vb`，會出現在**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="ee397-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="ee397-138">將此欄位變更為 MathClass.vb，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="ee397-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="ee397-139">這會建立名為類別`MathClass`，並顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="ee397-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="ee397-140">將下列程式碼加入至頂端`MathClass`從 COM 類別繼承。</span><span class="sxs-lookup"><span data-stu-id="ee397-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="ee397-141">多載基底類別的公用方法，藉由新增下列程式碼`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="ee397-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="ee397-142">新增下列程式碼來擴充繼承的類別`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="ee397-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="ee397-143">新的類別會繼承基底類別中的 COM 物件的屬性、 多載方法，並定義新方法來擴充類別。</span><span class="sxs-lookup"><span data-stu-id="ee397-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="ee397-144">若要測試繼承的類別</span><span class="sxs-lookup"><span data-stu-id="ee397-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="ee397-145">將按鈕加入您的啟動表單，然後按兩下以檢視其程式碼。</span><span class="sxs-lookup"><span data-stu-id="ee397-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="ee397-146">在按鈕的`Click`事件處理常式的程序，新增下列程式碼，建立的執行個體`MathClass`呼叫多載的方法：</span><span class="sxs-lookup"><span data-stu-id="ee397-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="ee397-147">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="ee397-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="ee397-148">當您按一下表單上的按鈕`AddNumbers`與第一次呼叫方法`Short`資料類型的數字和 Visual Basic 會選擇適當的方法基底類別。</span><span class="sxs-lookup"><span data-stu-id="ee397-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="ee397-149">第二次呼叫`AddNumbers`會導向至多載方法，從`MathClass`。</span><span class="sxs-lookup"><span data-stu-id="ee397-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="ee397-150">第三個呼叫呼叫`SubtractNumbers`擴充類別的方法。</span><span class="sxs-lookup"><span data-stu-id="ee397-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="ee397-151">設定基底類別中的屬性，並在顯示的值。</span><span class="sxs-lookup"><span data-stu-id="ee397-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ee397-152">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ee397-152">Next Steps</span></span>  
 <span data-ttu-id="ee397-153">您可能已經注意到，多載`AddNumbers`函式似乎有相同的資料類型從 COM 物件的基底類別繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="ee397-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="ee397-154">這是因為引數和基底類別方法的參數會定義為 Visual Basic 6.0 中的 16 位元整數，但它們會公開為 16 位元整數類型的`Short`在新版的 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="ee397-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="ee397-155">新的函式會接受 32 位元整數，並多載基底類別函式。</span><span class="sxs-lookup"><span data-stu-id="ee397-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="ee397-156">使用 COM 物件，請確定您已驗證的大小和資料類型的參數。</span><span class="sxs-lookup"><span data-stu-id="ee397-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="ee397-157">例如，當您使用接受做為引數的 Visual Basic 6.0 集合物件的 COM 物件時，您就無法提供更新版本的 Visual Basic 中的集合。</span><span class="sxs-lookup"><span data-stu-id="ee397-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="ee397-158">屬性和方法繼承自 COM 類別可以覆寫，這表示您可以宣告區域屬性或方法，以取代屬性或繼承自基底的 COM 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="ee397-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="ee397-159">覆寫其他的屬性和方法，但有下列例外狀況的規則覆寫繼承的 COM 屬性的規則如下：</span><span class="sxs-lookup"><span data-stu-id="ee397-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="ee397-160">如果您覆寫任何屬性或繼承自 COM 類別的方法，您必須覆寫所有其他繼承的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="ee397-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="ee397-161">使用屬性`ByRef`無法覆寫參數。</span><span class="sxs-lookup"><span data-stu-id="ee397-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee397-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee397-162">See Also</span></span>  
 [<span data-ttu-id="ee397-163">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="ee397-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="ee397-164">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="ee397-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="ee397-165">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="ee397-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
