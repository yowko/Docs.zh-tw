---
title: 利用 COM 用戶端使用 WCF Moniker
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 827ea3295bc052f7272eeff241ece10caf5a9704
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624246"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="be881-102">利用 COM 用戶端使用 WCF Moniker</span><span class="sxs-lookup"><span data-stu-id="be881-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="be881-103">此範例示範如何使用 Windows Communication Foundation (WCF) 服務 moniker 將 Web 服務整合至 COM 架構開發環境，例如 Microsoft Office Visual Basic for Applications (Office VBA) 或 Visual Basic 6.0。</span><span class="sxs-lookup"><span data-stu-id="be881-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="be881-104">這個範例由 Windows Script Host 用戶端 (.vbs)、支援的用戶端程式庫 (.dll) 和網際網路資訊服務 (IIS) 裝載的服務程式庫 (.dll) 所組成。</span><span class="sxs-lookup"><span data-stu-id="be881-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="be881-105">服務為計算機服務，而 COM 用戶端會呼叫服務上的數學作業：加法、減法、乘法和除法。</span><span class="sxs-lookup"><span data-stu-id="be881-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="be881-106">您可以在訊息方塊視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="be881-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be881-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="be881-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="be881-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="be881-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="be881-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="be881-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="be881-110">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="be881-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be881-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="be881-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="be881-112">此服務會實作 `ICalculator` 合約，其定義如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="be881-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="be881-113">此範例會示範使用 Moniker 的三個替代方法：</span><span class="sxs-lookup"><span data-stu-id="be881-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="be881-114">型別合約：合約會在用戶端電腦上註冊為 COM 可見型別。</span><span class="sxs-lookup"><span data-stu-id="be881-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="be881-115">WSDL 合約：合約會以 WSDL 文件的形式提供。</span><span class="sxs-lookup"><span data-stu-id="be881-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="be881-116">中繼資料交換合約：會在執行階段從中繼資料交換 (MEX) 端點擷取合約。</span><span class="sxs-lookup"><span data-stu-id="be881-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="be881-117">型別合約</span><span class="sxs-lookup"><span data-stu-id="be881-117">Typed Contract</span></span>  
 <span data-ttu-id="be881-118">若要搭配使用 Moniker 和型別合約，必須使用 COM 適當地註冊服務合約的屬性化型別。</span><span class="sxs-lookup"><span data-stu-id="be881-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="be881-119">首先，必須使用所產生的用戶端[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="be881-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="be881-120">請從用戶端目錄中的命令提示字元執行下列命令，以產生具有型別的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="be881-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="be881-121">這個類別必須包含在專案中，並且專案應該設定為在進行編譯時，產生 COM 可見的簽署組件。</span><span class="sxs-lookup"><span data-stu-id="be881-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="be881-122">下列屬性應該包含在 AssemblyInfo.cs 檔中。</span><span class="sxs-lookup"><span data-stu-id="be881-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="be881-123">建置專案之後，請使用 `regasm` 註冊 COM 可見的型別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="be881-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="be881-124">建立的組件則應該會加入至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="be881-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="be881-125">這樣可簡化執行階段尋找組件的程序，不過這不是十分必要的動作。</span><span class="sxs-lookup"><span data-stu-id="be881-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="be881-126">下列命令會將組件加入至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="be881-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="be881-127">服務 Moniker 只需要型別註冊，而不會使用 Proxy 與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="be881-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="be881-128">ComCalcClient.vbs 用戶端應用程式會使用 `GetObject` 函式以建構服務的 Proxy，進而使用服務 Moniker 語法來指定服務的位址、繫結和合約。</span><span class="sxs-lookup"><span data-stu-id="be881-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="be881-129">Moniker 所使用的參數會指定：</span><span class="sxs-lookup"><span data-stu-id="be881-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="be881-130">服務端點的位址。</span><span class="sxs-lookup"><span data-stu-id="be881-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="be881-131">用戶端應該用來連接該端點的繫結。</span><span class="sxs-lookup"><span data-stu-id="be881-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="be881-132">在此情況下，雖然可以在用戶端組態檔中定義自訂繫結，仍會使用系統定義的 wsHttpBinding。</span><span class="sxs-lookup"><span data-stu-id="be881-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="be881-133">若要與 Windows Script Host 搭配使用，可在與 Cscript.exe 相同目錄的 Cscript.exe.config 檔中定義自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="be881-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="be881-134">端點所支援的合約型別。</span><span class="sxs-lookup"><span data-stu-id="be881-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="be881-135">這是上面所產生及註冊的型別。</span><span class="sxs-lookup"><span data-stu-id="be881-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="be881-136">由於 Visual Basic 指令碼不支援強型別 COM 環境，因此，必須為合約指定識別碼。</span><span class="sxs-lookup"><span data-stu-id="be881-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="be881-137">此 GUID 是取自 CalcProxy.tlb 的 `interfaceID`，您可以使用 OLE/COM 物件檢視器 (OleView.exe) 這類 COM 工作來檢視 CalcProxy.tlb。</span><span class="sxs-lookup"><span data-stu-id="be881-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="be881-138">針對 Office VBA 或 Visual Basic 6.0 這類強型別，將明確參考新增至型別程式庫，然後宣告 Proxy 物件的型別，這個動作可用來代替合約參數。</span><span class="sxs-lookup"><span data-stu-id="be881-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="be881-139">此動作在應用程式開發期間也會提供 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="be881-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="be881-140">使用服務 Moniker 建構 Proxy 執行個體完畢之後，用戶端應用程式就可以針對 Proxy 呼叫方法，使服務 Moniker 基礎結構呼叫對應的服務作業。</span><span class="sxs-lookup"><span data-stu-id="be881-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 當您執行範例時，作業回應會顯示在 Windows Script Host 訊息方塊視窗中。 這示範了 COM 用戶端進行通訊的 WCF 服務使用具型別的 moniker 進行 COM 呼叫。 <span data-ttu-id="be881-143">就算在用戶端應用程式中使用 COM，服務通訊只能包含 Web 服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="be881-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="be881-144">WSDL 合約</span><span class="sxs-lookup"><span data-stu-id="be881-144">WSDL Contract</span></span>  
 <span data-ttu-id="be881-145">若要搭配使用 Moniker 和 WSDL 合約，您不需要用戶端程式庫註冊，但必須透過超出範圍之外的機制擷取服務的 WSDL 合約，例如使用瀏覽器存取服務的 WSDL 端點。</span><span class="sxs-lookup"><span data-stu-id="be881-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="be881-146">Moniker 接著可在執行階段存取該合約。</span><span class="sxs-lookup"><span data-stu-id="be881-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="be881-147">ComCalcClient.vbs 用戶端應用程式會使用 `FileSystemObject` 來存取在本機儲存的 WSDL 檔，然後再次使用 `GetObject` 函式來建構服務的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="be881-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="be881-148">Moniker 所使用的參數會指定：</span><span class="sxs-lookup"><span data-stu-id="be881-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="be881-149">服務端點的位址。</span><span class="sxs-lookup"><span data-stu-id="be881-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="be881-150">用戶端應該用來連接該端點的繫結，以及在其中定義該繫結的命名空間。</span><span class="sxs-lookup"><span data-stu-id="be881-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="be881-151">在此情況中，會使用 `wsHttpBinding_ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="be881-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="be881-152">定義合約的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="be881-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="be881-153">在此情況中，這是已從 serviceWsdl.xml 檔讀取的字串。</span><span class="sxs-lookup"><span data-stu-id="be881-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="be881-154">合約的名稱與命名空間。</span><span class="sxs-lookup"><span data-stu-id="be881-154">The name and namespace of the contract.</span></span> <span data-ttu-id="be881-155">這是必要的識別，因為 WSDL 可能包含多個合約。</span><span class="sxs-lookup"><span data-stu-id="be881-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be881-156">根據預設，WCF 服務會產生不同的 WSDL 檔案，每個命名空間的使用。</span><span class="sxs-lookup"><span data-stu-id="be881-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="be881-157">而這些檔案則與使用 WSDL 匯入建構相連結。</span><span class="sxs-lookup"><span data-stu-id="be881-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="be881-158">由於 Moniker 預期使用單一 WSDL 定義，服務必須如同本範例所示範使用單一命名空間，或必須以手動方式合併不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="be881-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="be881-159">使用服務 Moniker 建構 Proxy 執行個體完畢之後，用戶端應用程式就可以針對 Proxy 呼叫方法，使服務 Moniker 基礎結構呼叫對應的服務作業。</span><span class="sxs-lookup"><span data-stu-id="be881-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 當您執行範例時，作業回應會顯示在 Windows Script Host 訊息方塊視窗中。 <span data-ttu-id="be881-161">這示範了 COM 用戶端進行通訊的 WCF 服務搭配使用 moniker 和 WSDL 合約的 COM 呼叫。</span><span class="sxs-lookup"><span data-stu-id="be881-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="be881-162">中繼資料交換合約</span><span class="sxs-lookup"><span data-stu-id="be881-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="be881-163">若要搭配使用 Moniker 和 MEX 合約，就如同搭配使用 WSDL 合約一樣，將不需要用戶端註冊。</span><span class="sxs-lookup"><span data-stu-id="be881-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="be881-164">透過內部使用中繼資料交換，即可在執行階段擷取服務合約。</span><span class="sxs-lookup"><span data-stu-id="be881-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="be881-165">ComCalcClient.vbs 用戶端應用程式會再次使用 `GetObject` 函式來建構服務的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="be881-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="be881-166">Moniker 所使用的參數會指定：</span><span class="sxs-lookup"><span data-stu-id="be881-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="be881-167">服務中繼資料交換端點的位址。</span><span class="sxs-lookup"><span data-stu-id="be881-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="be881-168">服務端點的位址。</span><span class="sxs-lookup"><span data-stu-id="be881-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="be881-169">用戶端應該用來連接該端點的繫結，以及在其中定義該繫結的命名空間。</span><span class="sxs-lookup"><span data-stu-id="be881-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="be881-170">在此情況中，會使用 `wsHttpBinding_ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="be881-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="be881-171">合約的名稱與命名空間。</span><span class="sxs-lookup"><span data-stu-id="be881-171">The name and namespace of the contract.</span></span> <span data-ttu-id="be881-172">這是必要的識別，因為 WSDL 可能包含多個合約。</span><span class="sxs-lookup"><span data-stu-id="be881-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="be881-173">使用服務 Moniker 建構 Proxy 執行個體完畢之後，用戶端應用程式就可以針對 Proxy 呼叫方法，使服務 Moniker 基礎結構呼叫對應的服務作業。</span><span class="sxs-lookup"><span data-stu-id="be881-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 當您執行範例時，作業回應會顯示在 Windows Script Host 訊息方塊視窗中。 <span data-ttu-id="be881-175">這示範了 COM 用戶端進行通訊的 WCF 服務搭配使用 moniker 和 MEX 合約的 COM 呼叫。</span><span class="sxs-lookup"><span data-stu-id="be881-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="be881-176">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="be881-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="be881-177">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="be881-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="be881-178">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="be881-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="be881-179">從開發人員命令提示字元中適用於 Visual Studio，開啟語言特定資料夾下 \client\bin 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="be881-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be881-180">如果您是使用 [!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[lserver](../../../../includes/lserver-md.md)]、Windows 7 或 Windows Server 2008 R2，請務必使用系統管理員權限來執行命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="be881-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="be881-181">輸入`tlbexp.exe client.dll /out:CalcProxy.tlb`dll 匯出至 tlb 檔案。</span><span class="sxs-lookup"><span data-stu-id="be881-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="be881-182">預期會出現「型別程式庫匯出工具警告」，但這不是很重要，因為不需要使用泛型型別。</span><span class="sxs-lookup"><span data-stu-id="be881-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="be881-183">輸入`regasm.exe /tlb:CalcProxy.tlb client.dll`向 COM 註冊型別</span><span class="sxs-lookup"><span data-stu-id="be881-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="be881-184">預期會出現「型別程式庫匯出工具警告」，但這不是很重要，因為不需要使用泛型型別。</span><span class="sxs-lookup"><span data-stu-id="be881-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="be881-185">輸入`gacutil.exe /i client.dll`加入到全域組件快取的組件。</span><span class="sxs-lookup"><span data-stu-id="be881-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="be881-186">若要在同一部電腦上執行範例</span><span class="sxs-lookup"><span data-stu-id="be881-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="be881-187">您可以使用瀏覽器輸入下列位址的服務的測試： `http://localhost/servicemodelsamples/service.svc`。</span><span class="sxs-lookup"><span data-stu-id="be881-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="be881-188">確認頁面應該會顯示在回應中。</span><span class="sxs-lookup"><span data-stu-id="be881-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="be881-189">在語言特定資料夾下的 \client 中，執行 ComCalcClient.vbs。</span><span class="sxs-lookup"><span data-stu-id="be881-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="be881-190">用戶端活動會顯示在訊息方塊視窗中。</span><span class="sxs-lookup"><span data-stu-id="be881-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="be881-191">如果用戶端和服務能夠進行通訊，請參閱[的 WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="be881-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="be881-192">若要跨電腦執行範例</span><span class="sxs-lookup"><span data-stu-id="be881-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="be881-193">在服務電腦上，建立一個名為 ServiceModelSamples 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="be881-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="be881-194">您可以使用範例隨附的 Setupvroot.bat 指令碼，建立磁碟目錄和虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="be881-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="be881-195">將服務程式檔案從 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 複製到服務電腦上的 ServiceModelSamples 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="be881-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="be881-196">請務必將檔案放在 \bin 目錄中。</span><span class="sxs-lookup"><span data-stu-id="be881-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="be881-197">將語言特定資料夾下 \client 資料夾中的用戶端指令碼檔，複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="be881-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="be881-198">在指令碼檔中，變更端點定義的位址值以符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="be881-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="be881-199">以位址中的完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="be881-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="be881-200">將 WSDL 檔案複製到用戶端電腦。</span><span class="sxs-lookup"><span data-stu-id="be881-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="be881-201">在 WSDL 檔案 serviceWsdl.xml 中，在位址中以完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="be881-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="be881-202">將語言特定資料夾下 \client\bin 資料夾的 Client.dll 程式庫，複製到用戶端電腦上的目錄。</span><span class="sxs-lookup"><span data-stu-id="be881-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="be881-203">從命令提示字元巡覽至用戶端電腦上的目的目錄。</span><span class="sxs-lookup"><span data-stu-id="be881-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="be881-204">如果使用 [!INCLUDE[wv](../../../../includes/wv-md.md)] 或 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]，請務必使用系統管理員身分執行命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="be881-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="be881-205">輸入`tlbexp.exe client.dll /out:CalcProxy.tlb`dll 匯出至 tlb 檔案。</span><span class="sxs-lookup"><span data-stu-id="be881-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="be881-206">預期會出現「型別程式庫匯出工具警告」，但這不是很重要，因為不需要使用泛型型別。</span><span class="sxs-lookup"><span data-stu-id="be881-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="be881-207">輸入`regasm.exe /tlb:CalcProxy.tlb client.dll`向 COM 註冊型別</span><span class="sxs-lookup"><span data-stu-id="be881-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="be881-208">請確定該路徑已設定為包含的資料夾`regasm.exe`執行命令之前。</span><span class="sxs-lookup"><span data-stu-id="be881-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="be881-209">輸入`gacutil.exe /i client.dll`加入到全域組件快取的組件。</span><span class="sxs-lookup"><span data-stu-id="be881-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="be881-210">請確定該路徑已設定為包含的資料夾`gacutil.exe`執行命令之前。</span><span class="sxs-lookup"><span data-stu-id="be881-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="be881-211">測試您是否能夠使用瀏覽器，從用戶端電腦存取服務。</span><span class="sxs-lookup"><span data-stu-id="be881-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="be881-212">在用戶端電腦上，啟動 ComCalcClient.vbs。</span><span class="sxs-lookup"><span data-stu-id="be881-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="be881-213">若要在使用範例之後進行清除</span><span class="sxs-lookup"><span data-stu-id="be881-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="be881-214">基於安全性目的，請在完成範例之後，移除虛擬目錄定義以及安裝步驟中所授與的權限。</span><span class="sxs-lookup"><span data-stu-id="be881-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
