---
title: 逐步解說：建立 COM 物件
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: bb312317b2bbcb77bed9e3966db6d9fd5db79e4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396736"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="b52d0-102">逐步解說：使用 Visual Basic 建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="b52d0-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="b52d0-103">建立新的應用程式或元件時，最好建立 .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="b52d0-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="b52d0-104">不過，Visual Basic 也可以輕鬆地將 .NET Framework 元件公開給 COM。</span><span class="sxs-lookup"><span data-stu-id="b52d0-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="b52d0-105">這可讓您針對需要 COM 元件的繼承應用程式套件，提供新的元件。</span><span class="sxs-lookup"><span data-stu-id="b52d0-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="b52d0-106">本逐步解說示範如何使用 Visual Basic 將 .NET Framework 物件公開為 COM 物件，而不論是否使用 COM 類別樣板。</span><span class="sxs-lookup"><span data-stu-id="b52d0-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="b52d0-107">公開 COM 物件的最簡單方式是使用 COM 類別範本。</span><span class="sxs-lookup"><span data-stu-id="b52d0-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="b52d0-108">COM 類別範本會建立新的類別，然後將您的專案設定為產生類別和互通性層做為 COM 物件，並向作業系統註冊它。</span><span class="sxs-lookup"><span data-stu-id="b52d0-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b52d0-109">雖然您也可以將 Visual Basic 中建立的類別公開為 COM 物件，以供非受控程式碼使用，但它並不是真正的 COM 物件，而且無法由 Visual Basic 使用。</span><span class="sxs-lookup"><span data-stu-id="b52d0-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="b52d0-110">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="b52d0-110">For more information, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="b52d0-111">若要使用 COM 類別範本來建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="b52d0-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="b52d0-112">按一下 [**新增專案**]，從 [ **File**檔案] 功能表開啟新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b52d0-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="b52d0-113">在 [**新增專案**] 對話方塊的 [**專案類型**] 欄位底下，檢查是否已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="b52d0-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="b52d0-114">從 [**範本**] 清單中選取 [**類別庫**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b52d0-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="b52d0-115">隨即顯示新專案。</span><span class="sxs-lookup"><span data-stu-id="b52d0-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="b52d0-116">從 [**專案**] 功能表中選取 [**加入新專案**]。</span><span class="sxs-lookup"><span data-stu-id="b52d0-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="b52d0-117">[ **加入新項目** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b52d0-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="b52d0-118">從 [**範本**] 清單中選取 [ **COM 類別**]，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="b52d0-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="b52d0-119">Visual Basic 加入新的類別，並為 COM Interop 設定新的專案。</span><span class="sxs-lookup"><span data-stu-id="b52d0-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="b52d0-120">將屬性、方法和事件等程式碼加入 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="b52d0-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="b52d0-121">從 [**建立**] 功能表中選取 [**組建 ClassLibrary1** ]。</span><span class="sxs-lookup"><span data-stu-id="b52d0-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="b52d0-122">Visual Basic 會建立元件，並向作業系統註冊 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="b52d0-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="b52d0-123">不搭配 COM 類別樣板來建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="b52d0-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="b52d0-124">您也可以手動建立 COM 類別，而不使用 COM 類別範本。</span><span class="sxs-lookup"><span data-stu-id="b52d0-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="b52d0-125">當您從命令列工作時，或當您想要更充分掌控 COM 物件的定義時，此程式會很有説明。</span><span class="sxs-lookup"><span data-stu-id="b52d0-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="b52d0-126">若要設定您的專案以產生 COM 物件</span><span class="sxs-lookup"><span data-stu-id="b52d0-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="b52d0-127">按一下 [檔案] 功能表中的 [ **NewProject** **]，以**開啟新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b52d0-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="b52d0-128">在 [**新增專案**] 對話方塊的 [**專案類型**] 欄位底下，檢查是否已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="b52d0-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="b52d0-129">從 [**範本**] 清單中選取 [**類別庫**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b52d0-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="b52d0-130">隨即顯示新專案。</span><span class="sxs-lookup"><span data-stu-id="b52d0-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="b52d0-131">在 [方案總管]\*\*\*\* 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b52d0-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="b52d0-132">隨即顯示 [**專案設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="b52d0-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="b52d0-133">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b52d0-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="b52d0-134">選取 [**註冊 COM Interop** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b52d0-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="b52d0-135">若要在您的類別中設定程式碼來建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="b52d0-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="b52d0-136">在**方案總管**中，按兩下 [ **Class1** ] 以顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="b52d0-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="b52d0-137">將類別重新命名為 `ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="b52d0-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="b52d0-138">將下列常數新增至 `ComClass1` 。</span><span class="sxs-lookup"><span data-stu-id="b52d0-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="b52d0-139">它們會儲存 COM 物件必須擁有的全域唯一識別碼（GUID）常數。</span><span class="sxs-lookup"><span data-stu-id="b52d0-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="b52d0-140">在 [工具]\*\*\*\* 功能表上，按一下 [建立 GUID]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b52d0-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="b52d0-141">在 [建立 GUID]\*\*\*\* 對話方塊中，依序按一下 [登錄格式]\*\*\*\* 和 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b52d0-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="b52d0-142">按一下 **[結束]**。</span><span class="sxs-lookup"><span data-stu-id="b52d0-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="b52d0-143">將的空字串取代為 `ClassId` GUID，移除開頭和尾端的大括弧。</span><span class="sxs-lookup"><span data-stu-id="b52d0-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="b52d0-144">例如，如果 Guidgen 所提供的 GUID 是， `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` 則您的程式碼應該會如下所示。</span><span class="sxs-lookup"><span data-stu-id="b52d0-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="b52d0-145">針對和常數重複上述步驟 `InterfaceId` `EventsId` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b52d0-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="b52d0-146">請確定 Guid 是新的，而且是唯一的;否則，您的 COM 元件可能會與其他 COM 元件衝突。</span><span class="sxs-lookup"><span data-stu-id="b52d0-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="b52d0-147">將 `ComClass` 屬性新增至 `ComClass1` ，並指定類別識別碼、介面識別碼和事件識別碼的 guid，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b52d0-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="b52d0-148">COM 類別必須有無參數的函式 `Public Sub New()` ，否則類別將不會正確地註冊。</span><span class="sxs-lookup"><span data-stu-id="b52d0-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="b52d0-149">將無參數的構造函式新增至類別：</span><span class="sxs-lookup"><span data-stu-id="b52d0-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="b52d0-150">將屬性、方法和事件加入至類別，並以 `End Class` 語句結束。</span><span class="sxs-lookup"><span data-stu-id="b52d0-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="b52d0-151">從 [**建立**] 功能表中選取 [**建立方案**]。</span><span class="sxs-lookup"><span data-stu-id="b52d0-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="b52d0-152">Visual Basic 會建立元件，並向作業系統註冊 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="b52d0-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b52d0-153">您使用 Visual Basic 產生的 COM 物件無法供其他 Visual Basic 應用程式使用，因為它們不是真正的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="b52d0-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="b52d0-154">嘗試加入對這類 COM 物件的參考將會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="b52d0-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="b52d0-155">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="b52d0-155">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b52d0-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b52d0-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="b52d0-157">COM Interop</span><span class="sxs-lookup"><span data-stu-id="b52d0-157">COM Interop</span></span>](index.md)
- [<span data-ttu-id="b52d0-158">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="b52d0-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="b52d0-159">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="b52d0-159">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="b52d0-160">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="b52d0-160">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="b52d0-161">疑難排解互通性的問題</span><span class="sxs-lookup"><span data-stu-id="b52d0-161">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
