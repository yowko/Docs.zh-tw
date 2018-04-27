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
ms.openlocfilehash: 10c6bdf46e351b23705107da3b693531718cfd37
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="fe02a-102">逐步解說：實作 COM 物件的繼承 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe02a-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="fe02a-103">您可以取得 Visual Basic 類別從`Public`中 COM 物件，即使這些舊版本的 Visual Basic 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="fe02a-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="fe02a-104">屬性和類別繼承自 COM 物件的方法可以覆寫或多載一樣屬性和任何其他基底類別的方法可以覆寫或多載。</span><span class="sxs-lookup"><span data-stu-id="fe02a-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="fe02a-105">從 COM 物件的繼承時，您有現有的類別程式庫，您不希望重新編譯。</span><span class="sxs-lookup"><span data-stu-id="fe02a-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="fe02a-106">下列程序示範如何使用 Visual Basic 6.0 中建立的 COM 物件，包含類別，並以它做為基底類別。</span><span class="sxs-lookup"><span data-stu-id="fe02a-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="fe02a-107">若要建立這個逐步解說中所使用的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="fe02a-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="fe02a-108">在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。</span><span class="sxs-lookup"><span data-stu-id="fe02a-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="fe02a-109">專案，名為`Project1`建立。</span><span class="sxs-lookup"><span data-stu-id="fe02a-109">A project named `Project1` is created.</span></span> <span data-ttu-id="fe02a-110">它具有名為類別`Class1`。</span><span class="sxs-lookup"><span data-stu-id="fe02a-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="fe02a-111">在**專案總管**，以滑鼠右鍵按一下**Project1**，然後按一下  **Project1 屬性**。</span><span class="sxs-lookup"><span data-stu-id="fe02a-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="fe02a-112">**專案屬性**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fe02a-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="fe02a-113">在**一般** 索引標籤**專案屬性**對話方塊方塊中，輸入新的專案名稱`ComObject1`中**專案名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="fe02a-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="fe02a-114">在**專案總管**，以滑鼠右鍵按一下`Class1`，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="fe02a-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="fe02a-115">**屬性**類別 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fe02a-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="fe02a-116">變更`Name`屬性`MathFunctions`。</span><span class="sxs-lookup"><span data-stu-id="fe02a-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="fe02a-117">在**Project Explorer**，以滑鼠右鍵按一下`MathFunctions`，然後按一下 **檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="fe02a-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="fe02a-118">**程式碼編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="fe02a-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="fe02a-119">加入本機變數來保存屬性值：</span><span class="sxs-lookup"><span data-stu-id="fe02a-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="fe02a-120">將屬性加入`Let`和屬性`Get`屬性程序：</span><span class="sxs-lookup"><span data-stu-id="fe02a-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
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
  
9. <span data-ttu-id="fe02a-121">加入函式：</span><span class="sxs-lookup"><span data-stu-id="fe02a-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="fe02a-122">建立並註冊的 COM 物件，依序按一下**進行 ComObject1.dll**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="fe02a-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fe02a-123">雖然您也可以公開使用 Visual Basic 為 COM 物件建立的類別，它不是真正的 COM 物件，並不能用在這個逐步解說。</span><span class="sxs-lookup"><span data-stu-id="fe02a-123">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="fe02a-124">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="fe02a-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="fe02a-125">Interop 組件</span><span class="sxs-lookup"><span data-stu-id="fe02a-125">Interop Assemblies</span></span>  
 <span data-ttu-id="fe02a-126">在下列程序中，您將建立 interop 組件，可做為 （例如 COM 物件） 的 unmanaged 程式碼與 managed 程式碼之間的橋樑[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="fe02a-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] uses.</span></span> <span data-ttu-id="fe02a-127">Visual Basic 建立的 interop 組件會處理許多細節，例如使用 COM 物件的*interop 封送處理*，封裝參數和傳回值為對等資料的程序類型，因為它們將移到和從 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="fe02a-127">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="fe02a-128">在 Visual Basic 應用程式中的參考指向的 interop 組件不是實際的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="fe02a-128">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="fe02a-129">使用 COM 物件來與 Visual Basic 2005 和更新版本</span><span class="sxs-lookup"><span data-stu-id="fe02a-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="fe02a-130">開啟新的 Visual Basic Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="fe02a-130">Open a new Visual Basic Windows Application project.</span></span>  
  
2.  <span data-ttu-id="fe02a-131">在 [專案] 功能表上，按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="fe02a-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="fe02a-132">[新增參考] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="fe02a-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="fe02a-133">在**COM**索引標籤上，按兩下`ComObject1`中**元件名稱**清單，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fe02a-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="fe02a-134">在 [專案]  功能表中，按一下 [加入新項目] 。</span><span class="sxs-lookup"><span data-stu-id="fe02a-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="fe02a-135">隨即顯示 [ 新增項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="fe02a-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="fe02a-136">在**範本**] 窗格中，按一下 [**類別**。</span><span class="sxs-lookup"><span data-stu-id="fe02a-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="fe02a-137">預設檔案名稱， `Class1.vb`，會出現在**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="fe02a-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="fe02a-138">此欄位變更為 MathClass.vb，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="fe02a-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="fe02a-139">這會建立名為類別`MathClass`，並顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe02a-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="fe02a-140">將下列程式碼加入至頂端`MathClass`繼承自 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="fe02a-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="fe02a-141">多載基底類別的公用方法加入下列程式碼以`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="fe02a-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="fe02a-142">加入下列程式碼來擴充繼承的類別`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="fe02a-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="fe02a-143">新類別會繼承基底類別中的 COM 物件的屬性、 多載方法，並定義新的方法來擴充類別。</span><span class="sxs-lookup"><span data-stu-id="fe02a-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="fe02a-144">若要測試繼承的類別</span><span class="sxs-lookup"><span data-stu-id="fe02a-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="fe02a-145">啟動表單，加入按鈕，然後按兩下以檢視其程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe02a-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="fe02a-146">在按鈕的`Click`事件處理常式的程序，加入下列程式碼建立的執行個體`MathClass`呼叫多載的方法：</span><span class="sxs-lookup"><span data-stu-id="fe02a-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="fe02a-147">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="fe02a-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="fe02a-148">當您按一下表單上的按鈕`AddNumbers`與第一次呼叫方法`Short`資料類型的數字，Visual Basic 中的基底類別選擇適當方法。</span><span class="sxs-lookup"><span data-stu-id="fe02a-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="fe02a-149">第二個呼叫`AddNumbers`導向至多載方法，從`MathClass`。</span><span class="sxs-lookup"><span data-stu-id="fe02a-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="fe02a-150">第三個呼叫呼叫`SubtractNumbers`方法，延伸的類別。</span><span class="sxs-lookup"><span data-stu-id="fe02a-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="fe02a-151">基底類別中的屬性已設定，而且將會顯示值。</span><span class="sxs-lookup"><span data-stu-id="fe02a-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fe02a-152">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fe02a-152">Next Steps</span></span>  
 <span data-ttu-id="fe02a-153">您可能已注意到，多載`AddNumbers`函式看似具有相同的資料類型繼承自基底類別之 COM 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="fe02a-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="fe02a-154">這是因為基底類別方法的參數與引數會定義為 Visual Basic 6.0 中的 16 位元整數，但這些元素會公開為 16 位元整數型別的`Short`在新版的 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="fe02a-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="fe02a-155">新的函式接受 32 位元整數，而且會多載基底類別函式。</span><span class="sxs-lookup"><span data-stu-id="fe02a-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="fe02a-156">當使用 COM 物件，請確定您確認的大小和資料類型的參數。</span><span class="sxs-lookup"><span data-stu-id="fe02a-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="fe02a-157">例如，當您使用接受做為引數的 Visual Basic 6.0 集合物件的 COM 物件時，您無法提供較新版的 Visual Basic 中的集合。</span><span class="sxs-lookup"><span data-stu-id="fe02a-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="fe02a-158">屬性和方法繼承自 COM 類別會覆寫，這表示您可以宣告區域屬性或方法，以取代屬性或繼承自基底 COM 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="fe02a-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="fe02a-159">覆寫繼承的 COM 內容的規則是類似的規則覆寫其他的屬性和方法，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="fe02a-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="fe02a-160">如果您覆寫任何屬性或繼承自 COM 類別的方法，您必須覆寫所有其他繼承的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="fe02a-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="fe02a-161">使用屬性`ByRef`無法覆寫參數。</span><span class="sxs-lookup"><span data-stu-id="fe02a-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe02a-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe02a-162">See Also</span></span>  
 [<span data-ttu-id="fe02a-163">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="fe02a-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="fe02a-164">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="fe02a-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="fe02a-165">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="fe02a-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
