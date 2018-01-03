---
title: "如何：設定免註冊啟用的 .NET Framework 架構 COM 元件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a704930f707895e7f343566fab544e2f8b32b22c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="deef7-102">如何：設定免註冊啟用的 .NET Framework 架構 COM 元件</span><span class="sxs-lookup"><span data-stu-id="deef7-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="deef7-103">.NET Framework 型元件的免註冊啟用，只比 COM 元件的免註冊啟用略為複雜。</span><span class="sxs-lookup"><span data-stu-id="deef7-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="deef7-104">安裝程式需要兩個資訊清單：</span><span class="sxs-lookup"><span data-stu-id="deef7-104">The setup requires two manifests:</span></span>  
  
-   <span data-ttu-id="deef7-105">COM 應用程式必須有 Win32 樣式應用程式資訊清單，才能識別 Managed 元件。</span><span class="sxs-lookup"><span data-stu-id="deef7-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
-   <span data-ttu-id="deef7-106">.NET Framework 元件必須具有執行階段所需啟用資訊的元件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="deef7-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="deef7-107">本主題描述如何建立應用程式資訊清單與應用程式的關聯、建立元件資訊清單與元件的關聯，以及將元件資訊清單內嵌在組件中。</span><span class="sxs-lookup"><span data-stu-id="deef7-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
### <a name="to-create-an-application-manifest"></a><span data-ttu-id="deef7-108">建立應用程式資訊清單</span><span class="sxs-lookup"><span data-stu-id="deef7-108">To create an application manifest</span></span>  
  
1.  <span data-ttu-id="deef7-109">使用 XML 編輯器，建立 (或修改) COM 應用程式所擁有的應用程式資訊清單，而其與一或多個 Managed 元件交互操作。</span><span class="sxs-lookup"><span data-stu-id="deef7-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2.  <span data-ttu-id="deef7-110">在檔案開頭，插入下列標準標頭：</span><span class="sxs-lookup"><span data-stu-id="deef7-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     <span data-ttu-id="deef7-111">資訊清單的項目和其屬性的相關資訊，請參閱[應用程式資訊清單](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx)。</span><span class="sxs-lookup"><span data-stu-id="deef7-111">For information about manifest elements and their attributes, see [Application Manifests](https://msdn.microsoft.com/library/windows/desktop/aa374191.aspx).</span></span>  
  
3.  <span data-ttu-id="deef7-112">識別資訊清單的擁有者。</span><span class="sxs-lookup"><span data-stu-id="deef7-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="deef7-113">在下列範例中，`myComApp` 第 1 版擁有資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="deef7-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  <span data-ttu-id="deef7-114">識別相依組件。</span><span class="sxs-lookup"><span data-stu-id="deef7-114">Identify dependent assemblies.</span></span> <span data-ttu-id="deef7-115">在下列範例中，`myComApp` 取決於 `myManagedComp`。</span><span class="sxs-lookup"><span data-stu-id="deef7-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
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
  
5.  <span data-ttu-id="deef7-116">儲存並命名資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="deef7-116">Save and name the manifest file.</span></span> <span data-ttu-id="deef7-117">應用程式資訊清單的名稱就是後接 .manifest 副檔名的組件可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="deef7-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="deef7-118">例如，myComApp.exe 的應用程式資訊清單檔案名稱是 myComApp.exe.manifest。</span><span class="sxs-lookup"><span data-stu-id="deef7-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
 <span data-ttu-id="deef7-119">您可以在與 COM 應用程式相同的目錄中安裝應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="deef7-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="deef7-120">或者，您可以將它當成資源新增至應用程式的.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="deef7-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="deef7-121">如需詳細資訊，如需詳細資訊，請參閱[-並存組件的相關](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx)。</span><span class="sxs-lookup"><span data-stu-id="deef7-121">For additional information, For more information, see [About Side-by-Side Assemblies](https://msdn.microsoft.com/library/windows/desktop/ff951640.aspx).</span></span>  
  
#### <a name="to-create-a-component-manifest"></a><span data-ttu-id="deef7-122">建立元件資訊清單</span><span class="sxs-lookup"><span data-stu-id="deef7-122">To create a component manifest</span></span>  
  
1.  <span data-ttu-id="deef7-123">使用 XML 編輯器，建立元件資訊清單以描述 Managed 組件。</span><span class="sxs-lookup"><span data-stu-id="deef7-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2.  <span data-ttu-id="deef7-124">在檔案開頭，插入下列標準標頭：</span><span class="sxs-lookup"><span data-stu-id="deef7-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  <span data-ttu-id="deef7-125">識別檔案的擁有者。</span><span class="sxs-lookup"><span data-stu-id="deef7-125">Identify the owner of the file.</span></span> <span data-ttu-id="deef7-126">應用程式資訊清單檔中 `<dependentAssembly>` 項目的 `<assemblyIdentity>` 項目必須符合元件資訊清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="deef7-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="deef7-127">在下列範例中，`myManagedComp` 版本 1.2.3.4 擁有資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="deef7-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
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
  
4.  <span data-ttu-id="deef7-128">識別組件中的每個類別。</span><span class="sxs-lookup"><span data-stu-id="deef7-128">Identify each class in the assembly.</span></span> <span data-ttu-id="deef7-129">使用 `<clrClass>` 項目，唯一識別 Managed 組件中的每個類別。</span><span class="sxs-lookup"><span data-stu-id="deef7-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="deef7-130">項目 (即 `<assembly>` 項目的子項目) 具有下表所述的屬性。</span><span class="sxs-lookup"><span data-stu-id="deef7-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="deef7-131">屬性</span><span class="sxs-lookup"><span data-stu-id="deef7-131">Attribute</span></span>|<span data-ttu-id="deef7-132">描述</span><span class="sxs-lookup"><span data-stu-id="deef7-132">Description</span></span>|<span data-ttu-id="deef7-133">必要</span><span class="sxs-lookup"><span data-stu-id="deef7-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="deef7-134">指定要啟用之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="deef7-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="deef7-135">[是]</span><span class="sxs-lookup"><span data-stu-id="deef7-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="deef7-136">通知使用者有關元件的字串。</span><span class="sxs-lookup"><span data-stu-id="deef7-136">A string that informs the user about the component.</span></span> <span data-ttu-id="deef7-137">空字串為預設值。</span><span class="sxs-lookup"><span data-stu-id="deef7-137">An empty string is the default.</span></span>|<span data-ttu-id="deef7-138">否</span><span class="sxs-lookup"><span data-stu-id="deef7-138">No</span></span>|  
    |`name`|<span data-ttu-id="deef7-139">代表 Managed 類別的字串。</span><span class="sxs-lookup"><span data-stu-id="deef7-139">A string that represents the managed class.</span></span>|<span data-ttu-id="deef7-140">[是]</span><span class="sxs-lookup"><span data-stu-id="deef7-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="deef7-141">要用於晚期繫結啟用的識別碼。</span><span class="sxs-lookup"><span data-stu-id="deef7-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="deef7-142">否</span><span class="sxs-lookup"><span data-stu-id="deef7-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="deef7-143">COM 執行緒模型。</span><span class="sxs-lookup"><span data-stu-id="deef7-143">The COM threading model.</span></span> <span data-ttu-id="deef7-144">「兩者」都是預設值。</span><span class="sxs-lookup"><span data-stu-id="deef7-144">"Both" is the default value.</span></span>|<span data-ttu-id="deef7-145">否</span><span class="sxs-lookup"><span data-stu-id="deef7-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="deef7-146">指定要使用的 Common Language Runtime (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="deef7-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="deef7-147">如果您未指定此屬性，而且尚未載入 CLR，則會載入具有 CLR 第 4 版前之最新已安裝 CLR 的元件。</span><span class="sxs-lookup"><span data-stu-id="deef7-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="deef7-148">如果您指定 v1.0.3705、v1.1.4322 或 v2.0.50727，版本會自動向前復原至 CLR 版本 4 之前的最新已安裝 CLR 版本 (通常是 v2.0.50727)。</span><span class="sxs-lookup"><span data-stu-id="deef7-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="deef7-149">如果已載入另一個版本的 CLR，並且可以透過並存同處理序方式載入指定的版本，則會載入指定的版本；否則，會使用載入的 CLR。</span><span class="sxs-lookup"><span data-stu-id="deef7-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="deef7-150">這可能會造成載入失敗。</span><span class="sxs-lookup"><span data-stu-id="deef7-150">This might cause a load failure.</span></span>|<span data-ttu-id="deef7-151">否</span><span class="sxs-lookup"><span data-stu-id="deef7-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="deef7-152">包含類別類型資訊的類型程式庫識別項。</span><span class="sxs-lookup"><span data-stu-id="deef7-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="deef7-153">否</span><span class="sxs-lookup"><span data-stu-id="deef7-153">No</span></span>|  
  
     <span data-ttu-id="deef7-154">所有屬性標記都會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="deef7-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="deef7-155">您可以使用 OLE/COM ObjectViewer (Oleview.exe) 檢視針對組件所匯出的型別程式庫，以取得 CLSID、ProgID、執行緒模型和執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="deef7-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="deef7-156">下列元件資訊清單識別兩個類別：`testClass1` 和 `testClass2`。</span><span class="sxs-lookup"><span data-stu-id="deef7-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4" />  
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
  
5.  <span data-ttu-id="deef7-157">儲存並命名資訊清單檔。</span><span class="sxs-lookup"><span data-stu-id="deef7-157">Save and name the manifest file.</span></span> <span data-ttu-id="deef7-158">元件資訊清單的名稱就是後接 .manifest 副檔名的組件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="deef7-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="deef7-159">例如，myManagedComp.dll 是 myManagedComp.manifest。</span><span class="sxs-lookup"><span data-stu-id="deef7-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="deef7-160">您必須將元件資訊清單內嵌為組件中的資源。</span><span class="sxs-lookup"><span data-stu-id="deef7-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="deef7-161">將元件資訊清單內嵌至 Managed 組件</span><span class="sxs-lookup"><span data-stu-id="deef7-161">To embed a component manifest in a managed assembly</span></span>  
  
1.  <span data-ttu-id="deef7-162">建立包含下列陳述式的資源指令碼：</span><span class="sxs-lookup"><span data-stu-id="deef7-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="deef7-163">在此陳述式中，`myManagedComp.manifest` 是所內嵌之元件資訊清單的名稱。</span><span class="sxs-lookup"><span data-stu-id="deef7-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="deef7-164">在此範例中，指令碼檔名稱是 `myresource.rc`。</span><span class="sxs-lookup"><span data-stu-id="deef7-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2.  <span data-ttu-id="deef7-165">使用 Microsoft Windows 資源編譯器 (Rc.exe) 編譯指令碼。</span><span class="sxs-lookup"><span data-stu-id="deef7-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="deef7-166">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="deef7-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="deef7-167">Rc.exe 會產生 `myresource.res` 資源檔。</span><span class="sxs-lookup"><span data-stu-id="deef7-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3.  <span data-ttu-id="deef7-168">重新編譯組件的原始程式檔，然後使用 **/win32res** 選項來指定資源檔：</span><span class="sxs-lookup"><span data-stu-id="deef7-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     <span data-ttu-id="deef7-169">同樣地，`myresource.res` 是包含內嵌資源之資源檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="deef7-169">Again, `myresource.res` is the name of the resource file containing embedded resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deef7-170">請參閱</span><span class="sxs-lookup"><span data-stu-id="deef7-170">See Also</span></span>  
 [<span data-ttu-id="deef7-171">免註冊的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="deef7-171">Registration-Free COM Interop</span></span>](../../../docs/framework/interop/registration-free-com-interop.md)  
 [<span data-ttu-id="deef7-172">免註冊 COM Interop 的需求</span><span class="sxs-lookup"><span data-stu-id="deef7-172">Requirements for Registration-Free COM Interop</span></span>](http://msdn.microsoft.com/en-us/0c43bc57-eecf-4e6c-8114-490141cce4da)  
 [<span data-ttu-id="deef7-173">設定 COM 元件，免註冊啟動</span><span class="sxs-lookup"><span data-stu-id="deef7-173">Configuring COM Components for Registration-Free Activation</span></span>](http://msdn.microsoft.com/en-us/bfe9b02f-d964-4784-960e-a1f94692fbfe)  
 [<span data-ttu-id="deef7-174">免註冊啟用 .NET 元件：逐步解說</span><span class="sxs-lookup"><span data-stu-id="deef7-174">Registration-Free Activation of .NET-Based Components: A Walkthrough</span></span>](http://go.microsoft.com/fwlink/?LinkId=158812)
