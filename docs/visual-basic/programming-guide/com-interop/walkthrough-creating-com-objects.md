---
title: "逐步解說：使用 Visual Basic 建立 COM 物件"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff7d3868a2e3ddaba06ebc6f98c8eacfc7299366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="23a52-102">逐步解說：使用 Visual Basic 建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="23a52-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="23a52-103">建立新的應用程式或元件時，最好建立.NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="23a52-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="23a52-104">不過，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]也可輕鬆公開.NET Framework 元件至 com。</span><span class="sxs-lookup"><span data-stu-id="23a52-104">However, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="23a52-105">這可讓您針對需要 COM 元件的舊版應用程式套件提供新的元件。</span><span class="sxs-lookup"><span data-stu-id="23a52-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="23a52-106">本逐步解說示範如何使用[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]公開[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]物件當做 COM 物件，及未在 COM 類別樣板。</span><span class="sxs-lookup"><span data-stu-id="23a52-106">This walkthrough demonstrates how to use [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to expose [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="23a52-107">公開 COM 物件的最簡單方式是使用 COM 類別樣板。</span><span class="sxs-lookup"><span data-stu-id="23a52-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="23a52-108">COM 類別範本會建立新的類別，並設定您的專案產生的類別和互通性的圖層為 COM 物件，並向作業系統。</span><span class="sxs-lookup"><span data-stu-id="23a52-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23a52-109">雖然您也可以公開類別中建立[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]為要使用的 unmanaged 程式碼的 COM 物件，它不是真正的 COM 物件，並且無法由[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="23a52-109">Although you can also expose a class created in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="23a52-110">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="23a52-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="23a52-111">若要使用 COM 類別樣板建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="23a52-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="23a52-112">開啟新的 Windows 應用程式專案，從**檔案**功能表按一下**新專案**。</span><span class="sxs-lookup"><span data-stu-id="23a52-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="23a52-113">在**新專案**對話方塊底下**專案類型**欄位中，Windows 會選取核取。</span><span class="sxs-lookup"><span data-stu-id="23a52-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="23a52-114">選取**類別庫**從**範本**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="23a52-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="23a52-115">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="23a52-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="23a52-116">選取**加入新項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="23a52-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="23a52-117">隨即顯示 [ 新增項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="23a52-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="23a52-118">選取**COM 類別**從**範本**清單，然後再按**新增**。</span><span class="sxs-lookup"><span data-stu-id="23a52-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="23a52-119">加入新的類別，並設定新的專案，COM interop。</span><span class="sxs-lookup"><span data-stu-id="23a52-119"> adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="23a52-120">例如屬性、 方法和事件的程式碼加入的 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="23a52-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="23a52-121">選取**建置 ClassLibrary1**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="23a52-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="23a52-122">建置組件，並向作業系統註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="23a52-122"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="23a52-123">建立 COM 物件不在 COM 類別範本</span><span class="sxs-lookup"><span data-stu-id="23a52-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="23a52-124">您也可以建立以手動方式而不是使用 COM 類別樣板的 COM 類別。</span><span class="sxs-lookup"><span data-stu-id="23a52-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="23a52-125">當您從命令列使用或是您想要更充分掌控 COM 物件的定義方式，此程序會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="23a52-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="23a52-126">若要設定您的專案，以產生 COM 物件</span><span class="sxs-lookup"><span data-stu-id="23a52-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="23a52-127">開啟新的 Windows 應用程式專案，從**檔案**功能表按一下**[新增專案]**。</span><span class="sxs-lookup"><span data-stu-id="23a52-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="23a52-128">在**新專案**對話方塊底下**專案類型**欄位中，Windows 會選取核取。</span><span class="sxs-lookup"><span data-stu-id="23a52-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="23a52-129">選取**類別庫**從**範本**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="23a52-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="23a52-130">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="23a52-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="23a52-131">在**方案總管 中**，以滑鼠右鍵按一下您的專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="23a52-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="23a52-132">**專案設計工具**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="23a52-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="23a52-133">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="23a52-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="23a52-134">選取**註冊 COM Interop**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="23a52-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="23a52-135">若要設定您的類別中的程式碼建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="23a52-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="23a52-136">在**方案總管 中**，連按兩下**Class1.vb**以顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="23a52-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="23a52-137">將類別重新命名為 `ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="23a52-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="23a52-138">加入下列的常數`ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="23a52-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="23a52-139">它們會儲存 COM 物件時需要有的全域唯一識別碼 (GUID) 常數。</span><span class="sxs-lookup"><span data-stu-id="23a52-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  <span data-ttu-id="23a52-140">在 [工具] 功能表上，按一下 [建立 GUID]。</span><span class="sxs-lookup"><span data-stu-id="23a52-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="23a52-141">在 [建立 GUID] 對話方塊中，依序按一下 [登錄格式] 和 [複製]。</span><span class="sxs-lookup"><span data-stu-id="23a52-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="23a52-142">按一下 [結束] 。</span><span class="sxs-lookup"><span data-stu-id="23a52-142">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="23a52-143">取代為空字串`ClassId`具有 GUID，移除開頭和尾端大括號。</span><span class="sxs-lookup"><span data-stu-id="23a52-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="23a52-144">例如，如果 Guidgen 所提供的 GUID 是`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`那麼您的程式碼應該會出現，如下所示。</span><span class="sxs-lookup"><span data-stu-id="23a52-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  <span data-ttu-id="23a52-145">重複上述步驟的`InterfaceId`和`EventsId`常數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="23a52-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="23a52-146">請確定 Guid 的新的和唯一的。否則，您的 COM 元件可能與其他 COM 元件發生衝突。</span><span class="sxs-lookup"><span data-stu-id="23a52-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="23a52-147">新增`ComClass`屬性`ComClass1`，指定的類別 ID、 介面 ID 以及事件識別碼的 Guid，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="23a52-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  <span data-ttu-id="23a52-148">COM 類別必須具有無參數`Public Sub New()`建構函式或類別將不會註冊正確。</span><span class="sxs-lookup"><span data-stu-id="23a52-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="23a52-149">無參數建構函式加入類別：</span><span class="sxs-lookup"><span data-stu-id="23a52-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. <span data-ttu-id="23a52-150">將屬性、 方法和事件加入至類別，其與結束`End Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="23a52-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="23a52-151">選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="23a52-151">Select **Build Solution** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="23a52-152">建置組件，並向作業系統註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="23a52-152"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23a52-153">產生具有的 COM 物件[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]不可由其他[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]應用程式因為它們不是，則為 true 的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="23a52-153">The COM objects you generate with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot be used by other [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] applications because they are not true COM objects.</span></span> <span data-ttu-id="23a52-154">嘗試將參考加入至這類 COM 物件將會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="23a52-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="23a52-155">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="23a52-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a52-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23a52-156">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [<span data-ttu-id="23a52-157">COM Interop</span><span class="sxs-lookup"><span data-stu-id="23a52-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="23a52-158">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="23a52-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [<span data-ttu-id="23a52-159">#Region 指示詞</span><span class="sxs-lookup"><span data-stu-id="23a52-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="23a52-160">.NET Framework 應用程式中的 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="23a52-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="23a52-161">互通性的疑難排解</span><span class="sxs-lookup"><span data-stu-id="23a52-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
