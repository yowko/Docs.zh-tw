---
title: 作法：建立 COM 包裝函式
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e34785fce3cd88bfe4fe4b075ba34b8d22bff4
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469664"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="226e8-102">作法：建立 COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="226e8-102">How to: Create COM Wrappers</span></span>

<span data-ttu-id="226e8-103">您可以使用 Visual Studio 2005 功能或 .NET Framework 工具 Tlbimp.exe 和 Regasm.exe 來建立元件物件模型 (COM) 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="226e8-103">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="226e8-104">這兩種方法會產生兩種類型的 COM 包裝函式：</span><span class="sxs-lookup"><span data-stu-id="226e8-104">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="226e8-105">型別程式庫中的[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md)，會以 Managed 程式碼執行 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="226e8-105">A [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="226e8-106">具有所需登錄設定的 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md)，會在原生應用程式中執行 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="226e8-106">A [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="226e8-107">在 Visual Studio 2005 中，您可以將 COM 包裝函式新增成為專案的參考。</span><span class="sxs-lookup"><span data-stu-id="226e8-107">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="226e8-108">在受控的應用程式中包裝 COM 物件</span><span class="sxs-lookup"><span data-stu-id="226e8-108">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="226e8-109">使用 Visual Studio 建立執行階段可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="226e8-109">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="226e8-110">開啟 Managed 應用程式的專案。</span><span class="sxs-lookup"><span data-stu-id="226e8-110">Open the project for your managed application.</span></span>

2. <span data-ttu-id="226e8-111">在 [專案] 功能表上，按一下 [顯示所有檔案]。</span><span class="sxs-lookup"><span data-stu-id="226e8-111">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="226e8-112">在 [專案] 功能表上，按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="226e8-112">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="226e8-113">在 [新增參考] 對話方塊中，按一下 [COM] 索引標籤，選取您要使用的元件，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="226e8-113">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="226e8-114">在方案總管中，請注意，會將 COM 元件新增至專案中的 [參考] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="226e8-114">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="226e8-115">現在，您可以撰寫程式碼以存取 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="226e8-115">You can now write code to access the COM object.</span></span> <span data-ttu-id="226e8-116">您可以從宣告物件開始，例如使用 Visual Basic `Imports` 陳述式或 C# `Using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="226e8-116">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="226e8-117">如果您想要開發 Microsoft Office 元件，請先安裝可從 Microsoft 下載中心取得的 [Microsoft Office 主要 Interop 組件](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA)。</span><span class="sxs-lookup"><span data-stu-id="226e8-117">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies](https://go.microsoft.com/fwlink/?LinkId=50479) (PIAs) from the Microsoft Download Center.</span></span> <span data-ttu-id="226e8-118">在步驟 4 中，選取您所需之 Office 產品的最新版可用物件程式庫，例如 **Microsoft Word 11.0 物件程式庫**。</span><span class="sxs-lookup"><span data-stu-id="226e8-118">In step 4, select the latest version of the object library available for the Office product you want, such as the **Microsoft Word 11.0 Object Library**.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="226e8-119">使用 .NET Framework 工具建立執行階段可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="226e8-119">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="226e8-120">執行 [Tlbimp.exe (型別程式庫匯入工具)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 工具。</span><span class="sxs-lookup"><span data-stu-id="226e8-120">Run the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="226e8-121">這項工具所建立的組件，包含原始型別程式庫中所定義之類型的執行階段中繼資料。</span><span class="sxs-lookup"><span data-stu-id="226e8-121">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="226e8-122">在原生應用程式中包裝受控物件</span><span class="sxs-lookup"><span data-stu-id="226e8-122">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="226e8-123">使用 Visual Studio 建立 COM 可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="226e8-123">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="226e8-124">針對您要在機器碼中執行的 Managed 類別，建立類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="226e8-124">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="226e8-125">此類別必須具有預設的建構函式。</span><span class="sxs-lookup"><span data-stu-id="226e8-125">The class must have a default constructor.</span></span>  
  
     <span data-ttu-id="226e8-126">確認您在 AssemblyInfo 檔案中擁有組件的完整四部分版本號碼。</span><span class="sxs-lookup"><span data-stu-id="226e8-126">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="226e8-127">這個號碼對於在 Windows 登錄中維護版本控制是必要的。</span><span class="sxs-lookup"><span data-stu-id="226e8-127">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="226e8-128">如需版本號碼的詳細資訊，請參閱[組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="226e8-128">For more information about version numbers, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
2. <span data-ttu-id="226e8-129">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="226e8-129">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="226e8-130">按一下 [編譯] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="226e8-130">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="226e8-131">選取 [註冊 COM Interop] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="226e8-131">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="226e8-132">當您建置專案時，組件會自動註冊 COM Interop。</span><span class="sxs-lookup"><span data-stu-id="226e8-132">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="226e8-133">如果您是在 Visual Studio 2005 中建置原生應用程式，即可在 [專案] 功能表上按一下 [新增參考] 以使用組件。</span><span class="sxs-lookup"><span data-stu-id="226e8-133">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="226e8-134">使用 .NET Framework 工具建立 COM 可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="226e8-134">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="226e8-135">執行 [Regasm.exe (組件註冊工具)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 工具。</span><span class="sxs-lookup"><span data-stu-id="226e8-135">Run the [Regasm.exe (Assembly Registration Tool)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="226e8-136">這項工具會讀取組件中繼資料，並將需要的項目新增至登錄。</span><span class="sxs-lookup"><span data-stu-id="226e8-136">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="226e8-137">因此，COM 用戶端便能明確地建立 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="226e8-137">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="226e8-138">您可以使用與原生 COM 類別相同的方式來使用組件。</span><span class="sxs-lookup"><span data-stu-id="226e8-138">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="226e8-139">您可以對位於任何目錄中的組件執行 Regasm.exe，然後執行 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 將它移到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="226e8-139">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="226e8-140">移動組件並不會使位置登錄項目無效，因為只要在其他位置找不到組件，就一律會對全域組件快取進行檢查。</span><span class="sxs-lookup"><span data-stu-id="226e8-140">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226e8-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="226e8-141">See also</span></span>

- [<span data-ttu-id="226e8-142">執行階段可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="226e8-142">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="226e8-143">COM 可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="226e8-143">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)
