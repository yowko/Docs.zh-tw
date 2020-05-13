---
title: 逐步解說：在 Visual Studio 中內嵌來自受控組件的類型
description: 本逐步解說將示範如何使用 Visual Studio，在 .NET 中內嵌來自 managed 元件的類型。 內嵌類型可支援版本獨立性。
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378978"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="4ece3-104">逐步解說：在 Visual Studio 中內嵌來自受控組件的類型</span><span class="sxs-lookup"><span data-stu-id="4ece3-104">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="4ece3-105">若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。</span><span class="sxs-lookup"><span data-stu-id="4ece3-105">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="4ece3-106">也就是說，您的程式可以撰寫成使用來自任何版本之 managed 程式庫的類型，而不需要針對每個新版本重新編譯。</span><span class="sxs-lookup"><span data-stu-id="4ece3-106">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="4ece3-107">內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。</span><span class="sxs-lookup"><span data-stu-id="4ece3-107">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="4ece3-108">當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="4ece3-108">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="4ece3-109">不過，您也可以將類型內嵌用於完全受控的解決方案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-109">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="4ece3-110">在您指定可以內嵌的公用介面之後，就可以建立執行這些介面的執行時間類別。</span><span class="sxs-lookup"><span data-stu-id="4ece3-110">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="4ece3-111">用戶端程式可以藉由參考包含公用介面的元件，並將參考的屬性設定為，在設計階段內嵌介面的類型資訊 `Embed Interop Types` `True` 。</span><span class="sxs-lookup"><span data-stu-id="4ece3-111">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="4ece3-112">然後，用戶端程式可以載入以這些介面類別型輸入之執行時間物件的實例。</span><span class="sxs-lookup"><span data-stu-id="4ece3-112">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="4ece3-113">這相當於使用命令列編譯器，並使用[-link 編譯器選項](../../csharp/language-reference/compiler-options/link-compiler-option.md)來參考元件。</span><span class="sxs-lookup"><span data-stu-id="4ece3-113">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="4ece3-114">如果您建立新版本的強式名稱執行時間元件，則不需要重新編譯用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="4ece3-114">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="4ece3-115">用戶端程式會繼續使用任何版本的執行時間元件，並使用公用介面的內嵌類型資訊。</span><span class="sxs-lookup"><span data-stu-id="4ece3-115">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="4ece3-116">在本逐步解說中，您將：</span><span class="sxs-lookup"><span data-stu-id="4ece3-116">In this walkthrough, you:</span></span>

1. <span data-ttu-id="4ece3-117">建立具有公用介面的強式名稱元件，其中包含可內嵌的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="4ece3-117">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="4ece3-118">建立強式名稱的執行時間元件，以執行公用介面。</span><span class="sxs-lookup"><span data-stu-id="4ece3-118">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="4ece3-119">建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4ece3-119">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="4ece3-120">修改並重新建置執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="4ece3-120">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="4ece3-121">執行用戶端程式，以查看它是否使用新版本的執行時間元件，而不需要重新編譯。</span><span class="sxs-lookup"><span data-stu-id="4ece3-121">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="4ece3-122">條件和限制</span><span class="sxs-lookup"><span data-stu-id="4ece3-122">Conditions and limitations</span></span>

<span data-ttu-id="4ece3-123">在下列情況下，您可以從元件內嵌類型資訊：</span><span class="sxs-lookup"><span data-stu-id="4ece3-123">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="4ece3-124">組件已公開至少一個公用介面。</span><span class="sxs-lookup"><span data-stu-id="4ece3-124">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="4ece3-125">內嵌的介面會以 `ComImport` 具有唯一 guid 的屬性和屬性來標注 `Guid` 。</span><span class="sxs-lookup"><span data-stu-id="4ece3-125">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="4ece3-126">您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件 </span><span class="sxs-lookup"><span data-stu-id="4ece3-126">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="4ece3-127">根據預設，Visual c # 和 Visual Basic 專案範本包含元件層級 `Guid` 屬性。</span><span class="sxs-lookup"><span data-stu-id="4ece3-127">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="4ece3-128">因為內嵌類型的主要功能是支援 COM Interop 元件，所以當您在完全受控的方案中嵌入類型資訊時，會有下列限制：</span><span class="sxs-lookup"><span data-stu-id="4ece3-128">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="4ece3-129">僅內嵌 COM Interop 特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="4ece3-129">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="4ece3-130">其他屬性則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="4ece3-130">Other attributes are ignored.</span></span>
- <span data-ttu-id="4ece3-131">如果類型使用泛型參數，且泛型參數的類型是內嵌類型，則該類型不能跨元件界限使用。</span><span class="sxs-lookup"><span data-stu-id="4ece3-131">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="4ece3-132">跨越元件界限的範例包括從另一個元件呼叫方法，或從另一個元件中定義的型別衍生型別。</span><span class="sxs-lookup"><span data-stu-id="4ece3-132">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="4ece3-133">系統不會內嵌常數。</span><span class="sxs-lookup"><span data-stu-id="4ece3-133">Constants are not embedded.</span></span>
- <span data-ttu-id="4ece3-134"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別不支援內嵌類型作為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4ece3-134">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="4ece3-135">您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。</span><span class="sxs-lookup"><span data-stu-id="4ece3-135">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="4ece3-136">建立介面</span><span class="sxs-lookup"><span data-stu-id="4ece3-136">Create an interface</span></span>

<span data-ttu-id="4ece3-137">第一個步驟是建立類型等價介面元件。</span><span class="sxs-lookup"><span data-stu-id="4ece3-137">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="4ece3-138">在 Visual Studio 中，選取 [檔案]   >  [新增]   >  [專案]  。</span><span class="sxs-lookup"><span data-stu-id="4ece3-138">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="4ece3-139">在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*類別庫*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-139">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="4ece3-140">從清單中選取 [c #] 或 [Visual Basic**類別庫（.NET Framework）** ] 範本，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-140">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="4ece3-141">在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceInterface*，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-141">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="4ece3-142">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-142">The new project is created.</span></span>

1. <span data-ttu-id="4ece3-143">在**方案總管**中，以滑鼠右鍵按一下*Class1.cs*或*Class1*檔案，選取 [**重新命名**]，然後將檔案從*Class1*重新命名為*ISampleInterface*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-143">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="4ece3-144">在提示中回應 **[是]** ，也會將類別重新命名為 `ISampleInterface` 。</span><span class="sxs-lookup"><span data-stu-id="4ece3-144">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="4ece3-145">此類別代表類別的公用介面。</span><span class="sxs-lookup"><span data-stu-id="4ece3-145">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="4ece3-146">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-146">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="4ece3-147">在 [**屬性**] 畫面的左窗格中選取 [**建立**]，並將**輸出路徑**設定為您電腦上的位置，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-147">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="4ece3-148">在本逐步解說中，您會使用相同的位置。</span><span class="sxs-lookup"><span data-stu-id="4ece3-148">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="4ece3-149">在 [**屬性**] 畫面的左窗格中選取 [**簽署**]，然後選取 [**簽署元件**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4ece3-149">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="4ece3-150">在 **[選擇強式名稱金鑰**檔] 的下拉式清單中，選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-150">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="4ece3-151">在 [**建立強式名稱金鑰**] 對話方塊中的 [**金鑰檔名稱**] 下，輸入 [*金鑰 .snk*]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-151">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="4ece3-152">取消選取 [**以密碼保護我的金鑰**檔] 核取方塊，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-152">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="4ece3-153">在程式碼編輯器中開啟*ISampleInterface*類別檔案，並以下列程式碼取代其內容以建立 `ISampleInterface` 介面：</span><span class="sxs-lookup"><span data-stu-id="4ece3-153">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="4ece3-154">在 [**工具**] 功能表上，選取 [**建立 guid**]，然後在 [**建立 guid** ] 對話方塊中，選取 [登錄**格式**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-154">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="4ece3-155">選取 [**複製**]，然後選取 [結束 **]。**</span><span class="sxs-lookup"><span data-stu-id="4ece3-155">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="4ece3-156">在 `Guid` 您程式碼的屬性中，以您複製的 guid 取代範例 guid，並移除大括弧（**{}**）。</span><span class="sxs-lookup"><span data-stu-id="4ece3-156">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="4ece3-157">在**方案總管**中，展開 [**屬性**] 資料夾，然後選取 [ *AssemblyInfo.cs* ] 或 [ *AssemblyInfo* ] 檔案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-157">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="4ece3-158">在 [程式碼編輯器] 中，將下列屬性新增至檔案：</span><span class="sxs-lookup"><span data-stu-id="4ece3-158">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="4ece3-159">選取**File**  >  [檔案] [**全部儲存**] 或按**Ctrl** + **Shift** + **S**以儲存檔案和專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-159">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="4ece3-160">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-160">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="4ece3-161">類別庫 DLL 檔案會經過編譯並儲存到指定的組建輸出路徑，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-161">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="4ece3-162">建立執行時間類別</span><span class="sxs-lookup"><span data-stu-id="4ece3-162">Create a runtime class</span></span>

<span data-ttu-id="4ece3-163">接下來，建立類型等價執行時間類別。</span><span class="sxs-lookup"><span data-stu-id="4ece3-163">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="4ece3-164">在 Visual Studio 中，選取 [檔案]   >  [新增]   >  [專案]  。</span><span class="sxs-lookup"><span data-stu-id="4ece3-164">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="4ece3-165">在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*類別庫*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-165">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="4ece3-166">從清單中選取 [c #] 或 [Visual Basic**類別庫（.NET Framework）** ] 範本，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-166">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="4ece3-167">在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceRuntime*，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-167">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="4ece3-168">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-168">The new project is created.</span></span>

1. <span data-ttu-id="4ece3-169">在**方案總管**中，以滑鼠右鍵按一下*Class1.cs*或*Class1*檔案，選取 [**重新命名**]，然後將檔案從*Class1*重新命名為*SampleClass*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-169">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="4ece3-170">在提示中回應 **[是]** ，也會將類別重新命名為 `SampleClass` 。</span><span class="sxs-lookup"><span data-stu-id="4ece3-170">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="4ece3-171">此類別會實作 `ISampleInterface` 介面。</span><span class="sxs-lookup"><span data-stu-id="4ece3-171">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="4ece3-172">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-172">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="4ece3-173">在 [**屬性**] 畫面的左窗格中選取 [**建立**]，然後將**輸出路徑**設定為您用於 TypeEquivalenceInterface 專案的相同位置，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-173">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="4ece3-174">在 [**屬性**] 畫面的左窗格中選取 [**簽署**]，然後選取 [**簽署元件**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4ece3-174">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="4ece3-175">在 **[選擇強式名稱金鑰**檔] 的下拉式清單中，選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-175">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="4ece3-176">在 [**建立強式名稱金鑰**] 對話方塊中的 [**金鑰檔名稱**] 下，輸入 [*金鑰 .snk*]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-176">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="4ece3-177">取消選取 [**以密碼保護我的金鑰**檔] 核取方塊，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-177">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="4ece3-178">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**加入**  >  **參考**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-178">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="4ece3-179">在 [**參考管理員**] 對話方塊中，選取 **[流覽**] 並流覽至 [輸出路徑] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4ece3-179">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="4ece3-180">選取 [ *TypeEquivalenceInterface* ] 檔案，選取 [**新增**]，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-180">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="4ece3-181">在**方案總管**中，展開 [**參考**] 資料夾，然後選取 [ **TypeEquivalenceInterface** ] 參考。</span><span class="sxs-lookup"><span data-stu-id="4ece3-181">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="4ece3-182">在 [**屬性**] 窗格中，將 [**特定版本**] 設為 [ **False** ] （如果尚未設定）。</span><span class="sxs-lookup"><span data-stu-id="4ece3-182">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="4ece3-183">在程式碼編輯器中開啟*SampleClass*類別檔案，並以下列程式碼取代其內容，以建立 `SampleClass` 類別：</span><span class="sxs-lookup"><span data-stu-id="4ece3-183">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

   ```csharp
   using System;
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

1. <span data-ttu-id="4ece3-184">選取**File**  >  [檔案] [**全部儲存**] 或按**Ctrl** + **Shift** + **S**以儲存檔案和專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-184">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="4ece3-185">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-185">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="4ece3-186">類別庫 DLL 檔案會經過編譯並儲存到指定的組建輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="4ece3-186">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="4ece3-187">建立用戶端專案</span><span class="sxs-lookup"><span data-stu-id="4ece3-187">Create a client project</span></span>

<span data-ttu-id="4ece3-188">最後，建立參考介面元件的類型等價用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="4ece3-188">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="4ece3-189">在 Visual Studio 中，選取 [檔案]   >  [新增]   >  [專案]  。</span><span class="sxs-lookup"><span data-stu-id="4ece3-189">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="4ece3-190">在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*console* 。</span><span class="sxs-lookup"><span data-stu-id="4ece3-190">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="4ece3-191">從清單中選取 [c #] 或 [Visual Basic**主控台應用程式（.NET Framework）** ] 範本，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-191">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="4ece3-192">在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceClient*，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-192">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="4ece3-193">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-193">The new project is created.</span></span>

1. <span data-ttu-id="4ece3-194">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceClient**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="4ece3-195">在 [**屬性**] 畫面的左窗格中選取 [**建立**]，然後將**輸出路徑**設定為您用於 TypeEquivalenceInterface 專案的相同位置，例如*C:\TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-195">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="4ece3-196">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceClient**專案，然後選取 [**加入**  >  **參考**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-196">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="4ece3-197">在 [**參考管理員**] 對話方塊中，如果已列出 [ **TypeEquivalenceInterface** ] 檔案，請選取它。</span><span class="sxs-lookup"><span data-stu-id="4ece3-197">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="4ece3-198">如果沒有，請選取 **[流覽]**，流覽至 [輸出路徑] 資料夾，選取 [ *TypeEquivalenceInterface* ] 檔案（而非*TypeEquivalenceRuntime*），然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-198">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="4ece3-199">選取 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="4ece3-199">Select **OK**.</span></span>

1. <span data-ttu-id="4ece3-200">在**方案總管**中，展開 [**參考**] 資料夾，然後選取 [ **TypeEquivalenceInterface** ] 參考。</span><span class="sxs-lookup"><span data-stu-id="4ece3-200">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="4ece3-201">在 [**屬性**] 窗格中，將 [**內嵌 Interop 類型**] 設定為 [ **True**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-201">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="4ece3-202">在程式碼編輯器中開啟*Program.cs*或*Module1*檔案，並以下列程式碼取代其內容，以建立用戶端程式：</span><span class="sxs-lookup"><span data-stu-id="4ece3-202">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

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
   Imports System.Reflection
   Imports TypeEquivalenceInterface

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

1. <span data-ttu-id="4ece3-203">選取**File**  >  [檔案] [**全部儲存**] 或按**Ctrl** + **Shift** + **S**以儲存檔案和專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-203">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="4ece3-204">按**Ctrl** + **F5**以建立並執行程式。</span><span class="sxs-lookup"><span data-stu-id="4ece3-204">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="4ece3-205">請注意，主控台輸出會傳回元件版本**1.0.0.0**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-205">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="4ece3-206">修改介面</span><span class="sxs-lookup"><span data-stu-id="4ece3-206">Modify the interface</span></span>

<span data-ttu-id="4ece3-207">現在，修改介面元件，並變更其版本。</span><span class="sxs-lookup"><span data-stu-id="4ece3-207">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="4ece3-208">在 Visual Studio 中，**選取 [** 檔案]  >  [**開啟**  >  **專案/方案**]，然後開啟 [ **TypeEquivalenceInterface** ] 專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-208">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="4ece3-209">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-209">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="4ece3-210">在 [**屬性**] 畫面的左窗格中選取 [**應用程式**]，然後選取 [**元件資訊**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-210">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="4ece3-211">在 [**元件資訊**] 對話方塊中，將 [**元件版本**] 和 [檔案**版本**] 值變更為*2.0.0.0*，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-211">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="4ece3-212">開啟*SampleInterface.cs*或*SampleInterface*檔案，然後將下列程式程式碼新增至 `ISampleInterface` 介面：</span><span class="sxs-lookup"><span data-stu-id="4ece3-212">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="4ece3-213">選取**File**  >  [檔案] [**全部儲存**] 或按**Ctrl** + **Shift** + **S**以儲存檔案和專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-213">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="4ece3-214">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-214">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="4ece3-215">類別庫 DLL 檔案的新版本會進行編譯，並儲存至組建輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="4ece3-215">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="4ece3-216">修改執行時間類別</span><span class="sxs-lookup"><span data-stu-id="4ece3-216">Modify the runtime class</span></span>

<span data-ttu-id="4ece3-217">同時修改執行時間類別並更新其版本。</span><span class="sxs-lookup"><span data-stu-id="4ece3-217">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="4ece3-218">在 Visual Studio 中，**選取 [** 檔案]  >  [**開啟**  >  **專案/方案**]，然後開啟 [ **TypeEquivalenceRuntime** ] 專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-218">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="4ece3-219">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-219">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="4ece3-220">在 [**屬性**] 畫面的左窗格中選取 [**應用程式**]，然後選取 [**元件資訊**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-220">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="4ece3-221">在 [**元件資訊**] 對話方塊中，將 [**元件版本**] 和 [檔案**版本**] 值變更為*2.0.0.0*，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="4ece3-221">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="4ece3-222">開啟*SampleClass.cs*或*SampleClass*檔案，然後將下列程式碼新增至 `SampleClass` 類別：</span><span class="sxs-lookup"><span data-stu-id="4ece3-222">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="4ece3-223">選取**File**  >  [檔案] [**全部儲存**] 或按**Ctrl** + **Shift** + **S**以儲存檔案和專案。</span><span class="sxs-lookup"><span data-stu-id="4ece3-223">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="4ece3-224">在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="4ece3-224">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="4ece3-225">類別庫 DLL 檔案的新版本會進行編譯，並儲存至組建輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="4ece3-225">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="4ece3-226">執行更新的用戶端程式</span><span class="sxs-lookup"><span data-stu-id="4ece3-226">Run the updated client program</span></span>

<span data-ttu-id="4ece3-227">移至組建輸出檔案夾位置，並執行*TypeEquivalenceClient*。</span><span class="sxs-lookup"><span data-stu-id="4ece3-227">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="4ece3-228">請注意，主控台輸出現在會反映新版本的 `TypeEquivalenceRuntime` 元件*2.0.0.0*，而不會重新編譯程式。</span><span class="sxs-lookup"><span data-stu-id="4ece3-228">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ece3-229">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ece3-229">See also</span></span>

- [<span data-ttu-id="4ece3-230">-link (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="4ece3-230">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="4ece3-231">-link （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4ece3-231">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="4ece3-232">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="4ece3-232">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="4ece3-233">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4ece3-233">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="4ece3-234">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="4ece3-234">Assemblies in .NET</span></span>](index.md)
