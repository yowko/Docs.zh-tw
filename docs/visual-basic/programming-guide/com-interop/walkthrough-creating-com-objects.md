---
title: 逐步解說：使用 Visual Basic 建立 COM 物件
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 97e917d568b31860979e54598350d1ae7a6fdb25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331893"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="cdb75-102">逐步解說：使用 Visual Basic 建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="cdb75-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="cdb75-103">建立新的應用程式或元件時，最好是建立.NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="cdb75-104">不過，Visual Basic 也容易公開給 COM 的.NET Framework 元件</span><span class="sxs-lookup"><span data-stu-id="cdb75-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="cdb75-105">這可讓您針對需要 COM 元件的舊版應用程式套件中提供新元件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="cdb75-106">本逐步解說示範如何使用 Visual Basic 來公開 （expose）[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]為 COM 物件，使用和不使用 COM 類別範本的物件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-106">This walkthrough demonstrates how to use Visual Basic to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="cdb75-107">COM 物件公開 （expose） 的最簡單方式是使用 COM 類別範本。</span><span class="sxs-lookup"><span data-stu-id="cdb75-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="cdb75-108">使用 COM 類別範本會建立新的類別，並設定專案以產生類別和互通性層級為 COM 物件，並向作業系統註冊。</span><span class="sxs-lookup"><span data-stu-id="cdb75-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdb75-109">雖然您也可以公開為 COM 物件使用的 unmanaged 程式碼建立 Visual Basic 中的類別，它不是真正的 COM 物件，並無法供 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="cdb75-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="cdb75-110">如需詳細資訊，請參閱 < [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb75-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="cdb75-111">若要使用 COM 類別範本建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="cdb75-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="cdb75-112">開啟新的 Windows 應用程式專案，從**檔案**功能表中的按一下**新的專案**。</span><span class="sxs-lookup"><span data-stu-id="cdb75-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="cdb75-113">在 **新的專案**下方的對話方塊中**專案類型**欄位中，確認已選取 Windows。</span><span class="sxs-lookup"><span data-stu-id="cdb75-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="cdb75-114">選取 **類別庫**從**範本**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="cdb75-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="cdb75-115">新的專案會顯示。</span><span class="sxs-lookup"><span data-stu-id="cdb75-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="cdb75-116">選取 **加入新項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="cdb75-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="cdb75-117">隨即顯示 [ 新增項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cdb75-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="cdb75-118">選取  **COM 類別**從**範本**清單，然後再按**新增**。</span><span class="sxs-lookup"><span data-stu-id="cdb75-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="cdb75-119">Visual Basic 會加入新的類別，並設定新的專案，COM interop。</span><span class="sxs-lookup"><span data-stu-id="cdb75-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="cdb75-120">加入 COM 類別中的程式碼，例如屬性、 方法和事件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="cdb75-121">選取 **建置 ClassLibrary1**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="cdb75-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="cdb75-122">Visual Basic 建置的組件，並向作業系統註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="cdb75-123">建立 COM 物件，不使用 COM 類別範本</span><span class="sxs-lookup"><span data-stu-id="cdb75-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="cdb75-124">您也可以建立以手動方式而不是使用 COM 類別範本的 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="cdb75-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="cdb75-125">當您正在從命令列或您想要更充分掌控如何定義 COM 物件，此程序是很有幫助。</span><span class="sxs-lookup"><span data-stu-id="cdb75-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="cdb75-126">若要設定您的專案，以產生 COM 物件</span><span class="sxs-lookup"><span data-stu-id="cdb75-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="cdb75-127">開啟新的 Windows 應用程式專案，從**檔案**功能表中的按一下**NewProject**。</span><span class="sxs-lookup"><span data-stu-id="cdb75-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="cdb75-128">在 **新的專案**下方的對話方塊中**專案類型**欄位中，確認已選取 Windows。</span><span class="sxs-lookup"><span data-stu-id="cdb75-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="cdb75-129">選取 **類別庫**從**範本**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="cdb75-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="cdb75-130">新的專案會顯示。</span><span class="sxs-lookup"><span data-stu-id="cdb75-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="cdb75-131">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="cdb75-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="cdb75-132">**專案設計工具**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="cdb75-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="cdb75-133">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="cdb75-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="cdb75-134">選取 **註冊 COM Interop**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="cdb75-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="cdb75-135">若要設定您的類別中的程式碼，來建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="cdb75-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="cdb75-136">在 **方案總管**，按兩下**Class1.vb**以顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="cdb75-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="cdb75-137">將類別重新命名為 `ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="cdb75-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="cdb75-138">下列將常數新增到`ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="cdb75-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="cdb75-139">它們會儲存 COM 物件時需要有全域唯一識別碼 (GUID) 常數。</span><span class="sxs-lookup"><span data-stu-id="cdb75-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="cdb75-140">在 [工具] 功能表上，按一下 [建立 GUID]。</span><span class="sxs-lookup"><span data-stu-id="cdb75-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="cdb75-141">在 [建立 GUID] 對話方塊中，依序按一下 [登錄格式] 和 [複製]。</span><span class="sxs-lookup"><span data-stu-id="cdb75-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="cdb75-142">按一下 [結束] 。</span><span class="sxs-lookup"><span data-stu-id="cdb75-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="cdb75-143">取代為空字串`ClassId`guid，移除前置和尾端括號。</span><span class="sxs-lookup"><span data-stu-id="cdb75-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="cdb75-144">例如，如果 Guidgen 所提供的 GUID 是`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`則您的程式碼應該會出現，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cdb75-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="cdb75-145">重複上一個步驟`InterfaceId`和`EventsId`常數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cdb75-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  <span data-ttu-id="cdb75-146">請確定 Guid 的新的且唯一的;否則，您的 COM 元件可能發生衝突，與其他 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="cdb75-147">新增`ComClass`屬性設定為`ComClass1`，指定類別識別碼、 介面 ID 和事件識別碼的 Guid，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="cdb75-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="cdb75-148">COM 類別必須具有無參數`Public Sub New()`建構函式或類別不會註冊正確。</span><span class="sxs-lookup"><span data-stu-id="cdb75-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="cdb75-149">加入類別中的無參數建構函式：</span><span class="sxs-lookup"><span data-stu-id="cdb75-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="cdb75-150">將屬性、 方法和事件新增至類別，並結束它與`End Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="cdb75-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="cdb75-151">選取 **建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="cdb75-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="cdb75-152">Visual Basic 建置的組件，並向作業系統註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cdb75-153">其他 Visual Basic 應用程式無法使用您產生與 Visual Basic 的 COM 物件，因為它們不是，則為 true 的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="cdb75-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="cdb75-154">嘗試將參考加入至這類 COM 物件會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="cdb75-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="cdb75-155">如需詳細資訊，請參閱 < [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="cdb75-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb75-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdb75-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="cdb75-157">COM Interop</span><span class="sxs-lookup"><span data-stu-id="cdb75-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="cdb75-158">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="cdb75-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="cdb75-159">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="cdb75-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="cdb75-160">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="cdb75-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="cdb75-161">互通性的疑難排解</span><span class="sxs-lookup"><span data-stu-id="cdb75-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
