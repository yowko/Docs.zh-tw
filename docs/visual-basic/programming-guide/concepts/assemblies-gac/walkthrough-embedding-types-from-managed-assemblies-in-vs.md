---
title: "逐步解說： 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4411b40d8ffbdf2b74c49152db675286d91b43ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="7a290-102">逐步解說： 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型</span><span class="sxs-lookup"><span data-stu-id="7a290-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="7a290-103">若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。</span><span class="sxs-lookup"><span data-stu-id="7a290-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="7a290-104">也就是說，您可以撰寫程式來使用 Managed 程式庫多個版本的類型，而不需重新編譯每個版本。</span><span class="sxs-lookup"><span data-stu-id="7a290-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="7a290-105">內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。</span><span class="sxs-lookup"><span data-stu-id="7a290-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="7a290-106">當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="7a290-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="7a290-107">不過，您也可以搭配使用類型內嵌功能與完全受管理的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7a290-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="7a290-108">您可以透過組件來內嵌具有下列特性的類型資訊：</span><span class="sxs-lookup"><span data-stu-id="7a290-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="7a290-109">組件已公開至少一個公用介面。</span><span class="sxs-lookup"><span data-stu-id="7a290-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="7a290-110">內嵌的介面已標註 `ComImport` 屬性和 `Guid` 屬性 (以及唯一 GUID)。</span><span class="sxs-lookup"><span data-stu-id="7a290-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="7a290-111">您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件 </span><span class="sxs-lookup"><span data-stu-id="7a290-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="7a290-112">(根據預設，Visual Basic 專案範本包含組件層級`Guid`屬性。)</span><span class="sxs-lookup"><span data-stu-id="7a290-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="7a290-113">指定可內嵌的公用介面之後，您可以建立執行階段類別以實作這些介面。</span><span class="sxs-lookup"><span data-stu-id="7a290-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="7a290-114">接著，用戶端程式即會參考包含公用介面的組件，然後將參考的 `Embed Interop Types` 屬性設為 `True`，以在設計階段內嵌這些介面的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="7a290-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="7a290-115">這相當於使用命令列編譯器，並使用 `/link` 編譯器選項來參考組件。</span><span class="sxs-lookup"><span data-stu-id="7a290-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="7a290-116">用戶端程式即可載入以這些介面為類型的執行階段物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="7a290-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="7a290-117">如果您建立新版本的強式名稱執行階段組件，用戶端程式就不需要使用更新的執行階段組件來重新編譯。</span><span class="sxs-lookup"><span data-stu-id="7a290-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="7a290-118">相反地，用戶端程式會繼續使用執行階段組件適用的任何版本，並針對公用介面使用內嵌的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="7a290-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="7a290-119">由於類型內嵌的主要功能是支援透過 COM Interop 組件進行類型資訊內嵌，因此當您將類型資訊內嵌在完全受管理的解決方案中時，也會套用下列限制：</span><span class="sxs-lookup"><span data-stu-id="7a290-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="7a290-120">只會內嵌 COM Interop 專屬的屬性，而忽略其他屬性。</span><span class="sxs-lookup"><span data-stu-id="7a290-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="7a290-121">如果某類型使用泛型參數，而該泛型參數的類型是內嵌的類型，您就不能跨組件界限使用此類型。</span><span class="sxs-lookup"><span data-stu-id="7a290-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="7a290-122">跨組件界限的範例包括從其他組件呼叫方法，或透過定義於其他組件上的類型來衍生類型。</span><span class="sxs-lookup"><span data-stu-id="7a290-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="7a290-123">系統不會內嵌常數。</span><span class="sxs-lookup"><span data-stu-id="7a290-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="7a290-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別不支援內嵌類型作為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="7a290-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="7a290-125">您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。</span><span class="sxs-lookup"><span data-stu-id="7a290-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="7a290-126">在這個逐步解說中，您將進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="7a290-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="7a290-127">建立具有公用介面的強式名稱組件，且該介面包含可內嵌的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="7a290-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="7a290-128">建立強式名稱的執行階段組件，以實作上述公用介面。</span><span class="sxs-lookup"><span data-stu-id="7a290-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="7a290-129">建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7a290-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="7a290-130">修改並重新建置執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="7a290-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="7a290-131">執行用戶端程式，查看是否正在使用新版本的執行階段組件，而不必重新編譯用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="7a290-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="7a290-132">建立介面</span><span class="sxs-lookup"><span data-stu-id="7a290-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="7a290-133">若要建立類型等價介面專案</span><span class="sxs-lookup"><span data-stu-id="7a290-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="7a290-134">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="7a290-135">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="7a290-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="7a290-136">在 [範本] 窗格中，選取 [類別庫]。</span><span class="sxs-lookup"><span data-stu-id="7a290-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="7a290-137">在 [名稱] 方塊中，輸入 `TypeEquivalenceInterface` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7a290-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="7a290-138">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="7a290-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="7a290-139">在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="7a290-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="7a290-140">將檔案重新命名為 `ISampleInterface.vb`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="7a290-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="7a290-141">重新命名檔案時，也會將類別重新命名為 `ISampleInterface`。</span><span class="sxs-lookup"><span data-stu-id="7a290-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="7a290-142">這個類別將代表類別的公用介面。</span><span class="sxs-lookup"><span data-stu-id="7a290-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="7a290-143">以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="7a290-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="7a290-144">按一下 [編譯] 索引標籤。將輸出路徑設為開發電腦上的有效位置，例如 `C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="7a290-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="7a290-145">這個位置也會用於本逐步解說稍後的步驟。</span><span class="sxs-lookup"><span data-stu-id="7a290-145">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="7a290-146">在編輯專案屬性期間，按一下 [簽署] 索引標籤。選取 [簽署組件] 選項。</span><span class="sxs-lookup"><span data-stu-id="7a290-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="7a290-147">在 [選擇強式名稱金鑰檔案] 清單中，按一下 [<新增...>]。</span><span class="sxs-lookup"><span data-stu-id="7a290-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="7a290-148">在 [金鑰檔案名稱] 方塊中，輸入 `key.snk`。</span><span class="sxs-lookup"><span data-stu-id="7a290-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="7a290-149">清除 [以密碼保護我的金鑰檔] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7a290-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="7a290-150">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7a290-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="7a290-151">開啟 ISampleInterface.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="7a290-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="7a290-152">將下列程式碼加入 ISampleInterface 類別檔案，以建立 ISampleInterface 介面。</span><span class="sxs-lookup"><span data-stu-id="7a290-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  <span data-ttu-id="7a290-153">在 [工具] 功能表上，按一下 [建立 GUID]。</span><span class="sxs-lookup"><span data-stu-id="7a290-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="7a290-154">在 [建立 GUID] 對話方塊中，依序按一下 [登錄格式] 和 [複製]。</span><span class="sxs-lookup"><span data-stu-id="7a290-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="7a290-155">按一下 [結束] 。</span><span class="sxs-lookup"><span data-stu-id="7a290-155">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="7a290-156">刪除 `Guid` 屬性中的範例 GUID，然後貼上您從 [建立 GUID] 對話方塊所複製的 GUID。</span><span class="sxs-lookup"><span data-stu-id="7a290-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="7a290-157">移除已複製 GUID 的大括號 ({})。</span><span class="sxs-lookup"><span data-stu-id="7a290-157">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="7a290-158">在 [專案] 功能表上，按一下 [顯示所有檔案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-158">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="7a290-159">在**方案總管 中**，依序展開**我的專案**資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a290-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="7a290-160">按兩下 AssemblyInfo.vb。</span><span class="sxs-lookup"><span data-stu-id="7a290-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="7a290-161">將下列屬性加入檔案中。</span><span class="sxs-lookup"><span data-stu-id="7a290-161">Add the following attribute to the file.</span></span>  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     <span data-ttu-id="7a290-162">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="7a290-162">Save the file.</span></span>  
  
11. <span data-ttu-id="7a290-163">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="7a290-163">Save the project.</span></span>  
  
12. <span data-ttu-id="7a290-164">以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="7a290-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="7a290-165">即會編譯類別庫 .dll 檔案，並將其儲存至指定的建置輸出路徑 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="7a290-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="7a290-166">建立執行階段類別</span><span class="sxs-lookup"><span data-stu-id="7a290-166">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="7a290-167">若要建立類型等價執行階段專案</span><span class="sxs-lookup"><span data-stu-id="7a290-167">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="7a290-168">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="7a290-169">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="7a290-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="7a290-170">在 [範本] 窗格中，選取 [類別庫]。</span><span class="sxs-lookup"><span data-stu-id="7a290-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="7a290-171">在 [名稱] 方塊中，輸入 `TypeEquivalenceRuntime` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7a290-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="7a290-172">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="7a290-172">The new project is created.</span></span>  
  
3.  <span data-ttu-id="7a290-173">在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="7a290-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="7a290-174">將檔案重新命名為 `SampleClass.vb`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="7a290-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="7a290-175">重新命名檔案時，也會將類別重新命名為 `SampleClass`。</span><span class="sxs-lookup"><span data-stu-id="7a290-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="7a290-176">此類別會實作 `ISampleInterface` 介面。</span><span class="sxs-lookup"><span data-stu-id="7a290-176">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="7a290-177">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="7a290-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="7a290-178">按一下 [編譯] 索引標籤。將輸出路徑設為您在 TypeEquivalenceInterface 專案中使用的相同位置，例如 `C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="7a290-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="7a290-179">在編輯專案屬性期間，按一下 [簽署] 索引標籤。選取 [簽署組件] 選項。</span><span class="sxs-lookup"><span data-stu-id="7a290-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="7a290-180">在 [選擇強式名稱金鑰檔案] 清單中，按一下 [<新增...>]。</span><span class="sxs-lookup"><span data-stu-id="7a290-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="7a290-181">在 [金鑰檔案名稱] 方塊中，輸入 `key.snk`。</span><span class="sxs-lookup"><span data-stu-id="7a290-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="7a290-182">清除 [以密碼保護我的金鑰檔] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7a290-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="7a290-183">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7a290-183">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="7a290-184">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="7a290-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="7a290-185">按一下 [瀏覽] 索引標籤，並瀏覽至輸出路徑資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a290-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="7a290-186">選取 TypeEquivalenceInterface.dll 檔案，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7a290-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="7a290-187">在 [專案] 功能表上，按一下 [顯示所有檔案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-187">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="7a290-188">展開方案總管中的 [參考] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a290-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="7a290-189">選取 TypeEquivalenceInterface 參考。</span><span class="sxs-lookup"><span data-stu-id="7a290-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="7a290-190">在 TypeEquivalenceInterface 參考的 [屬性] 視窗中，將 [特定版本] 屬性設為 [False]。</span><span class="sxs-lookup"><span data-stu-id="7a290-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="7a290-191">將下列程式碼加入 SampleClass 類別檔案中，以建立 SampleClass 類別。</span><span class="sxs-lookup"><span data-stu-id="7a290-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
    ```vb  
    Imports TypeEquivalenceInterface  
  
    Public Class SampleClass  
        Implements ISampleInterface  
  
        Private p_UserInput As String  
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput  
            Get  
                Return p_UserInput  
            End Get  
        End Property  
  
        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput  
            Console.WriteLine("Please enter a value:")  
            p_UserInput = Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
10. <span data-ttu-id="7a290-192">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="7a290-192">Save the project.</span></span>  
  
11. <span data-ttu-id="7a290-193">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="7a290-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="7a290-194">即會編譯類別庫 .dll 檔案，並將其儲存至指定的建置輸出路徑 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="7a290-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="7a290-195">建立用戶端專案</span><span class="sxs-lookup"><span data-stu-id="7a290-195">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="7a290-196">若要建立類型等價用戶端專案</span><span class="sxs-lookup"><span data-stu-id="7a290-196">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="7a290-197">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="7a290-198">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="7a290-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="7a290-199">選取 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="7a290-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="7a290-200">在 [名稱] 方塊中，輸入 `TypeEquivalenceClient` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7a290-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="7a290-201">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="7a290-201">The new project is created.</span></span>  
  
3.  <span data-ttu-id="7a290-202">以滑鼠右鍵按一下 TypeEquivalenceClient 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="7a290-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="7a290-203">按一下 [編譯] 索引標籤。將輸出路徑設為您在 TypeEquivalenceInterface 專案中使用的相同位置，例如 `C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="7a290-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="7a290-204">以滑鼠右鍵按一下 TypeEquivalenceClient 專案，然後按一下 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="7a290-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="7a290-205">按一下 [瀏覽] 索引標籤，並瀏覽至輸出路徑資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a290-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="7a290-206">選取 TypeEquivalenceInterface.dll 檔案 (而不是 TypeEquivalenceRuntime.dll)，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="7a290-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="7a290-207">在 [專案] 功能表上，按一下 [顯示所有檔案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-207">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="7a290-208">展開方案總管中的 [參考] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7a290-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="7a290-209">選取 TypeEquivalenceInterface 參考。</span><span class="sxs-lookup"><span data-stu-id="7a290-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="7a290-210">在 TypeEquivalenceInterface 參考的 [屬性] 視窗中，將 [內嵌 Interop 類型] 屬性設為 [True]。</span><span class="sxs-lookup"><span data-stu-id="7a290-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="7a290-211">將下列程式碼加入至要建立用戶端程式的 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="7a290-211">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
    ```vb  
    Imports TypeEquivalenceInterface  
    Imports System.Reflection  
  
    Module Module1  
  
        Sub Main()  
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")  
            Dim sampleClass As ISampleInterface = CType( _  
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)  
            sampleClass.GetUserInput()  
            Console.WriteLine(sampleClass.UserInput)  
            Console.WriteLine(sampleAssembly.GetName().Version)  
            Console.ReadLine()  
        End Sub  
  
    End Module  
    ```  
  
8.  <span data-ttu-id="7a290-212">按 CTRL+F5 建置並執行程式。</span><span class="sxs-lookup"><span data-stu-id="7a290-212">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="7a290-213">修改介面</span><span class="sxs-lookup"><span data-stu-id="7a290-213">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="7a290-214">若要修改介面</span><span class="sxs-lookup"><span data-stu-id="7a290-214">To modify the interface</span></span>  
  
1.  <span data-ttu-id="7a290-215">在 Visual Studio 的 [檔案] 功能表上，指向 [開啟]，然後按一下 [專案/方案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="7a290-216">在 [開啟] 對話方塊中，以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="7a290-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="7a290-217">按一下 [應用程式]  索引標籤。按一下 [組件資訊] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a290-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="7a290-218">將 [組件版本] 和 [檔案版本] 的值變更為 `2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="7a290-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="7a290-219">開啟 ISampleInterface.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="7a290-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="7a290-220">將下列程式碼行加入 ISampleInterface 介面。</span><span class="sxs-lookup"><span data-stu-id="7a290-220">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     <span data-ttu-id="7a290-221">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="7a290-221">Save the file.</span></span>  
  
4.  <span data-ttu-id="7a290-222">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="7a290-222">Save the project.</span></span>  
  
5.  <span data-ttu-id="7a290-223">以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="7a290-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="7a290-224">即會編譯新版本的類別庫 .dll 檔案，並將其儲存在指定的建置輸出路徑中 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="7a290-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="7a290-225">修改執行階段類別</span><span class="sxs-lookup"><span data-stu-id="7a290-225">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="7a290-226">若要修改執行階段類別</span><span class="sxs-lookup"><span data-stu-id="7a290-226">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="7a290-227">在 Visual Studio 的 [檔案] 功能表上，指向 [開啟]，然後按一下 [專案/方案]。</span><span class="sxs-lookup"><span data-stu-id="7a290-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="7a290-228">在 [開啟] 對話方塊中，以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="7a290-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="7a290-229">按一下 [應用程式]  索引標籤。按一下 [組件資訊] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a290-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="7a290-230">將 [組件版本] 和 [檔案版本] 的值變更為 `2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="7a290-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="7a290-231">開啟 SampleClass.vbfile。</span><span class="sxs-lookup"><span data-stu-id="7a290-231">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="7a290-232">將下列幾行程式碼加入 SampleClass 類別。</span><span class="sxs-lookup"><span data-stu-id="7a290-232">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="7a290-233">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="7a290-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="7a290-234">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="7a290-234">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="7a290-235">即會編譯更新版本的類別庫 .dll 檔案，並將其儲存在之前指定的建置輸出路徑中 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="7a290-235">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="7a290-236">在檔案總管中，開啟輸出路徑資料夾 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="7a290-236">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="7a290-237">按兩下 TypeEquivalenceClient.exe 以執行程式。</span><span class="sxs-lookup"><span data-stu-id="7a290-237">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="7a290-238">程式即會反映新版本的 TypeEquivalenceRuntime 組件，而不需重新編譯。</span><span class="sxs-lookup"><span data-stu-id="7a290-238">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a290-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a290-239">See Also</span></span>  
 [<span data-ttu-id="7a290-240">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a290-240">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [<span data-ttu-id="7a290-241">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="7a290-241">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="7a290-242">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="7a290-242">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="7a290-243">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a290-243">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
