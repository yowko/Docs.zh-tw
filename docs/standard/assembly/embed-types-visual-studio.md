---
title: 逐步解說：在 Visual Studio 中，從 managed 元件內嵌類型
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1f32bd840efa97b62097a2d051c25d519785b381
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973268"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="58c4a-102">逐步解說：在 Visual Studio 中，從 managed 元件內嵌類型</span><span class="sxs-lookup"><span data-stu-id="58c4a-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="58c4a-103">若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。</span><span class="sxs-lookup"><span data-stu-id="58c4a-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="58c4a-104">也就是說，您的程式可以撰寫成使用來自任何版本之 managed 程式庫的類型，而不需要針對每個新版本重新編譯。</span><span class="sxs-lookup"><span data-stu-id="58c4a-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="58c4a-105">內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。</span><span class="sxs-lookup"><span data-stu-id="58c4a-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="58c4a-106">當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="58c4a-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="58c4a-107">不過，您也可以將類型內嵌用於完全受控的解決方案。</span><span class="sxs-lookup"><span data-stu-id="58c4a-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="58c4a-108">在您指定可以內嵌的公用介面之後，就可以建立執行這些介面的執行時間類別。</span><span class="sxs-lookup"><span data-stu-id="58c4a-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="58c4a-109">用戶端程式可以藉由參考包含公用介面的元件，並將參考的`Embed Interop Types`屬性設定為`True`，在設計階段內嵌介面的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="58c4a-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="58c4a-110">然後，用戶端程式可以載入以這些介面類別型輸入之執行時間物件的實例。</span><span class="sxs-lookup"><span data-stu-id="58c4a-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="58c4a-111">這相當於使用命令列編譯器，並使用 `/link` 編譯器選項來參考組件。</span><span class="sxs-lookup"><span data-stu-id="58c4a-111">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> 

<span data-ttu-id="58c4a-112">如果您建立新版本的強式名稱執行時間元件，則不需要重新編譯用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="58c4a-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="58c4a-113">用戶端程式會繼續使用任何版本的執行時間元件，並使用公用介面的內嵌類型資訊。</span><span class="sxs-lookup"><span data-stu-id="58c4a-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="58c4a-114">在本逐步解說中, 您會:</span><span class="sxs-lookup"><span data-stu-id="58c4a-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="58c4a-115">建立具有公用介面的強式名稱元件，其中包含可內嵌的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="58c4a-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="58c4a-116">建立強式名稱的執行時間元件，以執行公用介面。</span><span class="sxs-lookup"><span data-stu-id="58c4a-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="58c4a-117">建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="58c4a-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="58c4a-118">修改並重新建置執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="58c4a-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="58c4a-119">執行用戶端程式，以查看它是否使用新版本的執行時間元件，而不需要重新編譯。</span><span class="sxs-lookup"><span data-stu-id="58c4a-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="58c4a-120">條件和限制</span><span class="sxs-lookup"><span data-stu-id="58c4a-120">Conditions and limitations</span></span>

<span data-ttu-id="58c4a-121">在下列情況下，您可以從元件內嵌類型資訊：</span><span class="sxs-lookup"><span data-stu-id="58c4a-121">You can embed type information from an assembly under the following conditions:</span></span> 

- <span data-ttu-id="58c4a-122">組件已公開至少一個公用介面。</span><span class="sxs-lookup"><span data-stu-id="58c4a-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="58c4a-123">內嵌的介面會以`ComImport`具有唯一 guid 的屬性和`Guid`屬性來標注。</span><span class="sxs-lookup"><span data-stu-id="58c4a-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="58c4a-124">您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件</span><span class="sxs-lookup"><span data-stu-id="58c4a-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="58c4a-125">根據預設C# ，視覺效果和 Visual Basic 專案範本包含元件`Guid`層級屬性。</span><span class="sxs-lookup"><span data-stu-id="58c4a-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="58c4a-126">因為內嵌類型的主要功能是支援 COM Interop 元件，所以當您在完全受控的方案中嵌入類型資訊時，會有下列限制：</span><span class="sxs-lookup"><span data-stu-id="58c4a-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="58c4a-127">僅內嵌 COM Interop 特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="58c4a-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="58c4a-128">其他屬性則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="58c4a-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="58c4a-129">如果類型使用泛型參數，且泛型參數的類型是內嵌類型，則該類型不能跨元件界限使用。</span><span class="sxs-lookup"><span data-stu-id="58c4a-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="58c4a-130">跨越元件界限的範例包括從另一個元件呼叫方法，或從另一個元件中定義的型別衍生型別。</span><span class="sxs-lookup"><span data-stu-id="58c4a-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="58c4a-131">系統不會內嵌常數。</span><span class="sxs-lookup"><span data-stu-id="58c4a-131">Constants are not embedded.</span></span>
- <span data-ttu-id="58c4a-132"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別不支援內嵌類型作為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="58c4a-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="58c4a-133">您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。</span><span class="sxs-lookup"><span data-stu-id="58c4a-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="58c4a-134">建立介面</span><span class="sxs-lookup"><span data-stu-id="58c4a-134">Create an interface</span></span>

<span data-ttu-id="58c4a-135">第一個步驟是建立類型等價介面元件。</span><span class="sxs-lookup"><span data-stu-id="58c4a-135">The first step is to create the type equivalence interface assembly.</span></span> 

1. <span data-ttu-id="58c4a-136">在 Visual Studio 中，選取 [檔案] > [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58c4a-137">在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*類別庫*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="58c4a-138">從清單中C#選取或 VB**類別庫（.NET Framework）** 範本，然後選取 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-138">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58c4a-139">在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceInterface*，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="58c4a-140">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="58c4a-140">The new project is created.</span></span>
   
1. <span data-ttu-id="58c4a-141">在**方案總管**中，以滑鼠右鍵按一下*Class1.cs*或*Class1*檔案，選取 [**重新命名**]，然後將檔案從*Class1*重新命名為*ISampleInterface*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="58c4a-142">在提示中回應 **[是]** ，也會將`ISampleInterface`類別重新命名為。</span><span class="sxs-lookup"><span data-stu-id="58c4a-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="58c4a-143">此類別代表類別的公用介面。</span><span class="sxs-lookup"><span data-stu-id="58c4a-143">This class represents the public interface for the class.</span></span>
   
1. <span data-ttu-id="58c4a-144">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span> 
   
1. <span data-ttu-id="58c4a-145">在 [**屬性**] 畫面的左窗格中選取 [**建立**]，並將**輸出路徑**設定為您電腦上的位置，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="58c4a-146">在本逐步解說中，您會使用相同的位置。</span><span class="sxs-lookup"><span data-stu-id="58c4a-146">You use the same location throughout this walkthrough.</span></span> 
   
1. <span data-ttu-id="58c4a-147">在 [**屬性**] 畫面的左窗格中選取 [**簽署**]，然後選取 [**簽署元件**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="58c4a-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="58c4a-148">在 **[選擇強式名稱金鑰**檔] 的下拉式清單中，選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="58c4a-149">在 [**建立強式名稱金鑰**] 對話方塊中的 [**金鑰檔名稱**] 下，輸入 [*金鑰 .snk*]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="58c4a-150">取消選取 [**以密碼保護我的金鑰**檔] 核取方塊，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58c4a-151">在程式碼編輯器中開啟*ISampleInterface*類別檔案，並以下列程式碼取代其內容以建立`ISampleInterface`介面：</span><span class="sxs-lookup"><span data-stu-id="58c4a-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>
   
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
   
   ```vb
   Imports System.Runtime.InteropServices
   
   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```
   
1. <span data-ttu-id="58c4a-152">在 [**工具**] 功能表上，選取 [**建立 guid**]，然後在 [**建立 guid** ] 對話方塊中，選取 [登錄**格式**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="58c4a-153">選取 [**複製**]，然後選取 [結束 **]。**</span><span class="sxs-lookup"><span data-stu-id="58c4a-153">Select **Copy**, and then select **Exit**.</span></span>
   
1. <span data-ttu-id="58c4a-154">在您`Guid`程式碼的屬性中，以您複製的 guid 取代範例 guid，並移除大括弧（ **{}** ）。</span><span class="sxs-lookup"><span data-stu-id="58c4a-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>
   
1. <span data-ttu-id="58c4a-155">在**方案總管**中，展開 [**屬性**] 資料夾，然後選取 [ *AssemblyInfo.cs* ] 或 [ *AssemblyInfo* ] 檔案。</span><span class="sxs-lookup"><span data-stu-id="58c4a-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="58c4a-156">在 [程式碼編輯器] 中，將下列屬性新增至檔案：</span><span class="sxs-lookup"><span data-stu-id="58c4a-156">In the code editor, add the following attribute to the file:</span></span>
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. <span data-ttu-id="58c4a-157">+ +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > </span><span class="sxs-lookup"><span data-stu-id="58c4a-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58c4a-158">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="58c4a-159">類別庫 DLL 檔案會經過編譯並儲存到指定的組建輸出路徑，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="58c4a-160">建立執行時間類別</span><span class="sxs-lookup"><span data-stu-id="58c4a-160">Create a runtime class</span></span>

<span data-ttu-id="58c4a-161">接下來，建立類型等價執行時間類別。</span><span class="sxs-lookup"><span data-stu-id="58c4a-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="58c4a-162">在 Visual Studio 中，選取 [檔案] > [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58c4a-163">在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*類別庫*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="58c4a-164">從清單中C#選取或 VB**類別庫（.NET Framework）** 範本，然後選取 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-164">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58c4a-165">在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceRuntime*，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="58c4a-166">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="58c4a-166">The new project is created.</span></span>
   
1. <span data-ttu-id="58c4a-167">在**方案總管**中，以滑鼠右鍵按一下*Class1.cs*或*Class1*檔案，選取 [**重新命名**]，然後將檔案從*Class1*重新命名為*SampleClass*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="58c4a-168">在提示中回應 **[是]** ，也會將`SampleClass`類別重新命名為。</span><span class="sxs-lookup"><span data-stu-id="58c4a-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="58c4a-169">這個類別會實作 `ISampleInterface` 介面。</span><span class="sxs-lookup"><span data-stu-id="58c4a-169">This class implements the `ISampleInterface` interface.</span></span>
   
1. <span data-ttu-id="58c4a-170">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58c4a-171">在 [**屬性**] 畫面的左窗格中選取 [**建立**]，然後將**輸出路徑**設定為您用於 TypeEquivalenceInterface 專案的相同位置，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="58c4a-172">在 [**屬性**] 畫面的左窗格中選取 [**簽署**]，然後選取 [**簽署元件**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="58c4a-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="58c4a-173">在 **[選擇強式名稱金鑰**檔] 的下拉式清單中，選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="58c4a-174">在 [**建立強式名稱金鑰**] 對話方塊中的 [**金鑰檔名稱**] 下，輸入 [*金鑰 .snk*]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="58c4a-175">取消選取 [**以密碼保護我的金鑰**檔] 核取方塊，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58c4a-176">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**加入** > **參考**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="58c4a-177">在 [**參考管理員**] 對話方塊中，選取 **[流覽**] 並流覽至 [輸出路徑] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="58c4a-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="58c4a-178">選取 [ *TypeEquivalenceInterface* ] 檔案，選取 [**新增**]，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58c4a-179">在**方案總管**中，展開 [**參考**] 資料夾，然後選取 [ **TypeEquivalenceInterface** ] 參考。</span><span class="sxs-lookup"><span data-stu-id="58c4a-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="58c4a-180">在 [**屬性**] 窗格中，將 [**特定版本**] 設為 [ **False** ] （如果尚未設定）。</span><span class="sxs-lookup"><span data-stu-id="58c4a-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>
   
1. <span data-ttu-id="58c4a-181">在程式碼編輯器中開啟*SampleClass*類別檔案，並以下列程式碼取代其內容，以建立`SampleClass`類別：</span><span class="sxs-lookup"><span data-stu-id="58c4a-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>
   
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
   }
   ```
   
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
   
1. <span data-ttu-id="58c4a-182">+ +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > </span><span class="sxs-lookup"><span data-stu-id="58c4a-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58c4a-183">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="58c4a-184">類別庫 DLL 檔案會經過編譯並儲存到指定的組建輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="58c4a-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="58c4a-185">建立用戶端專案</span><span class="sxs-lookup"><span data-stu-id="58c4a-185">Create a client project</span></span>

<span data-ttu-id="58c4a-186">最後，建立參考介面元件的類型等價用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="58c4a-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="58c4a-187">在 Visual Studio 中，選取 [檔案] > [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58c4a-188">在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*console* 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="58c4a-189">從清單中C#選取 [或 VB**主控台應用程式（.NET Framework）** ] 範本，然後選取 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-189">Select either the C# or VB **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58c4a-190">在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceClient*，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="58c4a-191">隨即會建立新專案。</span><span class="sxs-lookup"><span data-stu-id="58c4a-191">The new project is created.</span></span>
   
1. <span data-ttu-id="58c4a-192">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceClient**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58c4a-193">在 [**屬性**] 畫面的左窗格中選取 [**建立**]，然後將**輸出路徑**設定為您用於 TypeEquivalenceInterface 專案的相同位置，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="58c4a-194">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceClient**專案，然後選取 [**加入** > **參考**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="58c4a-195">在 [**參考管理員**] 對話方塊中，如果已列出 [ **TypeEquivalenceInterface** ] 檔案，請選取它。</span><span class="sxs-lookup"><span data-stu-id="58c4a-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="58c4a-196">如果沒有，請選取 **[流覽]** ，流覽至 [輸出路徑] 資料夾，選取 [ *TypeEquivalenceInterface* ] 檔案（而非*TypeEquivalenceRuntime*），然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="58c4a-197">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-197">Select **OK**.</span></span>
   
1. <span data-ttu-id="58c4a-198">在**方案總管**中，展開 [**參考**] 資料夾，然後選取 [ **TypeEquivalenceInterface** ] 參考。</span><span class="sxs-lookup"><span data-stu-id="58c4a-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="58c4a-199">在 [**屬性**] 窗格中，將 [**內嵌 Interop 類型**] 設定為 [ **True**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>
   
1. <span data-ttu-id="58c4a-200">在程式碼編輯器中開啟*Program.cs*或*Module1*檔案，並以下列程式碼取代其內容，以建立用戶端程式：</span><span class="sxs-lookup"><span data-stu-id="58c4a-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>
   
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
   
1. <span data-ttu-id="58c4a-201">+ +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > </span><span class="sxs-lookup"><span data-stu-id="58c4a-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58c4a-202">按**Ctrl** + **F5**以建立並執行程式。</span><span class="sxs-lookup"><span data-stu-id="58c4a-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="58c4a-203">請注意，主控台輸出會傳回元件版本**1.0.0.0**。</span><span class="sxs-lookup"><span data-stu-id="58c4a-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span> 
   
## <a name="modify-the-interface"></a><span data-ttu-id="58c4a-204">修改介面</span><span class="sxs-lookup"><span data-stu-id="58c4a-204">Modify the interface</span></span>

<span data-ttu-id="58c4a-205">現在，修改介面元件，並變更其版本。</span><span class="sxs-lookup"><span data-stu-id="58c4a-205">Now, modify the interface assembly, and change its version.</span></span> 

1. <span data-ttu-id="58c4a-206">在 Visual Studio 中，**選取** > [檔案] [**開啟** > **專案/方案**]，然後開啟 [ **TypeEquivalenceInterface** ] 專案。</span><span class="sxs-lookup"><span data-stu-id="58c4a-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>
   
1. <span data-ttu-id="58c4a-207">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58c4a-208">在 [**屬性**] 畫面的左窗格中選取 [**應用程式**]，然後選取 [**元件資訊**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="58c4a-209">在 [**元件資訊**] 對話方塊中，將 [**元件版本**] 和 [檔案**版本**] 值變更為*2.0.0.0*，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58c4a-210">開啟*SampleInterface.cs*或*SampleInterface*檔案，然後將下列程式`ISampleInterface`程式碼新增至介面：</span><span class="sxs-lookup"><span data-stu-id="58c4a-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. <span data-ttu-id="58c4a-211">+ +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > </span><span class="sxs-lookup"><span data-stu-id="58c4a-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58c4a-212">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="58c4a-213">類別庫 DLL 檔案的新版本會進行編譯，並儲存至組建輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="58c4a-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="58c4a-214">修改執行時間類別</span><span class="sxs-lookup"><span data-stu-id="58c4a-214">Modify the runtime class</span></span>

<span data-ttu-id="58c4a-215">同時修改執行時間類別並更新其版本。</span><span class="sxs-lookup"><span data-stu-id="58c4a-215">Also modify the runtime class and update its version.</span></span> 

1. <span data-ttu-id="58c4a-216">在 Visual Studio 中，**選取** > [檔案] [**開啟** > **專案/方案**]，然後開啟 [ **TypeEquivalenceRuntime** ] 專案。</span><span class="sxs-lookup"><span data-stu-id="58c4a-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>
   
1. <span data-ttu-id="58c4a-217">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58c4a-218">在 [**屬性**] 畫面的左窗格中選取 [**應用程式**]，然後選取 [**元件資訊**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="58c4a-219">在 [**元件資訊**] 對話方塊中，將 [**元件版本**] 和 [檔案**版本**] 值變更為*2.0.0.0*，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58c4a-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58c4a-220">開啟*SampleClass.cs*或*SampleClass*檔案，然後將下列程式`SampleClass`代碼新增至類別：</span><span class="sxs-lookup"><span data-stu-id="58c4a-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>
   
   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```
   
   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```
   
1. <span data-ttu-id="58c4a-221">+ +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > </span><span class="sxs-lookup"><span data-stu-id="58c4a-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58c4a-222">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="58c4a-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="58c4a-223">類別庫 DLL 檔案的新版本會進行編譯，並儲存至組建輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="58c4a-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="58c4a-224">執行更新的用戶端程式</span><span class="sxs-lookup"><span data-stu-id="58c4a-224">Run the updated client program</span></span> 

<span data-ttu-id="58c4a-225">移至組建輸出檔案夾位置，並執行*TypeEquivalenceClient*。</span><span class="sxs-lookup"><span data-stu-id="58c4a-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="58c4a-226">請注意，主控台輸出現在會反映新版本的`TypeEquivalenceRuntime`元件*2.0.0.0*，而不會重新編譯程式。</span><span class="sxs-lookup"><span data-stu-id="58c4a-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="58c4a-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58c4a-227">See also</span></span>

- [<span data-ttu-id="58c4a-228">/link (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="58c4a-228">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="58c4a-229">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58c4a-229">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="58c4a-230">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="58c4a-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="58c4a-231">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="58c4a-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="58c4a-232">具有元件的程式</span><span class="sxs-lookup"><span data-stu-id="58c4a-232">Program with assemblies</span></span>](program.md)
- [<span data-ttu-id="58c4a-233">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="58c4a-233">Assemblies in .NET</span></span>](index.md)
