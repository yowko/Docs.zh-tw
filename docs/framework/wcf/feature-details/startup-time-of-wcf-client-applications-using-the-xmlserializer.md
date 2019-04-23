---
title: HOW TO：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: b6f010cb5edc3111f05c78f5d27cf178bd501ef9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326420"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="6c7e2-102">HOW TO：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間</span><span class="sxs-lookup"><span data-stu-id="6c7e2-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="6c7e2-103">使用資料型別 (可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化) 的服務和用戶端應用程式會在執行階段針對這些資料型別產生和編譯序列化程式碼，這可能會導致啟動的效能變慢。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c7e2-104">預先產生的序列化程式碼只能用於用戶端應用程式中，而不能用於服務中。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="6c7e2-105">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可改善這些應用程式的啟動效能，藉由從應用程式編譯的組件產生必要的序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="6c7e2-106">Svcutil.exe 會針對已編譯的應用程式組件中可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化的服務合約所使用的所有資料型別，產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="6c7e2-107">使用 <xref:System.Xml.Serialization.XmlSerializer> 的服務和作業合約會標記為 <xref:System.ServiceModel.XmlSerializerFormatAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="6c7e2-108">若要產生 XmlSerializer 序列化程式碼</span><span class="sxs-lookup"><span data-stu-id="6c7e2-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="6c7e2-109">將服務或用戶端程式碼編譯至一或多個組件。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="6c7e2-110">開啟 [SDK 命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="6c7e2-111">在命令提示字元中，使用下列格式啟動 Svcutil.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="6c7e2-112">`assemblyPath` 引數會指定包含服務合約類型之組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="6c7e2-113">Svcutil.exe 會針對已編譯的應用程式組件中可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化的服務合約所使用的所有資料型別，產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="6c7e2-114">Svcutil.exe 只會產生 C# 序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="6c7e2-115">每個輸入組件會產生一個原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="6c7e2-116">您無法使用 **/language**參數來變更產生的程式碼的語言。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="6c7e2-117">若要指定相依組件的路徑，請使用 **/參考**選項。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="6c7e2-118">使用下列其中一個選項，將產生的序列化程式碼提供給應用程式使用：</span><span class="sxs-lookup"><span data-stu-id="6c7e2-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="6c7e2-119">產生的序列化程式碼編譯成名稱的不同組件 [*原始組件*].Xmlserializers.dll (例如，MyApp.XmlSerializers.dll)。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="6c7e2-120">您的應用程式必須能夠載入這個組件，而這個組件必須使用與原始組件相同的金鑰來簽署。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="6c7e2-121">如果要重新編譯原始組件，則必須重新產生序列化組件。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="6c7e2-122">將產生的序列化程式碼編譯至不同的組件，並使用可使用 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> 的服務合約上的 <xref:System.ServiceModel.XmlSerializerFormatAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="6c7e2-123">將 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> 或 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> 屬性設定為指向已編譯的序列化組件。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="6c7e2-124">將產生的序列化程式碼編譯至應用程式組件，並將 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> 加入至可使用 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 的服務合約。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="6c7e2-125">請勿設定 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> 或 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="6c7e2-126">預設的序列化組件會假設為目前的組件。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="6c7e2-127">若要在 Visual Studio 中產生 XmlSerializer 序列化程式碼</span><span class="sxs-lookup"><span data-stu-id="6c7e2-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="6c7e2-128">建立 WCF 服務和用戶端專案在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="6c7e2-129">然後，新增服務參考至用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="6c7e2-130">新增<xref:System.ServiceModel.XmlSerializerFormatAttribute>中的服務合約*reference.cs*下的用戶端應用程式專案中的檔案**serviceReference** -> **reference.svcmap**.</span><span class="sxs-lookup"><span data-stu-id="6c7e2-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="6c7e2-131">請注意，您需要顯示中的所有檔案**方案總管 中**若要查看這些檔案。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="6c7e2-132">建置用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="6c7e2-133">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來建立預先產生的序列化 *.cs*使用命令的檔案：</span><span class="sxs-lookup"><span data-stu-id="6c7e2-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="6c7e2-134">AssemblyPath 引數會指定 WCF 用戶端組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="6c7e2-135">例如：</span><span class="sxs-lookup"><span data-stu-id="6c7e2-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="6c7e2-136">*WCFClient.XmlSerializers.dll.cs*將產生的檔案。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="6c7e2-137">編譯預先產生的序列化組件。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="6c7e2-138">根據上一個步驟中的範例，編譯命令應如下所示：</span><span class="sxs-lookup"><span data-stu-id="6c7e2-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="6c7e2-139">請確定所產生*WCFClient.XmlSerializers.dll*用戶端應用程式，也就是相同的目錄中*WCFClient.exe*在此情況下。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="6c7e2-140">如往常般執行用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-140">Run the client app as usual.</span></span> <span data-ttu-id="6c7e2-141">將使用預先產生的序列化組件。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c7e2-142">範例</span><span class="sxs-lookup"><span data-stu-id="6c7e2-142">Example</span></span>  
 <span data-ttu-id="6c7e2-143">下列命令會針對組件中任何服務合約所使用的 `XmlSerializer` 型別，產生序列化型別。</span><span class="sxs-lookup"><span data-stu-id="6c7e2-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c7e2-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c7e2-144">See also</span></span>

- [<span data-ttu-id="6c7e2-145">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="6c7e2-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
