---
title: "逐步解說︰ 從內嵌類型 Managed 組件，在 Visual Studio (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: adc58e081cd9b874a841d84b11d92cbffb6ba6b8
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="6be6f-102">逐步解說︰ 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型</span><span class="sxs-lookup"><span data-stu-id="6be6f-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="6be6f-103">內嵌強式名稱的 managed 組件的類型資訊時，您可以鬆散結合達成版本獨立應用程式中的型別。</span><span class="sxs-lookup"><span data-stu-id="6be6f-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="6be6f-104">也就是您的程式可以寫入使用 managed 程式庫的多個版本的型別，而不需重新編譯每個版本。</span><span class="sxs-lookup"><span data-stu-id="6be6f-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="6be6f-105">使用 COM interop，例如從 Microsoft Office 使用 automation 物件的應用程式經常使用內嵌型別。</span><span class="sxs-lookup"><span data-stu-id="6be6f-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="6be6f-106">內嵌類型資訊，可讓相同組建的程式以使用不同版本的 Microsoft Office 的不同電腦上。</span><span class="sxs-lookup"><span data-stu-id="6be6f-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="6be6f-107">不過，您也可以使用內嵌的完全受管理的解決方案類型。</span><span class="sxs-lookup"><span data-stu-id="6be6f-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="6be6f-108">可以具有下列特性的組件內嵌類型資訊︰</span><span class="sxs-lookup"><span data-stu-id="6be6f-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="6be6f-109">組件會公開一個以上的公用介面。</span><span class="sxs-lookup"><span data-stu-id="6be6f-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="6be6f-110">內嵌的介面必須標註`ComImport`屬性和`Guid`屬性 （和唯一的 GUID）。</span><span class="sxs-lookup"><span data-stu-id="6be6f-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="6be6f-111">組件以註解`ImportedFromTypeLib`屬性或`PrimaryInteropAssembly`屬性及組件層級`Guid`屬性。</span><span class="sxs-lookup"><span data-stu-id="6be6f-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="6be6f-112">(根據預設，Visual Basic 專案範本會包含組件層級`Guid`屬性。)</span><span class="sxs-lookup"><span data-stu-id="6be6f-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="6be6f-113">指定可內嵌的公用介面之後，您可以建立實作這些介面的執行階段類別。</span><span class="sxs-lookup"><span data-stu-id="6be6f-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="6be6f-114">用戶端程式由參考該組件包含的公用介面和設定，然後內嵌這些介面的型別資訊，在設計階段`Embed Interop Types`屬性參考的`True`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="6be6f-115">這相當於使用命令列編譯器，並使用參考組件`/link`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="6be6f-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="6be6f-116">用戶端程式可以載入執行階段物件的型別為介面的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6be6f-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="6be6f-117">如果您建立強式名稱的執行階段組件的新版本時，用戶端程式沒有更新的執行階段組件重新編譯。</span><span class="sxs-lookup"><span data-stu-id="6be6f-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="6be6f-118">相反地，用戶端程式會繼續使用執行階段組件的任何版本都提供，針對公用介面使用內嵌的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="6be6f-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="6be6f-119">因為內嵌類型的主要功能是支援的 COM interop 組件的類型資訊內嵌，當您將類型資訊內嵌在完全受管理的解決方案，也會套用下列限制︰</span><span class="sxs-lookup"><span data-stu-id="6be6f-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="6be6f-120">只有屬性特定 COM interop 會內嵌。其他屬性都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6be6f-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="6be6f-121">如果型別會使用泛用參數的泛型參數的型別是內嵌的型別，該類型不能跨組件界限。</span><span class="sxs-lookup"><span data-stu-id="6be6f-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="6be6f-122">組件界限的範例包括從另一個組件呼叫方法，或從型別衍生型別定義於另一個組件。</span><span class="sxs-lookup"><span data-stu-id="6be6f-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="6be6f-123">常數不會內嵌。</span><span class="sxs-lookup"><span data-stu-id="6be6f-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="6be6f-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>類別不支援內嵌的型別做為索引鍵。</xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6be6f-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> class does not support an embedded type as a key.</span></span> <span data-ttu-id="6be6f-125">您可以實作自己的字典類型，以支援做為索引鍵為內嵌的類型。</span><span class="sxs-lookup"><span data-stu-id="6be6f-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="6be6f-126">在本逐步解說中，您將會執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="6be6f-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="6be6f-127">建立強式名稱組件具有公用的介面，其中包含可內嵌類型資訊。</span><span class="sxs-lookup"><span data-stu-id="6be6f-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="6be6f-128">建立強式名稱的執行階段組件實作的公用介面。</span><span class="sxs-lookup"><span data-stu-id="6be6f-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="6be6f-129">建立用戶端程式內嵌的公用介面的型別資訊，從執行階段組件建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6be6f-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="6be6f-130">修改並重新建置執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="6be6f-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="6be6f-131">若要查看新版本的執行階段組件，而無須重新編譯用戶端程式正在使用用戶端程式執行。</span><span class="sxs-lookup"><span data-stu-id="6be6f-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="6be6f-132">建立介面</span><span class="sxs-lookup"><span data-stu-id="6be6f-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="6be6f-133">若要建立類型等價介面專案</span><span class="sxs-lookup"><span data-stu-id="6be6f-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="6be6f-134">在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6be6f-135">在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。</span><span class="sxs-lookup"><span data-stu-id="6be6f-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6be6f-136">選取**類別庫**中**範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="6be6f-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="6be6f-137">在**名稱**方塊中，輸入`TypeEquivalenceInterface`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="6be6f-138">建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="6be6f-139">在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="6be6f-140">若要將檔案重新命名`ISampleInterface.vb`按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="6be6f-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="6be6f-141">重新命名檔案也會重新命名類別來`ISampleInterface`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="6be6f-142">這個類別將代表類別的公用介面。</span><span class="sxs-lookup"><span data-stu-id="6be6f-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="6be6f-143">TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="6be6f-144">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6be6f-144">Click the **Compile** tab.</span></span> <span data-ttu-id="6be6f-145">輸出路徑設定有效的位置，在開發電腦，例如`C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-145">Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="6be6f-146">此位置也會用於在此逐步解說稍後的步驟。</span><span class="sxs-lookup"><span data-stu-id="6be6f-146">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="6be6f-147">仍在編輯專案屬性，然後按一下**簽署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6be6f-147">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="6be6f-148">選取**簽署組件**選項。</span><span class="sxs-lookup"><span data-stu-id="6be6f-148">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="6be6f-149">在**選擇強式名稱金鑰檔**清單中，按一下** <New...> **。</New...></span><span class="sxs-lookup"><span data-stu-id="6be6f-149">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="6be6f-150">在**金鑰檔名稱**方塊中，輸入`key.snk`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-150">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="6be6f-151">清除**保護我的密碼金鑰檔**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6be6f-151">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="6be6f-152">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="6be6f-152">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6be6f-153">開啟 ISampleInterface.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-153">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="6be6f-154">若要建立 ISampleInterface 介面 ISampleInterface 類別檔案中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6be6f-154">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
<span data-ttu-id="6be6f-155"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6be6f-155"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
7.  <span data-ttu-id="6be6f-156">在**工具**] 功能表上，按一下 [**建立 Guid**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-156">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="6be6f-157">在**建立 GUID**對話方塊中，按一下 **登錄格式**然後按一下 **複製**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-157">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="6be6f-158">按一下 [結束] ****。</span><span class="sxs-lookup"><span data-stu-id="6be6f-158">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="6be6f-159">在`Guid`屬性、 刪除範例 GUID，然後貼上您所複製的 GUID**建立 GUID**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6be6f-159">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="6be6f-160">移除大括號 （{}） 從已複製的 GUID。</span><span class="sxs-lookup"><span data-stu-id="6be6f-160">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="6be6f-161">在**專案**] 功能表上，按一下 [**顯示所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-161">On the **Project** menu, click **Show All Files**.</span></span>  
  
10. <span data-ttu-id="6be6f-162">在**方案總管 中**，依序展開**我的專案**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6be6f-162">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="6be6f-163">按兩下 AssemblyInfo.vb。</span><span class="sxs-lookup"><span data-stu-id="6be6f-163">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="6be6f-164">將下列屬性加入至檔案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-164">Add the following attribute to the file.</span></span>  
  
<span data-ttu-id="6be6f-165"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6be6f-165"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="6be6f-166">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-166">Save the file.</span></span>  
  
11. <span data-ttu-id="6be6f-167">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-167">Save the project.</span></span>  
  
12. <span data-ttu-id="6be6f-168">TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-168">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="6be6f-169">編譯並儲存至指定的組建輸出路徑 (例如，C:\TypeEquivalenceSample) 類別庫.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-169">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="6be6f-170">建立執行階段類別</span><span class="sxs-lookup"><span data-stu-id="6be6f-170">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="6be6f-171">若要建立類型等價執行階段專案</span><span class="sxs-lookup"><span data-stu-id="6be6f-171">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="6be6f-172">在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-172">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6be6f-173">在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。</span><span class="sxs-lookup"><span data-stu-id="6be6f-173">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6be6f-174">選取**類別庫**中**範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="6be6f-174">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="6be6f-175">在**名稱**方塊中，輸入`TypeEquivalenceRuntime`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-175">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="6be6f-176">建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-176">The new project is created.</span></span>  
  
3.  <span data-ttu-id="6be6f-177">在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-177">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="6be6f-178">若要將檔案重新命名`SampleClass.vb`按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="6be6f-178">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="6be6f-179">重新命名檔案也會重新命名類別來`SampleClass`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-179">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="6be6f-180">這個類別會實作`ISampleInterface`介面。</span><span class="sxs-lookup"><span data-stu-id="6be6f-180">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="6be6f-181">TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-181">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="6be6f-182">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6be6f-182">Click the **Compile** tab.</span></span> <span data-ttu-id="6be6f-183">輸出路徑設定為相同的位置，例如，在 TypeEquivalenceInterface 專案中，使用`C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-183">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="6be6f-184">仍在編輯專案屬性，然後按一下**簽署** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6be6f-184">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="6be6f-185">選取**簽署組件**選項。</span><span class="sxs-lookup"><span data-stu-id="6be6f-185">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="6be6f-186">在**選擇強式名稱金鑰檔**清單中，按一下** <New...> **。</New...></span><span class="sxs-lookup"><span data-stu-id="6be6f-186">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="6be6f-187">在**金鑰檔名稱**方塊中，輸入`key.snk`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-187">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="6be6f-188">清除**保護我的密碼金鑰檔**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6be6f-188">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="6be6f-189">按一下 [確定]****。</span><span class="sxs-lookup"><span data-stu-id="6be6f-189">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="6be6f-190">TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-190">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="6be6f-191">按一下 **瀏覽** 索引標籤上，瀏覽至 輸出路徑資料夾。</span><span class="sxs-lookup"><span data-stu-id="6be6f-191">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="6be6f-192">選取 TypeEquivalenceInterface.dll 檔案，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-192">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="6be6f-193">在**專案**] 功能表上，按一下 [**顯示所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-193">On the **Project** menu, click **Show All Files**.</span></span>  
  
8.  <span data-ttu-id="6be6f-194">在**方案總管 中**，依序展開**參考**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6be6f-194">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="6be6f-195">選取 TypeEquivalenceInterface 參考。</span><span class="sxs-lookup"><span data-stu-id="6be6f-195">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="6be6f-196">TypeEquivalenceInterface 參考的 [屬性] 視窗中設定**特定版本**屬性**False**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-196">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
9. <span data-ttu-id="6be6f-197">若要建立 SampleClass 類別 SampleClass 類別檔案中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6be6f-197">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
<span data-ttu-id="6be6f-198"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6be6f-198"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
10. <span data-ttu-id="6be6f-199">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-199">Save the project.</span></span>  
  
11. <span data-ttu-id="6be6f-200">TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-200">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="6be6f-201">編譯並儲存至指定的組建輸出路徑 (例如，C:\TypeEquivalenceSample) 類別庫.dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-201">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="6be6f-202">建立用戶端專案</span><span class="sxs-lookup"><span data-stu-id="6be6f-202">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="6be6f-203">若要建立類型等價的用戶端專案</span><span class="sxs-lookup"><span data-stu-id="6be6f-203">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="6be6f-204">在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-204">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6be6f-205">在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。</span><span class="sxs-lookup"><span data-stu-id="6be6f-205">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="6be6f-206">選取**主控台應用程式**中**範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="6be6f-206">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="6be6f-207">在**名稱**方塊中，輸入`TypeEquivalenceClient`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-207">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="6be6f-208">建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-208">The new project is created.</span></span>  
  
3.  <span data-ttu-id="6be6f-209">TypeEquivalenceClient 專案上按一下滑鼠右鍵，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-209">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="6be6f-210">按一下 [編譯]**** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6be6f-210">Click the **Compile** tab.</span></span> <span data-ttu-id="6be6f-211">輸出路徑設定為相同的位置，例如，在 TypeEquivalenceInterface 專案中，使用`C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-211">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="6be6f-212">TypeEquivalenceClient 專案上按一下滑鼠右鍵，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-212">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="6be6f-213">按一下 **瀏覽** 索引標籤上，瀏覽至 輸出路徑資料夾。</span><span class="sxs-lookup"><span data-stu-id="6be6f-213">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="6be6f-214">選取 TypeEquivalenceInterface.dll 檔案 (不 TypeEquivalenceRuntime.dll)，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-214">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="6be6f-215">在**專案**] 功能表上，按一下 [**顯示所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-215">On the **Project** menu, click **Show All Files**.</span></span>  
  
6.  <span data-ttu-id="6be6f-216">在**方案總管 中**，依序展開**參考**資料夾。</span><span class="sxs-lookup"><span data-stu-id="6be6f-216">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="6be6f-217">選取 TypeEquivalenceInterface 參考。</span><span class="sxs-lookup"><span data-stu-id="6be6f-217">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="6be6f-218">TypeEquivalenceInterface 參考的 [屬性] 視窗中設定**內嵌 Interop 類型**屬性**True**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-218">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
7.  <span data-ttu-id="6be6f-219">若要建立用戶端程式 Module1.vb 檔案中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6be6f-219">Add the following code to the Module1.vb file to create the client program.</span></span>  
  
<span data-ttu-id="6be6f-220"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6be6f-220"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
8.  <span data-ttu-id="6be6f-221">按 CTRL + F5 以建置並執行程式。</span><span class="sxs-lookup"><span data-stu-id="6be6f-221">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="6be6f-222">修改介面</span><span class="sxs-lookup"><span data-stu-id="6be6f-222">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="6be6f-223">若要修改的介面</span><span class="sxs-lookup"><span data-stu-id="6be6f-223">To modify the interface</span></span>  
  
1.  <span data-ttu-id="6be6f-224">在 Visual Studio 中，在**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-224">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="6be6f-225">在**開啟專案**對話方塊中，TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-225">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="6be6f-226">按一下 [應用程式] **** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6be6f-226">Click the **Application** tab.</span></span> <span data-ttu-id="6be6f-227">按一下 [**組件資訊**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6be6f-227">Click the **Assembly Information** button.</span></span> <span data-ttu-id="6be6f-228">變更**組件版本**和**檔案版本**值`2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-228">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="6be6f-229">開啟 ISampleInterface.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-229">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="6be6f-230">將下列程式碼行加入至 ISampleInterface 介面。</span><span class="sxs-lookup"><span data-stu-id="6be6f-230">Add the following line of code to the ISampleInterface interface.</span></span>  
  
<span data-ttu-id="6be6f-231"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="6be6f-231"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="6be6f-232">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-232">Save the file.</span></span>  
  
4.  <span data-ttu-id="6be6f-233">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-233">Save the project.</span></span>  
  
5.  <span data-ttu-id="6be6f-234">TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-234">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="6be6f-235">編譯並儲存在指定的組建輸出路徑 (例如，C:\TypeEquivalenceSample) 中的類別庫.dll 檔案的新版本。</span><span class="sxs-lookup"><span data-stu-id="6be6f-235">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="6be6f-236">修改執行階段類別</span><span class="sxs-lookup"><span data-stu-id="6be6f-236">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="6be6f-237">若要修改執行階段類別</span><span class="sxs-lookup"><span data-stu-id="6be6f-237">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="6be6f-238">在 Visual Studio 中，在**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-238">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="6be6f-239">在**開啟專案** 對話方塊，以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-239">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="6be6f-240">按一下 [應用程式] **** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6be6f-240">Click the **Application** tab.</span></span> <span data-ttu-id="6be6f-241">按一下 [**組件資訊**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6be6f-241">Click the **Assembly Information** button.</span></span> <span data-ttu-id="6be6f-242">變更**組件版本**和**檔案版本**值`2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="6be6f-242">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="6be6f-243">開啟 SampleClass.vbfile。</span><span class="sxs-lookup"><span data-stu-id="6be6f-243">Open the SampleClass.vbfile.</span></span> <span data-ttu-id="6be6f-244">將下列程式碼行加入至 SampleClass 類別。</span><span class="sxs-lookup"><span data-stu-id="6be6f-244">Add the following lines of code to the SampleClass class.</span></span>  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  <span data-ttu-id="6be6f-245">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="6be6f-245">Save the project.</span></span>  
  
5.  <span data-ttu-id="6be6f-246">TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="6be6f-246">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="6be6f-247">編譯並儲存在先前指定的建置輸出路徑 (例如，C:\TypeEquivalenceSample) 類別庫.dll 檔案的更新的版本。</span><span class="sxs-lookup"><span data-stu-id="6be6f-247">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="6be6f-248">在 檔案總管 中，開啟 輸出路徑資料夾 (例如，C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="6be6f-248">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="6be6f-249">按兩下 TypeEquivalenceClient.exe 執行程式。</span><span class="sxs-lookup"><span data-stu-id="6be6f-249">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="6be6f-250">程式將會反映 TypeEquivalenceRuntime 組件的新版本，而不需重新編譯。</span><span class="sxs-lookup"><span data-stu-id="6be6f-250">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be6f-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6be6f-251">See Also</span></span>  
 <span data-ttu-id="6be6f-252">[/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md) </span><span class="sxs-lookup"><span data-stu-id="6be6f-252">[/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md) </span></span>  
<span data-ttu-id="6be6f-253"> [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="6be6f-253"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="6be6f-254"> [使用組件設計程式](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) </span><span class="sxs-lookup"><span data-stu-id="6be6f-254"> [Programming with Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) </span></span>  
<span data-ttu-id="6be6f-255"> [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="6be6f-255"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>

