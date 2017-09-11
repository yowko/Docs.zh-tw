---
title: "逐步解說︰ 使用 Visual Basic 建立 COM 物件 |Microsoft 文件"
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
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
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
ms.openlocfilehash: 859a8fc7440eecc0cadbfa8ea236dad7cae99247
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="d8ef9-102">逐步解說：使用 Visual Basic 建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d8ef9-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="d8ef9-103">建立新的應用程式或元件時，最好建立.NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="d8ef9-104">不過，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]也方便您公開給 COM 的.NET Framework 元件</span><span class="sxs-lookup"><span data-stu-id="d8ef9-104">However, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="d8ef9-105">這可讓您提供新的元件需要的 COM 元件的舊版應用程式套件。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="d8ef9-106">本逐步解說示範如何使用[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]公開[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]物件當做 COM 物件，使用和不 COM 類別樣板。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-106">This walkthrough demonstrates how to use [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to expose [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="d8ef9-107">公開 COM 物件的最簡單方式是使用 COM 類別樣板。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="d8ef9-108">COM 類別範本建立新的類別，並設定您的專案產生的 COM 物件的類別以及交互操作層，並向作業系統註冊。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8ef9-109">雖然您也可以公開類別中建立[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]為 unmanaged 程式碼使用 COM 物件，它不是真正的 COM 物件，並且無法由[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-109">Although you can also expose a class created in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="d8ef9-110">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="d8ef9-111">若要使用 COM 類別樣板建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d8ef9-111">To create a COM object by using the COM class template</span></span>  
  
1.  <span data-ttu-id="d8ef9-112">開啟新的 Windows 應用程式專案，從**檔案**功能表按一下**新的專案**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2.  <span data-ttu-id="d8ef9-113">在**新的專案**對話方塊下的**專案類型**欄位中，檢查是否已選取 Windows。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="d8ef9-114">選取**類別庫**從**範本**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="d8ef9-115">會顯示新的專案。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-115">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="d8ef9-116">選取**加入新項目**從**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="d8ef9-117">**加入新項目**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="d8ef9-118">選取**COM 類別**從**範本**清單，然後再按**新增**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="d8ef9-119">加入新的類別，並設定新的專案，COM interop。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-119"> adds a new class and configures the new project for COM interop.</span></span>  
  
5.  <span data-ttu-id="d8ef9-120">加入 COM 類別程式碼，例如屬性、 方法和事件。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6.  <span data-ttu-id="d8ef9-121">選取**建置 ClassLibrary1**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="d8ef9-122">建置組件，並向作業系統註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-122"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="d8ef9-123">建立 COM 物件，而不需要的 COM 類別範本</span><span class="sxs-lookup"><span data-stu-id="d8ef9-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="d8ef9-124">您也可以建立 COM 類別，以手動方式而不是使用 COM 類別範本。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="d8ef9-125">當您從命令列使用或您想要進一步控制定義 COM 物件的方式，此程序會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="d8ef9-126">若要設定您的專案，產生 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d8ef9-126">To set up your project to generate a COM object</span></span>  
  
1.  <span data-ttu-id="d8ef9-127">開啟新的 Windows 應用程式專案，從**檔案**功能表按一下**NewProject**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2.  <span data-ttu-id="d8ef9-128">在**新的專案**對話方塊下的**專案類型**欄位中，檢查是否已選取 Windows。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="d8ef9-129">選取**類別庫**從**範本**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="d8ef9-130">會顯示新的專案。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-130">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="d8ef9-131">在**方案總管 中**，以滑鼠右鍵按一下您的專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="d8ef9-132">**專案設計工具**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-132">The **Project Designer** is displayed.</span></span>  
  
4.  <span data-ttu-id="d8ef9-133">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-133">Click the **Compile** tab.</span></span>  
  
5.  <span data-ttu-id="d8ef9-134">選取**註冊 COM Interop**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="d8ef9-135">若要設定您的類別中的程式碼來建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="d8ef9-135">To set up the code in your class to create a COM object</span></span>  
  
1.  <span data-ttu-id="d8ef9-136">在**方案總管 中**，連按兩下**Class1.vb**以顯示其程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2.  <span data-ttu-id="d8ef9-137">將類別重新命名為 `ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-137">Rename the class to `ComClass1`.</span></span>  
  
3.  <span data-ttu-id="d8ef9-138">新增下列常數來`ComClass1`。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="d8ef9-139">它們會儲存 COM 物件所擁有的全域唯一識別碼 (GUID) 常數。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     <span data-ttu-id="d8ef9-140">[!code-vb[VbVbalrInterop #&2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8ef9-140">[!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]</span></span>  
  
4.  <span data-ttu-id="d8ef9-141">在**工具**] 功能表上，按一下 [**建立 Guid**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-141">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="d8ef9-142">在**建立 GUID**對話方塊中，按一下 **登錄格式**然後按一下 **複製**。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-142">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="d8ef9-143">按一下 [結束] ****。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-143">Click **Exit**.</span></span>  
  
5.  <span data-ttu-id="d8ef9-144">空字串，來取代`ClassId`具有 GUID，移除前置和後端在大括號。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-144">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="d8ef9-145">例如，如果 Guidgen 所提供的 GUID 是`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`然後程式碼應該會出現，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-145">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     <span data-ttu-id="d8ef9-146">[!code-vb[VbVbalrInterop #&3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8ef9-146">[!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]</span></span>  
  
6.  <span data-ttu-id="d8ef9-147">重複上述步驟的`InterfaceId`和`EventsId`常數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-147">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     <span data-ttu-id="d8ef9-148">[!code-vb[VbVbalrInterop #&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8ef9-148">[!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d8ef9-149">請確定 Guid 的新的且唯一的。否則，與其他 COM 元件的 COM 元件可能發生衝突。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-149">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7.  <span data-ttu-id="d8ef9-150">新增`ComClass`屬性設定為`ComClass1`，指定的類別 ID、 介面 ID 以及事件識別碼的 Guid，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="d8ef9-150">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     <span data-ttu-id="d8ef9-151">[!code-vb[VbVbalrInterop #&5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8ef9-151">[!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]</span></span>  
  
8.  <span data-ttu-id="d8ef9-152">COM 類別必須具有無參數`Public Sub New()`建構函式或類別會不正確地登錄。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-152">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="d8ef9-153">將無參數建構函式加入至類別︰</span><span class="sxs-lookup"><span data-stu-id="d8ef9-153">Add a parameterless constructor to the class:</span></span>  
  
     <span data-ttu-id="d8ef9-154">[!code-vb[VbVbalrInterop #&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="d8ef9-154">[!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]</span></span>  
  
9. <span data-ttu-id="d8ef9-155">將屬性、 方法和事件加入至類別，它與結束`End Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-155">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="d8ef9-156">選取**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-156">Select **Build Solution** from the **Build** menu.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="d8ef9-157">建置組件，並向作業系統註冊的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-157"> builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d8ef9-158">產生具有 COM 物件[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不可由其他[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式因為它們不是，則為 true 的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-158">The COM objects you generate with [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot be used by other [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applications because they are not true COM objects.</span></span> <span data-ttu-id="d8ef9-159">嘗試將參考加入至這類 COM 物件將會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-159">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="d8ef9-160">如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ef9-160">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ef9-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ef9-161">See Also</span></span>  
 <span data-ttu-id="d8ef9-162"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="d8ef9-162"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>   
<span data-ttu-id="d8ef9-163"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="d8ef9-163"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="d8ef9-164"> [逐步解說︰ 實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span><span class="sxs-lookup"><span data-stu-id="d8ef9-164"> [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md) </span></span>  
<span data-ttu-id="d8ef9-165"> [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="d8ef9-165"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="d8ef9-166"> [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d8ef9-166"> [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md) </span></span>  
<span data-ttu-id="d8ef9-167"> [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="d8ef9-167"> [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)</span></span>
