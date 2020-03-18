---
title: 演練：在視覺化工作室中嵌入來自託管程式集的類型
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338548"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="cbdce-102">演練：在視覺化工作室中嵌入來自託管程式集的類型</span><span class="sxs-lookup"><span data-stu-id="cbdce-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="cbdce-103">若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。</span><span class="sxs-lookup"><span data-stu-id="cbdce-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="cbdce-104">也就是說，可以將程式編寫為使用託管庫任何版本的類型，而無需為每個新版本重新編譯。</span><span class="sxs-lookup"><span data-stu-id="cbdce-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="cbdce-105">內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。</span><span class="sxs-lookup"><span data-stu-id="cbdce-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="cbdce-106">當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。</span><span class="sxs-lookup"><span data-stu-id="cbdce-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="cbdce-107">但是，您也可以將類型嵌入與完全託管的解決方案一起使用。</span><span class="sxs-lookup"><span data-stu-id="cbdce-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="cbdce-108">指定可以嵌入的公共介面後，將創建實現這些介面的運行時類。</span><span class="sxs-lookup"><span data-stu-id="cbdce-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="cbdce-109">用戶端程式可以通過引用包含公共介面的程式集並設置`Embed Interop Types`引用`True`的屬性來在設計時嵌入介面的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="cbdce-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="cbdce-110">然後，用戶端程式可以載入作為這些介面鍵入的運行時物件的實例。</span><span class="sxs-lookup"><span data-stu-id="cbdce-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="cbdce-111">這相當於使用命令列編譯器並使用[-link 編譯器選項](../../csharp/language-reference/compiler-options/link-compiler-option.md)引用程式集。</span><span class="sxs-lookup"><span data-stu-id="cbdce-111">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="cbdce-112">如果創建強命名的運行時程式集的新版本，則不必重新編譯用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="cbdce-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="cbdce-113">用戶端程式繼續使用任何可用的運行時程式集版本，使用公共介面的嵌入式類型資訊。</span><span class="sxs-lookup"><span data-stu-id="cbdce-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="cbdce-114">在本逐步解說中，您將：</span><span class="sxs-lookup"><span data-stu-id="cbdce-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="cbdce-115">創建具有公共介面的強命名程式集，其中包含可嵌入的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="cbdce-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="cbdce-116">創建實現公共介面的強命名運行時程式集。</span><span class="sxs-lookup"><span data-stu-id="cbdce-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="cbdce-117">建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cbdce-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="cbdce-118">修改並重新建置執行階段組件。</span><span class="sxs-lookup"><span data-stu-id="cbdce-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="cbdce-119">運行用戶端程式以查看它使用新版本的運行時程式集，而無需重新編譯。</span><span class="sxs-lookup"><span data-stu-id="cbdce-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="cbdce-120">條件和限制</span><span class="sxs-lookup"><span data-stu-id="cbdce-120">Conditions and limitations</span></span>

<span data-ttu-id="cbdce-121">您可以在以下條件下嵌入程式集中的類型資訊：</span><span class="sxs-lookup"><span data-stu-id="cbdce-121">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="cbdce-122">組件已公開至少一個公用介面。</span><span class="sxs-lookup"><span data-stu-id="cbdce-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="cbdce-123">嵌入介面用`ComImport`具有唯一 GUID 的屬性`Guid`和屬性進行帶子。</span><span class="sxs-lookup"><span data-stu-id="cbdce-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="cbdce-124">您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件 </span><span class="sxs-lookup"><span data-stu-id="cbdce-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="cbdce-125">預設情況下，Visual C# 和 Visual Basic 專案範本`Guid`包括程式集級屬性。</span><span class="sxs-lookup"><span data-stu-id="cbdce-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="cbdce-126">由於類型嵌入的主要功能是支援 COM 交互操作程式集，因此在完全託管的解決方案中嵌入類型資訊時，以下限制適用：</span><span class="sxs-lookup"><span data-stu-id="cbdce-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="cbdce-127">僅嵌入特定于 COM 交互操作的屬性。</span><span class="sxs-lookup"><span data-stu-id="cbdce-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="cbdce-128">其他屬性將被忽略。</span><span class="sxs-lookup"><span data-stu-id="cbdce-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="cbdce-129">如果類型使用泛型參數，並且泛型參數的類型是嵌入類型，則無法跨程式集邊界使用該類型。</span><span class="sxs-lookup"><span data-stu-id="cbdce-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="cbdce-130">跨越程式集邊界的示例包括從另一個程式集調用方法或從另一個程式集中定義的類型派生類型。</span><span class="sxs-lookup"><span data-stu-id="cbdce-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="cbdce-131">系統不會內嵌常數。</span><span class="sxs-lookup"><span data-stu-id="cbdce-131">Constants are not embedded.</span></span>
- <span data-ttu-id="cbdce-132"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別不支援內嵌類型作為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="cbdce-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="cbdce-133">您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。</span><span class="sxs-lookup"><span data-stu-id="cbdce-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="cbdce-134">建立介面</span><span class="sxs-lookup"><span data-stu-id="cbdce-134">Create an interface</span></span>

<span data-ttu-id="cbdce-135">第一步是創建類型等效介面程式集。</span><span class="sxs-lookup"><span data-stu-id="cbdce-135">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="cbdce-136">在視覺化工作室中，選擇 **"檔** > **新專案** > **"。**</span><span class="sxs-lookup"><span data-stu-id="cbdce-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="cbdce-137">在"**創建新專案**"對話方塊中，在 **"搜索範本"** 框中鍵入*類庫*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="cbdce-138">從清單中選擇 C# 或視覺化基本**類庫 （.NET 框架）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-138">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="cbdce-139">在 **"配置新專案**"對話方塊中，在**專案名稱**下鍵入*TypeValvalence 介面*，然後選擇"**創建**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="cbdce-140">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-140">The new project is created.</span></span>

1. <span data-ttu-id="cbdce-141">在**解決方案資源管理器**中，按右鍵*Class1.cs*或*Class1.vb*檔，選擇**重命名**，並將檔從*類 1*重命名到*ISampleInterface*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="cbdce-142">回應 **"是**"的提示，將類重命名為`ISampleInterface`。</span><span class="sxs-lookup"><span data-stu-id="cbdce-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="cbdce-143">此類表示類的公共介面。</span><span class="sxs-lookup"><span data-stu-id="cbdce-143">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="cbdce-144">在**解決方案資源管理器**中，按右鍵**TypeValence 介面**專案，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cbdce-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="cbdce-145">選擇 **"在\*\*\*\*屬性"** 螢幕左窗格上的"生成"，並將 **"輸出"路徑**設置為電腦上的位置，例如*C：_TypeValenceSample*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="cbdce-146">在本演練中，您使用相同的位置。</span><span class="sxs-lookup"><span data-stu-id="cbdce-146">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="cbdce-147">選擇 **"屬性"** 螢幕左側窗格上的 **"簽名**"，然後選擇"**對程式集進行簽名**"核取方塊。</span><span class="sxs-lookup"><span data-stu-id="cbdce-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="cbdce-148">在 **"選擇強式名稱金鑰檔**"的下拉清單中，選擇 **"新建**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="cbdce-149">在 **"創建強式名稱鍵**"對話方塊中，在**鍵檔案名**下鍵入*key.snk*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="cbdce-150">取消選中 **"使用密碼核取方塊保護我的金鑰檔**"，然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="cbdce-151">在代碼編輯器中打開*ISampleInterface*類檔，並將其內容替換為以下代碼以創建`ISampleInterface`介面：</span><span class="sxs-lookup"><span data-stu-id="cbdce-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="cbdce-152">在 **"工具"** 功能表上，**選擇"創建 Guid**"，在 **"創建 GUID"** 對話方塊中，選擇 **"註冊表格式**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="cbdce-153">選擇 **"複製**"，然後選擇 **"退出**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-153">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="cbdce-154">在`Guid`代碼的屬性中，將示例 GUID 替換為複製的 GUID，然後刪除大括弧 \*\*（\*\*\*）。</span><span class="sxs-lookup"><span data-stu-id="cbdce-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="cbdce-155">在**解決方案資源管理器**中，展開**屬性**資料夾並選擇*AssemblyInfo.cs*或*AssemblyInfo.vb*檔。</span><span class="sxs-lookup"><span data-stu-id="cbdce-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="cbdce-156">在代碼編輯器中，向檔添加以下屬性：</span><span class="sxs-lookup"><span data-stu-id="cbdce-156">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="cbdce-157">選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="cbdce-158">在**解決方案資源管理器**中，按右鍵**TypeValence 介面**專案並選擇 **"生成**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="cbdce-159">類庫 DLL 檔被編譯並保存到指定的生成輸出路徑，例如*C：_TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="cbdce-160">創建運行時類</span><span class="sxs-lookup"><span data-stu-id="cbdce-160">Create a runtime class</span></span>

<span data-ttu-id="cbdce-161">接下來，創建類型等效運行時類。</span><span class="sxs-lookup"><span data-stu-id="cbdce-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="cbdce-162">在視覺化工作室中，選擇 **"檔** > **新專案** > **"。**</span><span class="sxs-lookup"><span data-stu-id="cbdce-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="cbdce-163">在"**創建新專案**"對話方塊中，在 **"搜索範本"** 框中鍵入*類庫*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="cbdce-164">從清單中選擇 C# 或視覺化基本**類庫 （.NET 框架）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-164">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="cbdce-165">在"**配置新專案**"對話方塊中，在 **"專案名稱**"下鍵入*TypeValvalence 執行時間*，然後選擇"**創建**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="cbdce-166">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-166">The new project is created.</span></span>

1. <span data-ttu-id="cbdce-167">在**解決方案資源管理器**中，按右鍵*Class1.cs*或*Class1.vb*檔，選擇 **"重命名**"並將檔從*類 1*重命名到*示例類*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="cbdce-168">回應 **"是**"的提示，將類重命名為`SampleClass`。</span><span class="sxs-lookup"><span data-stu-id="cbdce-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="cbdce-169">此類別會實作 `ISampleInterface` 介面。</span><span class="sxs-lookup"><span data-stu-id="cbdce-169">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="cbdce-170">在**解決方案資源管理器中**，按右鍵**TypeValence 介面**專案並選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cbdce-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="cbdce-171">選擇"**屬性"** 螢幕左窗格上的 **"生成\*\*\*\*"，然後將"輸出"路徑**設置為與 TypeEquivalence 介面專案所用的相同位置，例如*C：_TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="cbdce-172">選擇 **"屬性"** 螢幕左側窗格上的 **"簽名**"，然後選擇"**對程式集進行簽名**"核取方塊。</span><span class="sxs-lookup"><span data-stu-id="cbdce-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="cbdce-173">在 **"選擇強式名稱金鑰檔**"的下拉清單中，選擇 **"新建**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="cbdce-174">在 **"創建強式名稱鍵**"對話方塊中，在**鍵檔案名**下鍵入*key.snk*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="cbdce-175">取消選中 **"使用密碼核取方塊保護我的金鑰檔**"，然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="cbdce-176">在**解決方案資源管理器中**，按右鍵 **"類型等效執行時間"** 專案，然後選擇"**添加** > **參考**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="cbdce-177">在 **"參考管理器"** 對話方塊中，選擇 **"流覽**"並流覽到輸出路徑資料夾。</span><span class="sxs-lookup"><span data-stu-id="cbdce-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="cbdce-178">選擇*TypeValenceInterface.dll*檔，選擇 **"添加**"，然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="cbdce-179">在**解決方案資源管理器**中，展開**引用**資料夾並選擇**類型等效介面**引用。</span><span class="sxs-lookup"><span data-stu-id="cbdce-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="cbdce-180">在"**屬性"** 窗格中，將 **"特定版本**"設置為 **"false"（** 如果尚未）。</span><span class="sxs-lookup"><span data-stu-id="cbdce-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="cbdce-181">在代碼編輯器中打開*Sampleclass*類檔，並將其內容替換為以下代碼以創建類`SampleClass`：</span><span class="sxs-lookup"><span data-stu-id="cbdce-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="cbdce-182">選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="cbdce-183">在**解決方案資源管理器**中，按右鍵 **"類型等效執行時間**"專案並選擇 **"生成**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="cbdce-184">類庫 DLL 檔被編譯並保存到指定的生成輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="cbdce-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="cbdce-185">創建用戶端專案</span><span class="sxs-lookup"><span data-stu-id="cbdce-185">Create a client project</span></span>

<span data-ttu-id="cbdce-186">最後，創建引用介面程式集的類型等效用戶端程式。</span><span class="sxs-lookup"><span data-stu-id="cbdce-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="cbdce-187">在視覺化工作室中，選擇 **"檔** > **新專案** > **"。**</span><span class="sxs-lookup"><span data-stu-id="cbdce-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="cbdce-188">在"**創建新專案**"對話方塊中，在 **"搜索範本"** 框中鍵入*主控台*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="cbdce-189">從清單中選擇 C# 或視覺化基本**主控台應用 （.NET 框架）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-189">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="cbdce-190">在"**配置新專案**"對話方塊中，在**專案名稱**下鍵入*TypeValvalence 用戶端*，然後選擇"**創建**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="cbdce-191">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-191">The new project is created.</span></span>

1. <span data-ttu-id="cbdce-192">在**解決方案資源管理器中**，按右鍵**TypeValenceClient**專案並選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cbdce-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="cbdce-193">選擇"**屬性"** 螢幕左窗格上的 **"生成\*\*\*\*"，然後將"輸出"路徑**設置為與 TypeEquivalence 介面專案所用的相同位置，例如*C：_TypeEquivalenceSample*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="cbdce-194">在**解決方案資源管理器中**，按右鍵**TypeValenceClient**專案並選擇"**添加** > **參考**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="cbdce-195">在**參考管理器**對話方塊中，如果已列出**TypeEquivalenceInterface.dll**檔，請選擇它。</span><span class="sxs-lookup"><span data-stu-id="cbdce-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="cbdce-196">如果沒有，請選擇 **"流覽**"，流覽到輸出路徑資料夾，選擇*TypeEquivalenceInterface.dll*檔（不是*TypeValenceruntime.dll），* 然後選擇"**添加**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="cbdce-197">選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-197">Select **OK**.</span></span>

1. <span data-ttu-id="cbdce-198">在**解決方案資源管理器**中，展開**引用**資料夾並選擇**類型等效介面**引用。</span><span class="sxs-lookup"><span data-stu-id="cbdce-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="cbdce-199">在"**屬性"** 窗格中，將 **"嵌入互通類型"** 設置為 **"true"。**</span><span class="sxs-lookup"><span data-stu-id="cbdce-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="cbdce-200">在代碼編輯器中打開*Program.cs*或*Module1.vb*檔，並將其內容替換為以下代碼以創建用戶端程式：</span><span class="sxs-lookup"><span data-stu-id="cbdce-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

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

1. <span data-ttu-id="cbdce-201">選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="cbdce-202">按**Ctrl**+**F5**生成並運行程式。</span><span class="sxs-lookup"><span data-stu-id="cbdce-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="cbdce-203">請注意，主控台輸出返回程式集版本**1.0.0.0**。</span><span class="sxs-lookup"><span data-stu-id="cbdce-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="cbdce-204">修改介面</span><span class="sxs-lookup"><span data-stu-id="cbdce-204">Modify the interface</span></span>

<span data-ttu-id="cbdce-205">現在，修改介面程式集，並更改其版本。</span><span class="sxs-lookup"><span data-stu-id="cbdce-205">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="cbdce-206">在視覺化工作室中，選擇 **"檔** > **打開** > **專案/解決方案**"，然後打開**類型等效介面**專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="cbdce-207">在**解決方案資源管理器中**，按右鍵**TypeValence 介面**專案並選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cbdce-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="cbdce-208">在 **"屬性"** 螢幕的左側窗格中選擇 **"應用程式**"，然後選擇 **"程式集資訊**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="cbdce-209">在 **"程式集資訊"** 對話方塊中，將**程式集版本**和**檔版本**值更改為*2.0.0.0*，然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="cbdce-210">打開*SampleInterface.cs*或*示例介面.vb*檔，並將以下程式碼添加到`ISampleInterface`介面：</span><span class="sxs-lookup"><span data-stu-id="cbdce-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="cbdce-211">選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="cbdce-212">在**解決方案資源管理器**中，按右鍵**TypeValence 介面**專案並選擇 **"生成**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="cbdce-213">編譯類庫 DLL 檔的新版本並將其保存到生成輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="cbdce-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="cbdce-214">修改運行時類</span><span class="sxs-lookup"><span data-stu-id="cbdce-214">Modify the runtime class</span></span>

<span data-ttu-id="cbdce-215">還要修改運行時類並更新其版本。</span><span class="sxs-lookup"><span data-stu-id="cbdce-215">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="cbdce-216">在視覺化工作室中，選擇 **"檔** > **打開** > **專案/解決方案**"，然後打開**TypeValenceRuntime**專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="cbdce-217">在**解決方案資源管理器中**，按右鍵**TypeValence 運行時**專案並選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cbdce-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="cbdce-218">在 **"屬性"** 螢幕的左側窗格中選擇 **"應用程式**"，然後選擇 **"程式集資訊**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="cbdce-219">在 **"程式集資訊"** 對話方塊中，將**程式集版本**和**檔版本**值更改為*2.0.0.0*，然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="cbdce-220">打開*SampleClass.cs*或*sampleClass.vb*檔，並將以下代碼添加到`SampleClass`類：</span><span class="sxs-lookup"><span data-stu-id="cbdce-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="cbdce-221">選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。</span><span class="sxs-lookup"><span data-stu-id="cbdce-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="cbdce-222">在**解決方案資源管理器**中，按右鍵 **"類型等效執行時間**"專案並選擇 **"生成**"。</span><span class="sxs-lookup"><span data-stu-id="cbdce-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="cbdce-223">編譯類庫 DLL 檔的新版本並將其保存到生成輸出路徑。</span><span class="sxs-lookup"><span data-stu-id="cbdce-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="cbdce-224">運行更新的用戶端程式</span><span class="sxs-lookup"><span data-stu-id="cbdce-224">Run the updated client program</span></span>

<span data-ttu-id="cbdce-225">轉到生成輸出檔案夾位置並運行*TypeEquivalenceClient.exe*。</span><span class="sxs-lookup"><span data-stu-id="cbdce-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="cbdce-226">請注意，主控台輸出現在反映`TypeEquivalenceRuntime`程式集的新版本*2.0.0.0，* 無需重新編譯程式。</span><span class="sxs-lookup"><span data-stu-id="cbdce-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbdce-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbdce-227">See also</span></span>

- [<span data-ttu-id="cbdce-228">-link (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="cbdce-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="cbdce-229">-連結（視覺基礎）</span><span class="sxs-lookup"><span data-stu-id="cbdce-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="cbdce-230">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cbdce-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cbdce-231">程式設計概念（視覺基礎）</span><span class="sxs-lookup"><span data-stu-id="cbdce-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="cbdce-232">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="cbdce-232">Assemblies in .NET</span></span>](index.md)
