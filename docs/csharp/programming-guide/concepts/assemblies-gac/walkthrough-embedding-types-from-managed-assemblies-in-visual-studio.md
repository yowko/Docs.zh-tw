---
title: "逐步解說：在 Visual Studio 中內嵌來自 Managed 組件的型別 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7b003e76229a06883adc22f933f08663330f0c9d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-c"></a><span data-ttu-id="9f371-102">逐步解說：在 Visual Studio 中內嵌來自 Managed 組件的型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="9f371-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="9f371-103">若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。</span><span class="sxs-lookup"><span data-stu-id="9f371-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="9f371-104">也就是說，您可以撰寫程式來使用 Managed 程式庫多個版本的類型，而不需重新編譯每個版本。</span><span class="sxs-lookup"><span data-stu-id="9f371-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>  
  
 <span data-ttu-id="9f371-105">內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。</span><span class="sxs-lookup"><span data-stu-id="9f371-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="9f371-106">當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="9f371-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="9f371-107">不過，您也可以搭配使用類型內嵌功能與完全受管理的解決方案。</span><span class="sxs-lookup"><span data-stu-id="9f371-107">However, you can also use type embedding with a fully managed solution.</span></span>  
  
 <span data-ttu-id="9f371-108">您可以透過組件來內嵌具有下列特性的類型資訊：</span><span class="sxs-lookup"><span data-stu-id="9f371-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="9f371-109">組件已公開至少一個公用介面。</span><span class="sxs-lookup"><span data-stu-id="9f371-109">The assembly exposes at least one public interface.</span></span>  
  
-   <span data-ttu-id="9f371-110">內嵌的介面已標註 `ComImport` 屬性和 `Guid` 屬性 (以及唯一 GUID)。</span><span class="sxs-lookup"><span data-stu-id="9f371-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>  
  
-   <span data-ttu-id="9f371-111">您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件 </span><span class="sxs-lookup"><span data-stu-id="9f371-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="9f371-112">(Visual C# 專案範本預設會包含組件層級 `Guid` 屬性)。</span><span class="sxs-lookup"><span data-stu-id="9f371-112">(By default, Visual C# project templates include an assembly-level `Guid` attribute.)</span></span>  
  
 <span data-ttu-id="9f371-113">指定可內嵌的公用介面之後，您可以建立執行階段類別以實作這些介面。</span><span class="sxs-lookup"><span data-stu-id="9f371-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="9f371-114">接著，用戶端程式即會參考包含公用介面的組件，然後將參考的 `Embed Interop Types` 屬性設為 `True`，以在設計階段內嵌這些介面的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="9f371-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="9f371-115">這相當於使用命令列編譯器，並使用 `/link` 編譯器選項來參考組件。</span><span class="sxs-lookup"><span data-stu-id="9f371-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="9f371-116">用戶端程式即可載入以這些介面為類型的執行階段物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f371-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="9f371-117">如果您建立新版本的強式名稱執行階段組件，用戶端程式就不需要使用更新的執行階段組件來重新編譯。</span><span class="sxs-lookup"><span data-stu-id="9f371-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="9f371-118">相反地，用戶端程式會繼續使用執行階段組件適用的任何版本，並針對公用介面使用內嵌的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="9f371-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>  
  
 <span data-ttu-id="9f371-119">由於類型內嵌的主要功能是支援透過 COM Interop 組件進行類型資訊內嵌，因此當您將類型資訊內嵌在完全受管理的解決方案中時，也會套用下列限制：</span><span class="sxs-lookup"><span data-stu-id="9f371-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>  
  
-   <span data-ttu-id="9f371-120">只會內嵌 COM Interop 專屬的屬性，而忽略其他屬性。</span><span class="sxs-lookup"><span data-stu-id="9f371-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>  
  
-   <span data-ttu-id="9f371-121">如果某類型使用泛型參數，而該泛型參數的類型是內嵌的類型，您就不能跨組件界限使用此類型。</span><span class="sxs-lookup"><span data-stu-id="9f371-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="9f371-122">跨組件界限的範例包括從其他組件呼叫方法，或透過定義於其他組件上的類型來衍生類型。</span><span class="sxs-lookup"><span data-stu-id="9f371-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>  
  
-   <span data-ttu-id="9f371-123">系統不會內嵌常數。</span><span class="sxs-lookup"><span data-stu-id="9f371-123">Constants are not embedded.</span></span>  
  
-   <span data-ttu-id="9f371-124"><xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> 類別不支援內嵌類型作為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9f371-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> class does not support an embedded type as a key.</span></span> <span data-ttu-id="9f371-125">您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。</span><span class="sxs-lookup"><span data-stu-id="9f371-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>  
  
 <span data-ttu-id="9f371-126">在這個逐步解說中，您將進行下列工作：</span><span class="sxs-lookup"><span data-stu-id="9f371-126">In this walkthrough, you will do the following:</span></span>  
  
-   <span data-ttu-id="9f371-127">建立具有公用介面的強式名稱組件，且該介面包含可內嵌的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="9f371-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>  
  
-   <span data-ttu-id="9f371-128">建立強式名稱的執行階段組件，以實作上述公用介面。</span><span class="sxs-lookup"><span data-stu-id="9f371-128">Create a strong-named runtime assembly that implements that public interface.</span></span>  
  
-   <span data-ttu-id="9f371-129">建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9f371-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>  
  
-   <span data-ttu-id="9f371-130">修改並重新建置執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="9f371-130">Modify and rebuild the runtime assembly.</span></span>  
  
-   <span data-ttu-id="9f371-131">執行用戶端程式，查看是否正在使用新版本的執行階段組件，而不必重新編譯用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="9f371-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a><span data-ttu-id="9f371-132">建立介面</span><span class="sxs-lookup"><span data-stu-id="9f371-132">Creating an Interface</span></span>  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="9f371-133">若要建立類型等價介面專案</span><span class="sxs-lookup"><span data-stu-id="9f371-133">To create the type equivalence interface project</span></span>  
  
1.  <span data-ttu-id="9f371-134">在 Visual Studio 的 [檔案] 功能表上，選擇 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="9f371-134">In Visual Studio, on the **File** menu, choose **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="9f371-135">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="9f371-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="9f371-136">在 [範本] 窗格中，選取 [類別庫]。</span><span class="sxs-lookup"><span data-stu-id="9f371-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="9f371-137">在 [名稱] 方塊中，輸入 `TypeEquivalenceInterface` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9f371-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="9f371-138">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="9f371-138">The new project is created.</span></span>  
  
3.  <span data-ttu-id="9f371-139">在方案總管中，以滑鼠右鍵按一下 Class1.cs 檔案，然後按一下 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="9f371-139">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="9f371-140">將檔案重新命名為 `ISampleInterface.cs`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="9f371-140">Rename the file to `ISampleInterface.cs` and press ENTER.</span></span> <span data-ttu-id="9f371-141">重新命名檔案時，也會將類別重新命名為 `ISampleInterface`。</span><span class="sxs-lookup"><span data-stu-id="9f371-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="9f371-142">這個類別將代表類別的公用介面。</span><span class="sxs-lookup"><span data-stu-id="9f371-142">This class will represent the public interface for the class.</span></span>  
  
4.  <span data-ttu-id="9f371-143">以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9f371-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="9f371-144">按一下 [建置] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9f371-144">Click the the **Build** tab.</span></span> <span data-ttu-id="9f371-145">將輸出路徑設為開發電腦上的有效位置，例如 `C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="9f371-145">Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="9f371-146">這個位置也會用於本逐步解說稍後的步驟。</span><span class="sxs-lookup"><span data-stu-id="9f371-146">This location will also be used in a later step in this walkthrough.</span></span>  
  
5.  <span data-ttu-id="9f371-147">在編輯專案屬性期間，按一下 [簽署] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9f371-147">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="9f371-148">選取 [簽署組件] 選項。</span><span class="sxs-lookup"><span data-stu-id="9f371-148">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="9f371-149">在 [選擇強式名稱金鑰檔案] 清單中，按一下 [<新增...>]。</span><span class="sxs-lookup"><span data-stu-id="9f371-149">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="9f371-150">在 [金鑰檔案名稱] 方塊中，輸入 `key.snk`。</span><span class="sxs-lookup"><span data-stu-id="9f371-150">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="9f371-151">清除 [以密碼保護我的金鑰檔] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9f371-151">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="9f371-152">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9f371-152">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="9f371-153">開啟 ISampleInterface.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="9f371-153">Open the ISampleInterface.cs file.</span></span> <span data-ttu-id="9f371-154">將下列程式碼加入 ISampleInterface 類別檔案，以建立 ISampleInterface 介面。</span><span class="sxs-lookup"><span data-stu-id="9f371-154">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
  
    namespace TypeEquivalenceInterface  
    {  
        [ComImport]  
        [Guid("8DA56996-A151-4136-B474-32784559F6DF")]  
        public interface ISampleInterface  
        {  
            void GetUserInput();  
            string UserInput { get; }  
        }  
    }  
    ```  
  
7.  <span data-ttu-id="9f371-155">在 [工具] 功能表上，按一下 [建立 GUID]。</span><span class="sxs-lookup"><span data-stu-id="9f371-155">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="9f371-156">在 [建立 GUID] 對話方塊中，依序按一下 [登錄格式] 和 [複製]。</span><span class="sxs-lookup"><span data-stu-id="9f371-156">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="9f371-157">按一下 [結束] 。</span><span class="sxs-lookup"><span data-stu-id="9f371-157">Click **Exit**.</span></span>  
  
8.  <span data-ttu-id="9f371-158">刪除 `Guid` 屬性中的範例 GUID，然後貼上您從 [建立 GUID] 對話方塊所複製的 GUID。</span><span class="sxs-lookup"><span data-stu-id="9f371-158">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="9f371-159">移除已複製 GUID 的大括號 ({})。</span><span class="sxs-lookup"><span data-stu-id="9f371-159">Remove the braces ({}) from the copied GUID.</span></span>  
  
9. <span data-ttu-id="9f371-160">展開方案總管中的 [屬性] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f371-160">In **Solution Explorer**, expand the **Properties** folder.</span></span> <span data-ttu-id="9f371-161">按兩下 AssemblyInfo.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="9f371-161">Double-click the AssemblyInfo.cs file.</span></span> <span data-ttu-id="9f371-162">將下列屬性加入檔案中。</span><span class="sxs-lookup"><span data-stu-id="9f371-162">Add the following attribute to the file.</span></span>  
  
    ```csharp  
    [assembly: ImportedFromTypeLib("")]  
    ```  
  
     <span data-ttu-id="9f371-163">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9f371-163">Save the file.</span></span>  
  
10. <span data-ttu-id="9f371-164">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="9f371-164">Save the project.</span></span>  
  
11. <span data-ttu-id="9f371-165">以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="9f371-165">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="9f371-166">即會編譯類別庫 .dll 檔案，並將其儲存至指定的建置輸出路徑 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="9f371-166">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-runtime-class"></a><span data-ttu-id="9f371-167">建立執行階段類別</span><span class="sxs-lookup"><span data-stu-id="9f371-167">Creating a Runtime Class</span></span>  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="9f371-168">若要建立類型等價執行階段專案</span><span class="sxs-lookup"><span data-stu-id="9f371-168">To create the type equivalence runtime project</span></span>  
  
1.  <span data-ttu-id="9f371-169">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="9f371-169">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="9f371-170">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="9f371-170">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="9f371-171">在 [範本] 窗格中，選取 [類別庫]。</span><span class="sxs-lookup"><span data-stu-id="9f371-171">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="9f371-172">在 [名稱] 方塊中，輸入 `TypeEquivalenceRuntime` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9f371-172">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="9f371-173">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="9f371-173">The new project is created.</span></span>  
  
3.  <span data-ttu-id="9f371-174">在方案總管中，以滑鼠右鍵按一下 Class1.cs 檔案，然後按一下 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="9f371-174">In **Solution Explorer**, right-click the Class1.cs file and click **Rename**.</span></span> <span data-ttu-id="9f371-175">將檔案重新命名為 `SampleClass.cs`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="9f371-175">Rename the file to `SampleClass.cs` and press ENTER.</span></span> <span data-ttu-id="9f371-176">重新命名檔案時，也會將類別重新命名為 `SampleClass`。</span><span class="sxs-lookup"><span data-stu-id="9f371-176">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="9f371-177">此類別會實作 `ISampleInterface` 介面。</span><span class="sxs-lookup"><span data-stu-id="9f371-177">This class will implement the `ISampleInterface` interface.</span></span>  
  
4.  <span data-ttu-id="9f371-178">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9f371-178">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="9f371-179">按一下 [建置] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9f371-179">Click the **Build** tab.</span></span> <span data-ttu-id="9f371-180">將輸出路徑設為您在 TypeEquivalenceInterface 專案中使用的相同位置，例如 `C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="9f371-180">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
5.  <span data-ttu-id="9f371-181">在編輯專案屬性期間，按一下 [簽署] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9f371-181">While still editing the project properties, click the **Signing** tab.</span></span> <span data-ttu-id="9f371-182">選取 [簽署組件] 選項。</span><span class="sxs-lookup"><span data-stu-id="9f371-182">Select the **Sign the assembly** option.</span></span> <span data-ttu-id="9f371-183">在 [選擇強式名稱金鑰檔案] 清單中，按一下 [<新增...>]。</span><span class="sxs-lookup"><span data-stu-id="9f371-183">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="9f371-184">在 [金鑰檔案名稱] 方塊中，輸入 `key.snk`。</span><span class="sxs-lookup"><span data-stu-id="9f371-184">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="9f371-185">清除 [以密碼保護我的金鑰檔] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9f371-185">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="9f371-186">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9f371-186">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="9f371-187">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="9f371-187">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="9f371-188">按一下 [瀏覽] 索引標籤，並瀏覽至輸出路徑資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f371-188">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="9f371-189">選取 TypeEquivalenceInterface.dll 檔案，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9f371-189">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>  
  
7.  <span data-ttu-id="9f371-190">展開方案總管中的 [參考] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f371-190">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="9f371-191">選取 TypeEquivalenceInterface 參考。</span><span class="sxs-lookup"><span data-stu-id="9f371-191">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="9f371-192">在 TypeEquivalenceInterface 參考的 [屬性] 視窗中，將 [特定版本] 屬性設為 [False]。</span><span class="sxs-lookup"><span data-stu-id="9f371-192">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>  
  
8.  <span data-ttu-id="9f371-193">將下列程式碼加入 SampleClass 類別檔案中，以建立 SampleClass 類別。</span><span class="sxs-lookup"><span data-stu-id="9f371-193">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
  
    namespace TypeEquivalenceRuntime  
    {  
        public class SampleClass : ISampleInterface  
        {  
            private string p_UserInput;  
            public string UserInput { get { return p_UserInput; } }  
  
            public void GetUserInput()  
            {  
                Console.WriteLine("Please enter a value:");  
                p_UserInput = Console.ReadLine();  
            }  
        }  
    )  
    ```  
  
9. <span data-ttu-id="9f371-194">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="9f371-194">Save the project.</span></span>  
  
10. <span data-ttu-id="9f371-195">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="9f371-195">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="9f371-196">即會編譯類別庫 .dll 檔案，並將其儲存至指定的建置輸出路徑 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="9f371-196">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="creating-a-client-project"></a><span data-ttu-id="9f371-197">建立用戶端專案</span><span class="sxs-lookup"><span data-stu-id="9f371-197">Creating a Client Project</span></span>  
  
#### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="9f371-198">若要建立類型等價用戶端專案</span><span class="sxs-lookup"><span data-stu-id="9f371-198">To create the type equivalence client project</span></span>  
  
1.  <span data-ttu-id="9f371-199">在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="9f371-199">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="9f371-200">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="9f371-200">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="9f371-201">選取 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="9f371-201">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="9f371-202">在 [名稱] 方塊中，輸入 `TypeEquivalenceClient` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9f371-202">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="9f371-203">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="9f371-203">The new project is created.</span></span>  
  
3.  <span data-ttu-id="9f371-204">以滑鼠右鍵按一下 TypeEquivalenceClient 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9f371-204">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="9f371-205">按一下 [建置] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9f371-205">Click the **Build** tab.</span></span> <span data-ttu-id="9f371-206">將輸出路徑設為您在 TypeEquivalenceInterface 專案中使用的相同位置，例如 `C:\TypeEquivalenceSample`。</span><span class="sxs-lookup"><span data-stu-id="9f371-206">Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>  
  
4.  <span data-ttu-id="9f371-207">以滑鼠右鍵按一下 TypeEquivalenceClient 專案，然後按一下 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="9f371-207">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="9f371-208">按一下 [瀏覽] 索引標籤，並瀏覽至輸出路徑資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f371-208">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="9f371-209">選取 TypeEquivalenceInterface.dll 檔案 (而不是 TypeEquivalenceRuntime.dll)，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9f371-209">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>  
  
5.  <span data-ttu-id="9f371-210">展開方案總管中的 [參考] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f371-210">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="9f371-211">選取 TypeEquivalenceInterface 參考。</span><span class="sxs-lookup"><span data-stu-id="9f371-211">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="9f371-212">在 TypeEquivalenceInterface 參考的 [屬性] 視窗中，將 [內嵌 Interop 類型] 屬性設為 [True]。</span><span class="sxs-lookup"><span data-stu-id="9f371-212">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>  
  
6.  <span data-ttu-id="9f371-213">將下列程式碼加入 Program.cs 檔案中，以建立用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="9f371-213">Add the following code to the Program.cs file to create the client program.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using TypeEquivalenceInterface;  
    using System.Reflection;  
  
    namespace TypeEquivalenceClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");  
                ISampleInterface sampleClass =   
                    (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");  
                sampleClass.GetUserInput();  
                Console.WriteLine(sampleClass.UserInput);  
                Console.WriteLine(sampleAssembly.GetName().Version.ToString());  
                Console.ReadLine();  
            }  
        }  
    }  
    ```  
  
7.  <span data-ttu-id="9f371-214">按 CTRL+F5 建置並執行程式。</span><span class="sxs-lookup"><span data-stu-id="9f371-214">Press CTRL+F5 to build and run the program.</span></span>  
  
## <a name="modifying-the-interface"></a><span data-ttu-id="9f371-215">修改介面</span><span class="sxs-lookup"><span data-stu-id="9f371-215">Modifying the Interface</span></span>  
  
#### <a name="to-modify-the-interface"></a><span data-ttu-id="9f371-216">若要修改介面</span><span class="sxs-lookup"><span data-stu-id="9f371-216">To modify the interface</span></span>  
  
1.  <span data-ttu-id="9f371-217">在 Visual Studio 的 [檔案] 功能表上，指向 [開啟]，然後按一下 [專案/方案]。</span><span class="sxs-lookup"><span data-stu-id="9f371-217">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="9f371-218">在 [開啟] 對話方塊中，以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9f371-218">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="9f371-219">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9f371-219">Click the **Application** tab.</span></span> <span data-ttu-id="9f371-220">按一下 [組件資訊] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9f371-220">Click the **Assembly Information** button.</span></span> <span data-ttu-id="9f371-221">將 [組件版本] 和 [檔案版本] 的值變更為 `2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="9f371-221">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="9f371-222">開啟 SampleInterface.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="9f371-222">Open the SampleInterface.cs file.</span></span> <span data-ttu-id="9f371-223">將下列程式碼行加入 ISampleInterface 介面。</span><span class="sxs-lookup"><span data-stu-id="9f371-223">Add the following line of code to the ISampleInterface interface.</span></span>  
  
    ```csharp  
    DateTime GetDate();  
    ```  
  
     <span data-ttu-id="9f371-224">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9f371-224">Save the file.</span></span>  
  
4.  <span data-ttu-id="9f371-225">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="9f371-225">Save the project.</span></span>  
  
5.  <span data-ttu-id="9f371-226">以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="9f371-226">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="9f371-227">即會編譯新版本的類別庫 .dll 檔案，並將其儲存在指定的建置輸出路徑中 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="9f371-227">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
## <a name="modifying-the-runtime-class"></a><span data-ttu-id="9f371-228">修改執行階段類別</span><span class="sxs-lookup"><span data-stu-id="9f371-228">Modifying the Runtime Class</span></span>  
  
#### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="9f371-229">若要修改執行階段類別</span><span class="sxs-lookup"><span data-stu-id="9f371-229">To modify the runtime class</span></span>  
  
1.  <span data-ttu-id="9f371-230">在 Visual Studio 的 [檔案] 功能表上，指向 [開啟]，然後按一下 [專案/方案]。</span><span class="sxs-lookup"><span data-stu-id="9f371-230">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
2.  <span data-ttu-id="9f371-231">在 [開啟] 對話方塊中，以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9f371-231">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="9f371-232">按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9f371-232">Click the **Application** tab.</span></span> <span data-ttu-id="9f371-233">按一下 [組件資訊] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9f371-233">Click the **Assembly Information** button.</span></span> <span data-ttu-id="9f371-234">將 [組件版本] 和 [檔案版本] 的值變更為 `2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="9f371-234">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>  
  
3.  <span data-ttu-id="9f371-235">開啟 SampleClass.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="9f371-235">Open the SampleClass.cs file.</span></span> <span data-ttu-id="9f371-236">將下列幾行程式碼加入 SampleClass 類別。</span><span class="sxs-lookup"><span data-stu-id="9f371-236">Add the following lines of code to the SampleClass class.</span></span>  
  
    ```csharp  
    public DateTime GetDate()  
    {  
        return DateTime.Now;  
    }  
    ```  
  
     <span data-ttu-id="9f371-237">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9f371-237">Save the file.</span></span>  
  
4.  <span data-ttu-id="9f371-238">儲存專案。</span><span class="sxs-lookup"><span data-stu-id="9f371-238">Save the project.</span></span>  
  
5.  <span data-ttu-id="9f371-239">以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="9f371-239">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="9f371-240">即會編譯更新版本的類別庫 .dll 檔案，並將其儲存在之前指定的建置輸出路徑中 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="9f371-240">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>  
  
6.  <span data-ttu-id="9f371-241">在檔案總管中，開啟輸出路徑資料夾 (例如 C:\TypeEquivalenceSample)。</span><span class="sxs-lookup"><span data-stu-id="9f371-241">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="9f371-242">按兩下 TypeEquivalenceClient.exe 以執行程式。</span><span class="sxs-lookup"><span data-stu-id="9f371-242">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="9f371-243">程式即會反映新版本的 TypeEquivalenceRuntime 組件，而不需重新編譯。</span><span class="sxs-lookup"><span data-stu-id="9f371-243">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f371-244">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f371-244">See Also</span></span>  
 <span data-ttu-id="9f371-245">[/link (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="9f371-245">[/link (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md) </span></span>  
 <span data-ttu-id="9f371-246">[C# 程式設計手冊](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f371-246">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9f371-247">[使用組件設計程式](../../../../framework/app-domains/programming-with-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="9f371-247">[Programming with Assemblies](../../../../framework/app-domains/programming-with-assemblies.md) </span></span>  
 [<span data-ttu-id="9f371-248">組件和全域組件快取 (C#)</span><span class="sxs-lookup"><span data-stu-id="9f371-248">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)

