---
title: 如何：設定免註冊啟用的 .NET Framework 架構 COM 元件
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 744ce1f2810eee025f071cafaa71e473b6ed4c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392849"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="ed08e-102">如何：設定免註冊啟用的 .NET Framework 架構 COM 元件</span><span class="sxs-lookup"><span data-stu-id="ed08e-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="ed08e-103">.NET Framework 型元件的免註冊啟用，只比 COM 元件的免註冊啟用略為複雜。</span><span class="sxs-lookup"><span data-stu-id="ed08e-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="ed08e-104">安裝程式需要兩個資訊清單：</span><span class="sxs-lookup"><span data-stu-id="ed08e-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="ed08e-105">COM 應用程式必須有 Win32 樣式應用程式資訊清單，才能識別 Managed 元件。</span><span class="sxs-lookup"><span data-stu-id="ed08e-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="ed08e-106">.NET Framework 元件必須具有執行階段所需啟用資訊的元件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ed08e-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="ed08e-107">本主題描述如何建立應用程式資訊清單與應用程式的關聯、建立元件資訊清單與元件的關聯，以及將元件資訊清單內嵌在組件中。</span><span class="sxs-lookup"><span data-stu-id="ed08e-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="ed08e-108">建立應用程式資訊清單</span><span class="sxs-lookup"><span data-stu-id="ed08e-108">To create an application manifest</span></span>  
  
1.  <span data-ttu-id="ed08e-109">使用 XML 編輯器，建立 (或修改) COM 應用程式所擁有的應用程式資訊清單，而其與一或多個 Managed 元件交互操作。</span><span class="sxs-lookup"><span data-stu-id="ed08e-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2.  <span data-ttu-id="ed08e-110">在檔案開頭，插入下列標準標頭：</span><span class="sxs-lookup"><span data-stu-id="ed08e-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="ed08e-111">如需資訊清單元素及其屬性的相關資訊，請參閱[應用程式資訊清單](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="ed08e-111">For information about manifest elements and their attributes, see [Application Manifests](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).</span></span>  
  
3.  <span data-ttu-id="ed08e-112">識別資訊清單的擁有者。</span><span class="sxs-lookup"><span data-stu-id="ed08e-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="ed08e-113">在下列範例中，`myComApp` 第 1 版擁有資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="ed08e-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  <span data-ttu-id="ed08e-114">識別相依組件。</span><span class="sxs-lookup"><span data-stu-id="ed08e-114">Identify dependent assemblies.</span></span> <span data-ttu-id="ed08e-115">在下列範例中，`myComApp` 取決於 `myManagedComp`。</span><span class="sxs-lookup"><span data-stu-id="ed08e-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="ed08e-116">儲存並命名資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="ed08e-116">Save and name the manifest file.</span></span> <span data-ttu-id="ed08e-117">應用程式資訊清單的名稱就是後接 .manifest 副檔名的組件可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="ed08e-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="ed08e-118">例如，myComApp.exe 的應用程式資訊清單檔案名稱是 myComApp.exe.manifest。</span><span class="sxs-lookup"><span data-stu-id="ed08e-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="ed08e-119">您可以在與 COM 應用程式相同的目錄中安裝應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ed08e-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="ed08e-120">或者，您可以將它當成資源新增至應用程式的.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="ed08e-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="ed08e-121">如需詳細資訊，請參閱[關於並存組件](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="ed08e-121">For additional information, For more information, see [About Side-by-Side Assemblies](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="ed08e-122">建立元件資訊清單</span><span class="sxs-lookup"><span data-stu-id="ed08e-122">To create a component manifest</span></span>  
  
1.  <span data-ttu-id="ed08e-123">使用 XML 編輯器，建立元件資訊清單以描述 Managed 組件。</span><span class="sxs-lookup"><span data-stu-id="ed08e-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2.  <span data-ttu-id="ed08e-124">在檔案開頭，插入下列標準標頭：</span><span class="sxs-lookup"><span data-stu-id="ed08e-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  <span data-ttu-id="ed08e-125">識別檔案的擁有者。</span><span class="sxs-lookup"><span data-stu-id="ed08e-125">Identify the owner of the file.</span></span> <span data-ttu-id="ed08e-126">應用程式資訊清單檔中 `<dependentAssembly>` 項目的 `<assemblyIdentity>` 項目必須符合元件資訊清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="ed08e-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="ed08e-127">在下列範例中，`myManagedComp` 版本 1.2.3.4 擁有資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="ed08e-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  <span data-ttu-id="ed08e-128">識別組件中的每個類別。</span><span class="sxs-lookup"><span data-stu-id="ed08e-128">Identify each class in the assembly.</span></span> <span data-ttu-id="ed08e-129">使用 `<clrClass>` 項目，唯一識別 Managed 組件中的每個類別。</span><span class="sxs-lookup"><span data-stu-id="ed08e-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="ed08e-130">項目 (即 `<assembly>` 項目的子項目) 具有下表所述的屬性。</span><span class="sxs-lookup"><span data-stu-id="ed08e-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="ed08e-131">屬性</span><span class="sxs-lookup"><span data-stu-id="ed08e-131">Attribute</span></span>|<span data-ttu-id="ed08e-132">描述</span><span class="sxs-lookup"><span data-stu-id="ed08e-132">Description</span></span>|<span data-ttu-id="ed08e-133">必要</span><span class="sxs-lookup"><span data-stu-id="ed08e-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="ed08e-134">指定要啟用之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ed08e-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="ed08e-135">[是]</span><span class="sxs-lookup"><span data-stu-id="ed08e-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="ed08e-136">通知使用者有關元件的字串。</span><span class="sxs-lookup"><span data-stu-id="ed08e-136">A string that informs the user about the component.</span></span> <span data-ttu-id="ed08e-137">空字串為預設值。</span><span class="sxs-lookup"><span data-stu-id="ed08e-137">An empty string is the default.</span></span>|<span data-ttu-id="ed08e-138">否</span><span class="sxs-lookup"><span data-stu-id="ed08e-138">No</span></span>|  
    |`name`|<span data-ttu-id="ed08e-139">代表 Managed 類別的字串。</span><span class="sxs-lookup"><span data-stu-id="ed08e-139">A string that represents the managed class.</span></span>|<span data-ttu-id="ed08e-140">[是]</span><span class="sxs-lookup"><span data-stu-id="ed08e-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="ed08e-141">要用於晚期繫結啟用的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ed08e-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="ed08e-142">否</span><span class="sxs-lookup"><span data-stu-id="ed08e-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="ed08e-143">COM 執行緒模型。</span><span class="sxs-lookup"><span data-stu-id="ed08e-143">The COM threading model.</span></span> <span data-ttu-id="ed08e-144">「兩者」都是預設值。</span><span class="sxs-lookup"><span data-stu-id="ed08e-144">"Both" is the default value.</span></span>|<span data-ttu-id="ed08e-145">否</span><span class="sxs-lookup"><span data-stu-id="ed08e-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="ed08e-146">指定要使用的 Common Language Runtime (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="ed08e-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="ed08e-147">如果您未指定此屬性，而且尚未載入 CLR，則會載入具有 CLR 第 4 版前之最新已安裝 CLR 的元件。</span><span class="sxs-lookup"><span data-stu-id="ed08e-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="ed08e-148">如果您指定 v1.0.3705、v1.1.4322 或 v2.0.50727，版本會自動向前復原至 CLR 版本 4 之前的最新已安裝 CLR 版本 (通常是 v2.0.50727)。</span><span class="sxs-lookup"><span data-stu-id="ed08e-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="ed08e-149">如果已載入另一個版本的 CLR，並且可以透過並存同處理序方式載入指定的版本，則會載入指定的版本；否則，會使用載入的 CLR。</span><span class="sxs-lookup"><span data-stu-id="ed08e-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="ed08e-150">這可能會造成載入失敗。</span><span class="sxs-lookup"><span data-stu-id="ed08e-150">This might cause a load failure.</span></span>|<span data-ttu-id="ed08e-151">否</span><span class="sxs-lookup"><span data-stu-id="ed08e-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="ed08e-152">包含類別類型資訊的類型程式庫識別項。</span><span class="sxs-lookup"><span data-stu-id="ed08e-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="ed08e-153">否</span><span class="sxs-lookup"><span data-stu-id="ed08e-153">No</span></span>|  
  
     <span data-ttu-id="ed08e-154">所有屬性標記都會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ed08e-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="ed08e-155">您可以使用 OLE/COM ObjectViewer (Oleview.exe) 檢視針對組件所匯出的型別程式庫，以取得 CLSID、ProgID、執行緒模型和執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="ed08e-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="ed08e-156">下列元件資訊清單識別兩個類別：`testClass1` 和 `testClass2`。</span><span class="sxs-lookup"><span data-stu-id="ed08e-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  <span data-ttu-id="ed08e-157">儲存並命名資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="ed08e-157">Save and name the manifest file.</span></span> <span data-ttu-id="ed08e-158">元件資訊清單的名稱就是後接 .manifest 副檔名的組件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="ed08e-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="ed08e-159">例如，myManagedComp.dll 是 myManagedComp.manifest。</span><span class="sxs-lookup"><span data-stu-id="ed08e-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="ed08e-160">您必須將元件資訊清單內嵌為組件中的資源。</span><span class="sxs-lookup"><span data-stu-id="ed08e-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="ed08e-161">將元件資訊清單內嵌至 Managed 組件</span><span class="sxs-lookup"><span data-stu-id="ed08e-161">To embed a component manifest in a managed assembly</span></span>  
  
1.  <span data-ttu-id="ed08e-162">建立包含下列陳述式的資源指令碼：</span><span class="sxs-lookup"><span data-stu-id="ed08e-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="ed08e-163">在此陳述式中，`myManagedComp.manifest` 是所內嵌之元件資訊清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed08e-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="ed08e-164">在此範例中，指令碼檔名稱是 `myresource.rc`。</span><span class="sxs-lookup"><span data-stu-id="ed08e-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2.  <span data-ttu-id="ed08e-165">使用 Microsoft Windows 資源編譯器 (Rc.exe) 編譯指令碼。</span><span class="sxs-lookup"><span data-stu-id="ed08e-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="ed08e-166">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ed08e-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="ed08e-167">Rc.exe 會產生 `myresource.res` 資源檔。</span><span class="sxs-lookup"><span data-stu-id="ed08e-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3.  <span data-ttu-id="ed08e-168">重新編譯組件的原始程式檔，然後使用 **/win32res** 選項來指定資源檔：</span><span class="sxs-lookup"><span data-stu-id="ed08e-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="ed08e-169">同樣地，`myresource.res` 是包含內嵌資源之資源檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed08e-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed08e-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed08e-170">See Also</span></span>  
 [<span data-ttu-id="ed08e-171">免註冊的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="ed08e-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
 <span data-ttu-id="ed08e-172">[免註冊的 COM Interop 需求](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ed08e-172">[Requirements for Registration-Free COM Interop](https://msdn.microsoft.com/library/0c43bc57-eecf-4e6c-8114-490141cce4da(v=vs.100)))</span></span>  
 <span data-ttu-id="ed08e-173">[設定免註冊啟動的 COM 元件](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ed08e-173">[Configuring COM Components for Registration-Free Activation](https://msdn.microsoft.com/library/bfe9b02f-d964-4784-960e-a1f94692fbfe(v=vs.100)))</span></span>  
 [<span data-ttu-id="ed08e-174">免註冊啟用 .NET 元件：逐步解說</span><span class="sxs-lookup"><span data-stu-id="ed08e-174">Registration-Free Activation of .NET-Based Components: A Walkthrough</span></span>](https://msdn.microsoft.com/library/ms973915.aspx)
