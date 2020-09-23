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
ms.openlocfilehash: 90a21b70b45902a9f4fd559a97e777f26043fffb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075612"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="d27dd-102">逐步解說：使用 Visual Basic 建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d27dd-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>

<span data-ttu-id="d27dd-103">建立新的應用程式或元件時，最好是建立 .NET Framework 元件。</span><span class="sxs-lookup"><span data-stu-id="d27dd-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="d27dd-104">不過，Visual Basic 也可讓您輕鬆地將 .NET Framework 元件公開至 COM。</span><span class="sxs-lookup"><span data-stu-id="d27dd-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="d27dd-105">這可讓您為需要 COM 元件的繼承應用程式套件提供新元件。</span><span class="sxs-lookup"><span data-stu-id="d27dd-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="d27dd-106">本逐步解說示範如何使用 Visual Basic 將 .NET Framework 物件公開為 COM 物件，不論是否有 COM 類別範本。</span><span class="sxs-lookup"><span data-stu-id="d27dd-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="d27dd-107">公開 COM 物件最簡單的方式是使用 COM 類別範本。</span><span class="sxs-lookup"><span data-stu-id="d27dd-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="d27dd-108">此範本會建立新的類別，然後設定您的專案以使用交互操作層作為 COM 物件來產生類別，並將它註冊到作業系統。</span><span class="sxs-lookup"><span data-stu-id="d27dd-108">This template creates a new class, then configures your project to generate the class with an interoperability layer as a COM object, and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d27dd-109">雖然您也可以將 Visual Basic 中建立的類別公開為非受控程式碼要使用的 COM 物件，但它並不是真正的 COM 物件，Visual Basic 無法使用。</span><span class="sxs-lookup"><span data-stu-id="d27dd-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="d27dd-110">如需詳細資訊，請參閱 [.NET Framework 應用程式中的 COM 互通性](com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="d27dd-110">For more information, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="d27dd-111">使用 COM 類別範本來建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d27dd-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="d27dd-112">按一下 [**新增專案**]，開啟 [檔案] 功能表**中的新**Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d27dd-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="d27dd-113">在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 欄位底下，檢查是否已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="d27dd-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="d27dd-114">從 [**範本**] 清單中選取 [**類別庫**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d27dd-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="d27dd-115">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="d27dd-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="d27dd-116">從 [**專案**] 功能表中選取 [**加入新專案**]。</span><span class="sxs-lookup"><span data-stu-id="d27dd-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="d27dd-117">[ **加入新項目** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d27dd-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="d27dd-118">從 [**範本**] 清單中選取 [ **COM 類別**]，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d27dd-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="d27dd-119">Visual Basic 加入新的類別，並設定 COM interop 的新專案。</span><span class="sxs-lookup"><span data-stu-id="d27dd-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="d27dd-120">將屬性、方法和事件等程式碼新增至 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="d27dd-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="d27dd-121">從 [**組建**] 功能表選取 [**組建 ClassLibrary1** ]。</span><span class="sxs-lookup"><span data-stu-id="d27dd-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="d27dd-122">Visual Basic 會建立元件，並向作業系統註冊 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d27dd-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="d27dd-123">建立不具 COM 類別範本的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d27dd-123">Creating COM Objects without the COM Class Template</span></span>  

 <span data-ttu-id="d27dd-124">您也可以手動建立 COM 類別，而不是使用 COM 類別範本。</span><span class="sxs-lookup"><span data-stu-id="d27dd-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="d27dd-125">當您從命令列執行時，或當您想要更充分掌控 COM 物件的定義時，此程式會很有説明。</span><span class="sxs-lookup"><span data-stu-id="d27dd-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="d27dd-126">設定您的專案以產生 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d27dd-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="d27dd-127">按一下 [檔案] 功能表 **中的 [** **NewProject**]，以開啟新的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d27dd-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="d27dd-128">在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 欄位底下，檢查是否已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="d27dd-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="d27dd-129">從 [**範本**] 清單中選取 [**類別庫**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d27dd-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="d27dd-130">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="d27dd-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="d27dd-131">在 [方案總管]\*\*\*\* 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d27dd-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="d27dd-132">[ **專案設計** 工具] 隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="d27dd-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="d27dd-133">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d27dd-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="d27dd-134">選取 [ **註冊 COM Interop** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d27dd-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="d27dd-135">若要在您的類別中設定程式碼來建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d27dd-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="d27dd-136">在 **方案總管**中，按兩下 [ **Class1** ] 以顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="d27dd-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="d27dd-137">將類別重新命名為 `ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="d27dd-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="d27dd-138">將下列常數加入至 `ComClass1` 。</span><span class="sxs-lookup"><span data-stu-id="d27dd-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="d27dd-139">它們會將全域唯一識別碼儲存 (GUID) 必須具有 COM 物件的常數。</span><span class="sxs-lookup"><span data-stu-id="d27dd-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="d27dd-140">在 [工具]\*\*\*\* 功能表上，按一下 [建立 GUID]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d27dd-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="d27dd-141">在 [建立 GUID]\*\*\*\* 對話方塊中，依序按一下 [登錄格式]\*\*\*\* 和 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d27dd-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="d27dd-142">按一下 **[結束]**。</span><span class="sxs-lookup"><span data-stu-id="d27dd-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="d27dd-143">以 GUID 取代的空字串 `ClassId` ，移除開頭和尾端的大括弧。</span><span class="sxs-lookup"><span data-stu-id="d27dd-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="d27dd-144">例如，如果 Guidgen 所提供的 GUID， `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` 則您的程式碼應該會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="d27dd-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="d27dd-145">針對和常數重複上述步驟 `InterfaceId` `EventsId` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d27dd-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="d27dd-146">請確定 Guid 是新的且唯一的。否則，您的 COM 元件可能會與其他 COM 元件發生衝突。</span><span class="sxs-lookup"><span data-stu-id="d27dd-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="d27dd-147">將 `ComClass` 屬性新增至 `ComClass1` ，並指定類別識別碼、介面識別碼和事件識別碼的 guid，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d27dd-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="d27dd-148">COM 類別必須有無參數的函式 `Public Sub New()` ，否則類別將無法正確註冊。</span><span class="sxs-lookup"><span data-stu-id="d27dd-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="d27dd-149">將無參數的函式新增至類別：</span><span class="sxs-lookup"><span data-stu-id="d27dd-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="d27dd-150">將屬性、方法和事件加入至類別，並以 `End Class` 語句結尾。</span><span class="sxs-lookup"><span data-stu-id="d27dd-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="d27dd-151">從 [**組建**] 功能表選取 [**建立方案**]。</span><span class="sxs-lookup"><span data-stu-id="d27dd-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="d27dd-152">Visual Basic 會建立元件，並向作業系統註冊 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d27dd-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d27dd-153">您使用 Visual Basic 產生的 COM 物件無法供其他 Visual Basic 應用程式使用，因為它們不是真正的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d27dd-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="d27dd-154">嘗試加入這類 COM 物件的參考將會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="d27dd-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="d27dd-155">如需詳細資訊，請參閱 [.NET Framework 應用程式中的 COM 互通性](com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="d27dd-155">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27dd-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d27dd-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="d27dd-157">COM Interop</span><span class="sxs-lookup"><span data-stu-id="d27dd-157">COM Interop</span></span>](index.md)
- [<span data-ttu-id="d27dd-158">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="d27dd-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="d27dd-159">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="d27dd-159">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="d27dd-160">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="d27dd-160">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="d27dd-161">疑難排解互通性的問題</span><span class="sxs-lookup"><span data-stu-id="d27dd-161">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
