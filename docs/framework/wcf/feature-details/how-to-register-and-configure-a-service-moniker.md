---
title: HOW TO：註冊和設定服務 Moniker
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52b3ec27560ca2dc47b7951cb209f33f307fa7ea
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="13a35-102">HOW TO：註冊和設定服務 Moniker</span><span class="sxs-lookup"><span data-stu-id="13a35-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="13a35-103">在具有型別之合約的 COM 應用程式中使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務 Moniker 之前，您必須使用 COM 註冊必要的屬性化型別，並以必要的繫結組態設定 COM 應用程式和 Moniker。</span><span class="sxs-lookup"><span data-stu-id="13a35-103">Before using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="13a35-104">使用 COM 註冊必要的屬性化型別</span><span class="sxs-lookup"><span data-stu-id="13a35-104">To register the required attributed types with COM</span></span>  
  
1.  <span data-ttu-id="13a35-105">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具，可擷取中繼資料合約，從[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="13a35-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="13a35-106">這樣做會產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件的原始程式碼和用戶端應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="13a35-106">This generates the source code for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly and a client application configuration file.</span></span>  
  
2.  <span data-ttu-id="13a35-107">請確定組件中的型別已標示為 `ComVisible`。</span><span class="sxs-lookup"><span data-stu-id="13a35-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="13a35-108">若要這樣做，請在 Visual Studio 專案中將下列屬性新增至 AssemblyInfo.cs 檔。</span><span class="sxs-lookup"><span data-stu-id="13a35-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  <span data-ttu-id="13a35-109">將 Managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端編譯為強式名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="13a35-109">Compile the managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as a strong-named assembly.</span></span> <span data-ttu-id="13a35-110">這樣做將需要以密碼金鑰組 (Key Pairs) 進行簽署。</span><span class="sxs-lookup"><span data-stu-id="13a35-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="13a35-111">如需詳細資訊，請參閱[簽署以強式名稱組件](http://go.microsoft.com/fwlink/?LinkId=94874).NET 開發人員指南中。</span><span class="sxs-lookup"><span data-stu-id="13a35-111">For more information, see [Signing an Assembly with a Strong Name](http://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4.  <span data-ttu-id="13a35-112">使用組件註冊 (Regasm.exe) 工具並搭配 `/tlb` 選項，以使用 COM 註冊組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="13a35-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5.  <span data-ttu-id="13a35-113">使用全域組件快取 (Gacutil.exe) 工具，將組件新增至全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="13a35-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13a35-114">簽署組件並將該組件新增至全域組件快取都是選用性步驟，但這兩個步驟可以簡化在執行階段時，從正確的位置載入組件的程序。</span><span class="sxs-lookup"><span data-stu-id="13a35-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="13a35-115">使用必要的繫結組態設定 COM 應用程式和 Moniker</span><span class="sxs-lookup"><span data-stu-id="13a35-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="13a35-116">將繫結定義 (所產生[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)產生的用戶端應用程式組態檔中) 用戶端應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="13a35-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="13a35-117">例如，若是名稱為 CallCenterClient.exe 的 Visual Basic 6.0 可執行檔，應該將組態放置在與可執行檔相同之目錄內的 CallCenterConfig.exe.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="13a35-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="13a35-118">用戶端應用程式現在就可使用 Moniker。</span><span class="sxs-lookup"><span data-stu-id="13a35-118">The client application can now use the moniker.</span></span> <span data-ttu-id="13a35-119">請注意，如果使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的其中一種標準繫結型別，則不需要繫結組態。</span><span class="sxs-lookup"><span data-stu-id="13a35-119">Note that the binding configuration is not required if using one of the standard binding types provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
     <span data-ttu-id="13a35-120">接著會註冊下列型別。</span><span class="sxs-lookup"><span data-stu-id="13a35-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="13a35-121">已使用 `wsHttpBinding` 繫結公開應用程式。</span><span class="sxs-lookup"><span data-stu-id="13a35-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="13a35-122">針對提供的型別和應用程式組態，將會使用下列範例 Moniker 字串。</span><span class="sxs-lookup"><span data-stu-id="13a35-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="13a35-123">在將參考新增至包含 `IMathService` 型別的組件之後，您就可以從 Visual Basic 6.0 應用程式中使用這些 Moniker 字串，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="13a35-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="13a35-124">在這個範例中，針對用戶端應用程式將繫結組態 `Binding1` 的定義存放在適當命名的組態檔中，例如 vb6appname.exe.config。</span><span class="sxs-lookup"><span data-stu-id="13a35-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13a35-125">您可以在 C#、C++ 或其他 .NET 語言應用程式中使用類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="13a35-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13a35-126">：如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。</span><span class="sxs-lookup"><span data-stu-id="13a35-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="13a35-127">如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。</span><span class="sxs-lookup"><span data-stu-id="13a35-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="13a35-128">雖然本主題著重於從 VB 6.0 程式碼中使用服務 Moniker，但您也可以使用其他語言中的服務 Moniker。</span><span class="sxs-lookup"><span data-stu-id="13a35-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="13a35-129">從 C++ 程式碼中使用 Moniker 時，應該以 "no_namespace named_guids raw_interfaces_only" 這個名稱匯入 Svcutil.exe 產生的組件，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="13a35-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="13a35-130">這樣會修改匯入的介面定義，讓所有方法都會傳回 `HResult`。</span><span class="sxs-lookup"><span data-stu-id="13a35-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="13a35-131">其他傳回值都會轉換為 Out 參數。</span><span class="sxs-lookup"><span data-stu-id="13a35-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="13a35-132">整體的執行方法仍然相同。</span><span class="sxs-lookup"><span data-stu-id="13a35-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="13a35-133">這樣可讓您在 Proxy 上呼叫方法時，判斷發生例外狀況的原因。</span><span class="sxs-lookup"><span data-stu-id="13a35-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="13a35-134">不過這個功能只能用於 C++ 程式碼。</span><span class="sxs-lookup"><span data-stu-id="13a35-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a35-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13a35-135">See Also</span></span>  
 [<span data-ttu-id="13a35-136">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="13a35-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
