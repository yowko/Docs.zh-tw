---
title: "HOW TO：使用服務 Moniker 搭配 WSDL 合約 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：使用服務 Moniker 搭配 WSDL 合約
在某些情況中，您可能會想要有完全獨立的 COM Interop 用戶端。您要呼叫的服務可能不會公開 MEX 端點，而且系統可能也不會註冊 COM Interop 的 WCF 用戶端 DLL。在這些情況中，您可以建立 WSDL 檔案，使其描述服務並傳遞至 WCF 服務 Moniker 中。本主題說明如何使用 WCF WSDL Moniker 來呼叫使用者入門 WCF 範例。  
  
### 使用 WSDL 服務 Moniker  
  
1.  開啟和建置 GettingStarted 範例方案。  
  
2.  開啟 Internet Explorer 並瀏覽至 http:\/\/localhost\/ServiceModelSamples\/Service.svc，確定服務正在運作中。  
  
3.  在 Service.cs 檔案中新增 CalculatorService 類別的下列屬性：  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  新增繫結命名空間至服務 App.config：  
  
  
  
5.  建立讓應用程式讀取的 WSDL 檔案。由於在步驟 3 和 4 中已新增命名空間，因此您可以瀏覽至 http:\/\/localhost\/ServiceModelSamples\/Service.svc?wsdl，以使用 IE 來查詢服務的整個 WSDL 描述。然後，您可以從 Internet Explorer 將檔案另存為 serviceWSDL.xml。如果您在步驟 3 和 4 中沒有指定命名空間，藉由查詢上述 URL 而傳回的 WSDL 文件將不會是完整的 WSDL。傳回的 WSDL 文件將包含數個匯入其他 WSDL 文件的匯入陳述式。您必須瀏覽每個匯入陳述式並建置完整的 WSDL 文件，結合從服務傳回的 WSDL 和匯入 WSDL。  
  
6.  開啟 Visual Basic 6.0，並建立新的標準 .exe 檔案。將按鈕新增至表單中，然後按兩下這個按鈕，將下列程式碼新增至 Click 處理常式：  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    >  如果 Moniker 格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
7.  執行 Visual Basic 應用程式。訊息方塊會和呼叫 Subtract\(145, 76.54\) 的結果一起顯示。  
  
## 請參閱  
 [使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [整合 COM 應用程式概觀](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)