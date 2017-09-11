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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0e816d1728678467d930de524b894d175f9b0c0a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="24c53-102">逐步解說：實作 COM 物件的繼承 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24c53-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="24c53-103">您可以從 Visual Basic 類別來取得`Public`即使在舊版中建立的 COM 物件中的類別[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24c53-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="24c53-104">屬性和方法的類別繼承自 COM 物件可以覆寫或多載，就像屬性和任何其他基底類別的方法可以覆寫或多載。</span><span class="sxs-lookup"><span data-stu-id="24c53-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="24c53-105">從 COM 物件的繼承時，您有現有的類別程式庫不想重新編譯。</span><span class="sxs-lookup"><span data-stu-id="24c53-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="24c53-106">下列程序示範如何使用 Visual Basic 6.0 中建立的 COM 物件，包含類別，並以它做為基底類別。</span><span class="sxs-lookup"><span data-stu-id="24c53-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="24c53-107">若要建立這個逐步解說中所使用的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="24c53-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="24c53-108">在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。</span><span class="sxs-lookup"><span data-stu-id="24c53-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="24c53-109">專案，名為`Project1`建立。</span><span class="sxs-lookup"><span data-stu-id="24c53-109">A project named `Project1` is created.</span></span> <span data-ttu-id="24c53-110">它具有名為的類別`Class1`。</span><span class="sxs-lookup"><span data-stu-id="24c53-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="24c53-111">在**專案總管] 中**，以滑鼠右鍵按一下**Project1**，然後按一下 [ **Project1 屬性**。</span><span class="sxs-lookup"><span data-stu-id="24c53-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="24c53-112">**專案屬性**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="24c53-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="24c53-113">在**一般** 索引標籤的**專案屬性**對話方塊方塊中，輸入變更專案名稱`ComObject1`中**專案名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="24c53-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="24c53-114">在**專案總管] 中**，以滑鼠右鍵按一下`Class1`，然後按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="24c53-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="24c53-115">**屬性**類別 視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="24c53-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="24c53-116">變更`Name`屬性`MathFunctions`。</span><span class="sxs-lookup"><span data-stu-id="24c53-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="24c53-117">在**專案總管] 中**，以滑鼠右鍵按一下`MathFunctions`，然後按一下 [**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="24c53-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="24c53-118">**程式碼編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="24c53-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="24c53-119">加入區域變數來存放屬性值︰</span><span class="sxs-lookup"><span data-stu-id="24c53-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="24c53-120">將屬性加入`Let`和屬性`Get`屬性程序︰</span><span class="sxs-lookup"><span data-stu-id="24c53-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
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
  
9. <span data-ttu-id="24c53-121">將函式︰</span><span class="sxs-lookup"><span data-stu-id="24c53-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="24c53-122">建立並註冊的 COM 物件，即可**讓 ComObject1.dll**上**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="24c53-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="24c53-123">雖然您也可以公開類別，以建立[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]為 COM 物件，它不是真正的 COM 物件，並不能用在這個逐步解說。</span><span class="sxs-lookup"><span data-stu-id="24c53-123">Although you can also expose a class created with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="24c53-124">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="24c53-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="24c53-125">Interop 組件</span><span class="sxs-lookup"><span data-stu-id="24c53-125">Interop Assemblies</span></span>  
 <span data-ttu-id="24c53-126">在下列程序中，您將建立 interop 組件，可做為 unmanaged 程式碼 （例如 COM 物件） 和 managed 程式碼之間的橋樑[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="24c53-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] uses.</span></span> <span data-ttu-id="24c53-127">Interop 組件，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建立控制代碼使用 COM 的詳細資料的許多物件，例如*interop 封送處理*，封裝參數和傳回值，對等資料的程序類型移動的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="24c53-127">The interop assembly that [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="24c53-128">在參考[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式指向 interop 組件，而不是實際的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="24c53-128">The reference in the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="24c53-129">若要使用 Visual Basic 2005 和更新版本的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="24c53-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="24c53-130">開啟新[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="24c53-130">Open a new [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="24c53-131">在**專案**] 功能表上，按一下 [**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="24c53-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="24c53-132">**加入參考**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="24c53-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="24c53-133">在**COM**索引標籤上，按兩下`ComObject1`中**元件名稱**清單中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="24c53-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="24c53-134">在 [專案] **Walkthrough: Adding Controls to a Worksheet at Run Time in an VSTO Add-in project** 功能表中，按一下 [加入新項目] ****。</span><span class="sxs-lookup"><span data-stu-id="24c53-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="24c53-135">**加入新項目**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="24c53-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="24c53-136">在**範本**] 窗格中，按一下 [**類別**。</span><span class="sxs-lookup"><span data-stu-id="24c53-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="24c53-137">預設檔案名稱， `Class1.vb`，會出現在**名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="24c53-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="24c53-138">變更此欄位，然後按一下 MathClass.vb**新增**。</span><span class="sxs-lookup"><span data-stu-id="24c53-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="24c53-139">這會建立名為的類別`MathClass`，並顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="24c53-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="24c53-140">將下列程式碼加入至頂端`MathClass`從 COM 類別繼承。</span><span class="sxs-lookup"><span data-stu-id="24c53-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     <span data-ttu-id="24c53-141">[!code-vb[VbVbalrInterop #&31;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="24c53-141">[!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]</span></span>  
  
7.  <span data-ttu-id="24c53-142">加入下列程式碼來多載基底類別的公用方法`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="24c53-142">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="24c53-143">[!code-vb[VbVbalrInterop #&32;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="24c53-143">[!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]</span></span>  
  
8.  <span data-ttu-id="24c53-144">加入下列程式碼來擴充繼承的類別`MathClass`:</span><span class="sxs-lookup"><span data-stu-id="24c53-144">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     <span data-ttu-id="24c53-145">[!code-vb[VbVbalrInterop #&33;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="24c53-145">[!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]</span></span>  
  
 <span data-ttu-id="24c53-146">新的類別會繼承基底類別中的 COM 物件的屬性、 多載方法，並定義新的方法來擴充類別。</span><span class="sxs-lookup"><span data-stu-id="24c53-146">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="24c53-147">若要測試繼承的類別</span><span class="sxs-lookup"><span data-stu-id="24c53-147">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="24c53-148">將按鈕加入至啟動表單，並按兩下來檢視其程式碼。</span><span class="sxs-lookup"><span data-stu-id="24c53-148">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="24c53-149">在按鈕的`Click`事件處理常式的程序，新增下列程式碼建立的執行個體`MathClass`呼叫多載的方法︰</span><span class="sxs-lookup"><span data-stu-id="24c53-149">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     <span data-ttu-id="24c53-150">[!code-vb[VbVbalrInterop #&34;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="24c53-150">[!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]</span></span>  
  
3.  <span data-ttu-id="24c53-151">按 F5 執行專案。</span><span class="sxs-lookup"><span data-stu-id="24c53-151">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="24c53-152">當您按一下表單上的按鈕`AddNumbers`與第一次呼叫方法`Short`資料類型的數字和[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]從基底類別選擇適當的方法。</span><span class="sxs-lookup"><span data-stu-id="24c53-152">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chooses the appropriate method from the base class.</span></span> <span data-ttu-id="24c53-153">第二次呼叫`AddNumbers`導向至多載方法，從`MathClass`。</span><span class="sxs-lookup"><span data-stu-id="24c53-153">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="24c53-154">第三個呼叫呼叫`SubtractNumbers`方法，延伸類別。</span><span class="sxs-lookup"><span data-stu-id="24c53-154">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="24c53-155">設定基底類別中的屬性，並會顯示的值。</span><span class="sxs-lookup"><span data-stu-id="24c53-155">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="24c53-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="24c53-156">Next Steps</span></span>  
 <span data-ttu-id="24c53-157">您可能已經注意到，多載`AddNumbers`函式都會具有相同的資料類型繼承自基底類別的 COM 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="24c53-157">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="24c53-158">這是因為引數和基底類別方法的參數會定義為 16 位元整數，在 Visual Basic 6.0 中，但它們會以 16 位元整數型別的`Short`在新版的 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="24c53-158">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="24c53-159">新的函式會接受 32 位元整數，而且會多載基底類別函式。</span><span class="sxs-lookup"><span data-stu-id="24c53-159">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="24c53-160">當使用 COM 物件，請務必確認參數的大小和資料類型。</span><span class="sxs-lookup"><span data-stu-id="24c53-160">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="24c53-161">例如，當您使用 Visual Basic 6.0 集合物件做為引數會接受 COM 物件時，無法提供更新版本的 Visual Basic 中的集合。</span><span class="sxs-lookup"><span data-stu-id="24c53-161">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="24c53-162">屬性和方法繼承自 COM 類別可以覆寫，這表示您可以宣告區域屬性或方法，以取代屬性或繼承自基底的 COM 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="24c53-162">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="24c53-163">覆寫繼承的 COM 屬性的規則是類似的規則覆寫其他屬性和方法有下列例外︰</span><span class="sxs-lookup"><span data-stu-id="24c53-163">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="24c53-164">如果您覆寫任何屬性或方法繼承自 COM 類別，您必須覆寫所有其他繼承的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="24c53-164">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="24c53-165">使用屬性`ByRef`無法覆寫參數。</span><span class="sxs-lookup"><span data-stu-id="24c53-165">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c53-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24c53-166">See Also</span></span>  
 <span data-ttu-id="24c53-167">[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="24c53-167">[COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="24c53-168"> [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="24c53-168"> [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="24c53-169"> [Short 資料類型](../../../visual-basic/language-reference/data-types/short-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="24c53-169"> [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)</span></span>
