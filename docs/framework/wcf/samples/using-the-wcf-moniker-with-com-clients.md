---
title: "利用 COM 用戶端使用 WCF Moniker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 79155d68da65a421cf2aec111402b1780743b8e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-wcf-moniker-with-com-clients"></a>利用 COM 用戶端使用 WCF Moniker
這個範例會示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務 Moniker，以將 Web 服務整合至 COM 開發環境，例如 Microsoft Office Visual Basic for Applications (Office VBA) 或 Visual Basic 6.0。 這個範例由 Windows Script Host 用戶端 (.vbs)、支援的用戶端程式庫 (.dll) 和網際網路資訊服務 (IIS) 裝載的服務程式庫 (.dll) 所組成。 服務為計算機服務，而 COM 用戶端會呼叫服務上的數學作業：加法、減法、乘法和除法。 您可以在訊息方塊視窗中看到用戶端活動。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 此服務會實作 `ICalculator` 合約，其定義如下列程式碼範例所示。  
  
```  
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
  
 此範例會示範使用 Moniker 的三個替代方法：  
  
-   型別合約：合約會在用戶端電腦上註冊為 COM 可見型別。  
  
-   WSDL 合約：合約會以 WSDL 文件的形式提供。  
  
-   中繼資料交換合約：會在執行階段從中繼資料交換 (MEX) 端點擷取合約。  
  
## <a name="typed-contract"></a>型別合約  
 若要搭配使用 Moniker 和型別合約，必須使用 COM 適當地註冊服務合約的屬性化型別。 首先，必須使用所產生的用戶端[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 請從用戶端目錄中的命令提示字元執行下列命令，以產生具有型別的 Proxy。  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 這個類別必須包含在專案中，並且專案應該設定為在進行編譯時，產生 COM 可見的簽署組件。 下列屬性應該包含在 AssemblyInfo.cs 檔中。  
  
```  
[assembly: ComVisible(true)]  
```  
  
 建置專案之後，請使用 `regasm` 註冊 COM 可見的型別，如下列範例所示。  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 建立的組件則應該會加入至全域組件快取。 這樣可簡化執行階段尋找組件的程序，不過這不是十分必要的動作。 下列命令會將組件加入至全域組件快取。  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  服務 Moniker 只需要型別註冊，而不會使用 Proxy 與服務進行通訊。  
  
 ComCalcClient.vbs 用戶端應用程式會使用 `GetObject` 函式以建構服務的 Proxy，進而使用服務 Moniker 語法來指定服務的位址、繫結和合約。  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 Moniker 所使用的參數會指定：  
  
-   服務端點的位址。  
  
-   用戶端應該用來連接該端點的繫結。 在此情況下，雖然可以在用戶端組態檔中定義自訂繫結，仍會使用系統定義的 wsHttpBinding。 若要與 Windows Script Host 搭配使用，可在與 Cscript.exe 相同目錄的 Cscript.exe.config 檔中定義自訂繫結。  
  
-   端點所支援的合約型別。 這是上面所產生及註冊的型別。 由於 Visual Basic 指令碼不支援強型別 COM 環境，因此，必須為合約指定識別碼。 此 GUID 是取自 CalcProxy.tlb 的 `interfaceID`，您可以使用 OLE/COM 物件檢視器 (OleView.exe) 這類 COM 工作來檢視 CalcProxy.tlb。 針對 Office VBA 或 Visual Basic 6.0 這類強型別，將明確參考新增至型別程式庫，然後宣告 Proxy 物件的型別，這個動作可用來代替合約參數。 此動作在應用程式開發期間也會提供 IntelliSense 支援。  
  
 使用服務 Moniker 建構 Proxy 執行個體完畢之後，用戶端應用程式就可以針對 Proxy 呼叫方法，使服務 Moniker 基礎結構呼叫對應的服務作業。  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 當您執行範例時，作業回應會顯示在 Windows Script Host 訊息方塊視窗中。 這將示範使用具型別 Moniker 進行 COM 呼叫，以與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務通訊的 COM 用戶端。 就算在用戶端應用程式中使用 COM，服務通訊只能包含 Web 服務呼叫。  
  
## <a name="wsdl-contract"></a>WSDL 合約  
 若要搭配使用 Moniker 和 WSDL 合約，您不需要用戶端程式庫註冊，但必須透過超出範圍之外的機制擷取服務的 WSDL 合約，例如使用瀏覽器存取服務的 WSDL 端點。 Moniker 接著可在執行階段存取該合約。  
  
 ComCalcClient.vbs 用戶端應用程式會使用 `FileSystemObject` 來存取在本機儲存的 WSDL 檔，然後再次使用 `GetObject` 函式來建構服務的 Proxy。  
  
```  
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
  
 Moniker 所使用的參數會指定：  
  
-   服務端點的位址。  
  
-   用戶端應該用來連接該端點的繫結，以及在其中定義該繫結的命名空間。 在此情況中，會使用 `wsHttpBinding_ICalculator`。  
  
-   定義合約的 WSDL。 在此情況中，這是已從 serviceWsdl.xml 檔讀取的字串。  
  
-   合約的名稱與命名空間。 這是必要的識別，因為 WSDL 可能包含多個合約。  
  
    > [!NOTE]
    >  根據預設，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會對每個命名空間產生不同的 WSDL 檔。 而這些檔案則與使用 WSDL 匯入建構相連結。 由於 Moniker 預期使用單一 WSDL 定義，服務必須如同本範例所示範使用單一命名空間，或必須以手動方式合併不同的檔案。  
  
 使用服務 Moniker 建構 Proxy 執行個體完畢之後，用戶端應用程式就可以針對 Proxy 呼叫方法，使服務 Moniker 基礎結構呼叫對應的服務作業。  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 當您執行範例時，作業回應會顯示在 Windows Script Host 訊息方塊視窗中。 這將示範搭配使用 Moniker 和 WSDL 合約進行 COM 呼叫，以與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務通訊的 COM 用戶端。  
  
## <a name="metadata-exchange-contract"></a>中繼資料交換合約  
 若要搭配使用 Moniker 和 MEX 合約，就如同搭配使用 WSDL 合約一樣，將不需要用戶端註冊。 透過內部使用中繼資料交換，即可在執行階段擷取服務合約。  
  
 ComCalcClient.vbs 用戶端應用程式會再次使用 `GetObject` 函式來建構服務的 Proxy。  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 Moniker 所使用的參數會指定：  
  
-   服務中繼資料交換端點的位址。  
  
-   服務端點的位址。  
  
-   用戶端應該用來連接該端點的繫結，以及在其中定義該繫結的命名空間。 在此情況中，會使用 `wsHttpBinding_ICalculator`。  
  
-   合約的名稱與命名空間。 這是必要的識別，因為 WSDL 可能包含多個合約。  
  
 使用服務 Moniker 建構 Proxy 執行個體完畢之後，用戶端應用程式就可以針對 Proxy 呼叫方法，使服務 Moniker 基礎結構呼叫對應的服務作業。  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 當您執行範例時，作業回應會顯示在 Windows Script Host 訊息方塊視窗中。 這將示範搭配使用 Moniker 和 MEX 合約進行 COM 呼叫，以便與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務通訊的 COM 用戶端。  
  
#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 命令提示字元中，開啟語言特定資料夾下的 \client\bin 資料夾。  
  
    > [!NOTE]
    >  如果您是使用 [!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[lserver](../../../../includes/lserver-md.md)]、Windows 7 或 Windows Server 2008 R2，請務必使用系統管理員權限來執行命令提示字元。  
  
4.  在中輸入`tlbexp.exe client.dll /out:CalcProxy.tlb`dll 匯出至 tlb 檔案。 預期會出現「型別程式庫匯出工具警告」，但這不是很重要，因為不需要使用泛型型別。  
  
5.  在中輸入`regasm.exe /tlb:CalcProxy.tlb client.dll`向 COM 註冊型別 預期會出現「型別程式庫匯出工具警告」，但這不是很重要，因為不需要使用泛型型別。  
  
6.  在中輸入`gacutil.exe /i client.dll`加入到全域組件快取的組件。  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>若要在同一部電腦上執行範例  
  
1.  您可以存取服務使用瀏覽器輸入下列位址的測試： `http://localhost/servicemodelsamples/service.svc`。 確認頁面應該會顯示在回應中。  
  
2.  在語言特定資料夾下的 \client 中，執行 ComCalcClient.vbs。 用戶端活動會顯示在訊息方塊視窗中。  
  
3.  如果用戶端和服務無法通訊，請參閱 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
#### <a name="to-run-the-sample-across-computers"></a>若要跨電腦執行範例  
  
1.  在服務電腦上，建立一個名為 ServiceModelSamples 的虛擬目錄。 您可以使用範例隨附的 Setupvroot.bat 指令碼，建立磁碟目錄和虛擬目錄。  
  
2.  將服務程式檔案從 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 複製到服務電腦上的 ServiceModelSamples 虛擬目錄。 請務必將檔案放在 \bin 目錄中。  
  
3.  將語言特定資料夾下 \client 資料夾中的用戶端指令碼檔，複製到用戶端電腦。  
  
4.  在指令碼檔中，變更端點定義的位址值以符合服務的新位址。 以位址中的完整網域名稱取代 "localhost" 的任何參考。  
  
5.  將 WSDL 檔案複製到用戶端電腦。 在 WSDL 檔案 serviceWsdl.xml 中，在位址中以完整網域名稱取代 "localhost" 的任何參考。  
  
6.  將語言特定資料夾下 \client\bin 資料夾的 Client.dll 程式庫，複製到用戶端電腦上的目錄。  
  
7.  從命令提示字元巡覽至用戶端電腦上的目的目錄。 如果使用 [!INCLUDE[wv](../../../../includes/wv-md.md)] 或 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]，請務必使用系統管理員身分執行命令提示字元。  
  
8.  在中輸入`tlbexp.exe client.dll /out:CalcProxy.tlb`dll 匯出至 tlb 檔案。 預期會出現「型別程式庫匯出工具警告」，但這不是很重要，因為不需要使用泛型型別。  
  
9. 在中輸入`regasm.exe /tlb:CalcProxy.tlb client.dll`向 COM 註冊型別 請確定該路徑已設定為包含的資料夾`regasm.exe`執行命令之前。  
  
10. 在中輸入`gacutil.exe /i client.dll`加入到全域組件快取的組件。 請確定該路徑已設定為包含的資料夾`gacutil.exe`執行命令之前。  
  
11. 測試您是否能夠使用瀏覽器，從用戶端電腦存取服務。  
  
12. 在用戶端電腦上，啟動 ComCalcClient.vbs。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
-   基於安全性目的，請在完成範例之後，移除虛擬目錄定義以及安裝步驟中所授與的權限。  
  
## <a name="see-also"></a>另請參閱
