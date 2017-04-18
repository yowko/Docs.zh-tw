---
title: "網際網路資訊服務裝載最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0834768e-9665-46bf-86eb-d4b09ab91af5
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# 網際網路資訊服務裝載最佳做法
本主題將概述裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的一些最佳做法。  
  
## 將 WCF 服務實作為 DLL  
 將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務實作為 DLL 以部署至 Web 應用程式的 \\bin 目錄可讓您在 Web 應用程式模型以外的環境 \(例如，一個可能尚未部署網際網路資訊服務 \(IIS\) 的測試環境\) 重複使用服務。  
  
## IIS 裝載應用程式中的服務主機  
 請勿使用命令式自我裝載 API 來建立可接聽網路傳輸 \(原本並非由 IIS 裝載環境所支援\) 的新服務主機 \(例如，請勿使用 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 來裝載 TCP 服務，因為 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] 原本並不支援 TCP 通訊\)。我們不建議您使用這個方式。IIS 裝載環境無法辨識以命令式語法建立的服務主機。關鍵在於，當 IIS 判斷裝載應用程式集區是否為閒置時，不會考慮透過命令式語法建立的服務所執行的處理作業。而且內含此類以命令式語法建立之服務主機的應用程式，會透過 IIS 裝載環境強勢地處理 IIS 裝載處理序。  
  
## URI 和 IIS 裝載端點  
 IIS 裝載服務的端點應該透過相對的統一資源識別元 \(URI\)，而不是絕對位址來設定。這樣可保證端點位址落在屬於裝載應用程式的 URI 位址範圍內，並確保訊息式啟動會如預期般發生。  
  
## 狀態管理與處理序回收  
 IIS 裝載環境已經針對無法在記憶體中保留本機狀態的服務進行最佳化。IIS 會回收主機處理序以回應一系列不同的外部與內部事件，導致任何唯一存在記憶體中的變動性 \(Volatile\) 狀態遺失。IIS 裝載的服務應該會將其狀態儲存到處理序外部 \(例如，儲存在資料庫中\) 或是儲存到記憶體中的快取，以便在發生應用程式回收事件時可以輕易地重新建立。  
  
> [!NOTE]
>  用來做為訊息層可靠性與安全性的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通訊協定會利用動態的記憶體中狀態。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可靠工作階段與安全性工作階段可能會因為應用程式回收的緣故而無預警地終止。使用這些通訊協定的 IIS 裝載應用程式應該仰賴 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供的工作階段金鑰以外的金鑰來關聯應用程式層級狀態 \(例如，應用程式層級建構或自訂相互關聯標頭\)，或是停用裝載應用程式的 IIS 處理序回收作業。  
  
## 最佳化中介層案例中的效能  
 為了在「*中介層案例*」\(Middle\-Tier Scenario\) \(呼叫其他服務以回應傳入訊息的服務\) 中求得最佳效能，您可以針對遠端服務產生一次 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務用戶端，然後在多項傳入要求中重複加以使用。產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務用戶端是一項耗時的作業 \(相對於對預先存在的用戶端執行個體執行服務呼叫而言\)，而中介層案例則會藉由快取不同要求之間的遠端服務端來產生一些獨特的效能。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務用戶端是安全的執行緒，因此您不需要同步存取多個執行緒上的用戶端。  
  
 中介層案例同時會因為使用 `svcutil /a` 選項所產生的非同步 API 而產生一些效能。`/a` 選項會導致 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 為每個服務作業產生 `BeginXXX/EndXXX` 方法，以便允許在背景執行緒中針對遠端服務進行長期執行的呼叫。  
  
## 多重主目錄系統或多重具名案例中的 WCF  
 您可以在 IIS Web 伺服陣列中部署 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，讓當中的一群電腦共用通用外部名稱 \(例如，http:\/\/www.contoso.com\)，但是加上個別主機名稱的位址 \(例如，http:\/\/www.contoso.com 可能會將流量分別導向兩個名為 http:\/\/machine1.internal.contoso.com 和 http:\/\/machine2.internal.contoso.com 的電腦上\)。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 完全支援這個部署案例，但是需要裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之 IIS 網站的特殊組態，以便在服務的中繼資料 \(Web 服務描述語言\) 中顯示正確的 \(外部\) 主機名稱。  
  
 為了確保 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所產生的服務中繼資料會顯示正確的主機名稱，請將裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的 IIS 網站設為預設的身分識別以使用明確的主機名稱。例如，駐留在 www.contoso.com 伺服器陣列中的電腦應該搭配適當的 IIS 網站繫結 \(HTTP 使用 \*:80:www.contoso.com，而 HTTPS 則使用 \*:443:www.contoso.com\)。  
  
 您可以使用 IIS Microsoft Management Console \(MMC\) 嵌入式管理單元來設定 IIS 網站繫結。  
  
## 在不同使用者內容中執行的應用程式集區會覆寫來自暫存資料夾裡其他帳戶的組件  
 為了確保在不同使用者內容中執行的應用程式集區無法覆寫來自 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 暫存檔案資料夾中其他帳戶的組件，請針對不同的應用程式使用不同的身分識別與暫存資料夾。例如，如果您有兩個虛擬應用程式 \(\/Application1 和 \/ Application2\)，則可以使用兩個不同的身分識別來建立兩個應用程式集區 \(A 和 B\)。應用程式集區 A 可以使用某個使用者身分識別 \(user1\) 來執行，而應用程式集區 B 則可透過另一個使用者身分識別 \(user2\) 來執行，同時設定 \/Application1 來使用 A 並設定 \/Application2 來使用 B。  
  
 在 Web.config 中，您可以使用 \<system.web\/compilation\/@tempFolder\> 來設定暫存資料夾。如果是 \/Application1，則可能為 “c:\\tempForUser1”；如果是 application2，則可能是 "c:\\tempForUser2"。針對這些資料夾賦予兩個身分識別對應的寫入權限。  
  
 這樣一來，user2 將無法變更 \/application2 \(位於 c:\\tempForUser1 底下\) 的程式碼產生資料夾。  
  
## 啟用非同步處理  
 根據預設，當訊息傳送至 IIS 6.0 和之前版本之下裝載的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，會以同步方式處理訊息。ASP.NET 對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的呼叫是交付予自己的執行緒 \(ASP.NET 背景工作執行緒\)，而 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 則使用另一個執行緒來處理要求。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會暫止 ASP.NET 背景工作執行緒，直到其本身完成處理。這將致使同步處理要求。若以非同步方式處理要求，便能減少處理要求所需的執行緒數目，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在處理要求時並不會暫止 ASP.NET 執行緒，從而可提高延展性。執行 IIS 6.0 的電腦不建議採用非同步方式，因為伺服器將無法遏止傳入要求發動「*阻斷服務*」\(Denial Of Service，DOS\) 攻擊。從 IIS 7.0 開始，則已引進了同時並存要求節流閥：`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0]“MaxConcurrentRequestsPerCpu`。有了這個新的節流閥，便能放心地使用非同步處理。預設在 IIS 7.0 中，非同步處理常式和模組要經過登錄。如果這已經遭到關閉，您可以在應用程式的 Web.config 檔案中手動啟用非同步處理要求。應該使用何種設定，取決於您的 `aspNetCompatibilityEnabled` 設定。若您已將 `aspNetCompatibilityEnabled` 設定為 `false`，請依下列組態程式碼片段所示，設定 <xref:System.ServiceModel.Activation.ServiceHttpModule>。  
  
```  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="false" />      
  </system.serviceModel>  
  <system.webServer>  
    <modules>  
      <remove name="ServiceModel"/>  
      <add name="ServiceModel"   
           preCondition="integratedMode,runtimeVersionv2.0"   
           type="System.ServiceModel.Activation.ServiceHttpModule, System.ServiceModel,Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
    </modules>  
    </system.webServer>  
  
```  
  
 若您已將 `aspNetCompatibilityEnabled` 設定為 `true`，請依下列組態程式碼片段所示，設定 <xref:System.ServiceModel.Activation.ServiceHttpHandlerFactory>。  
  
```  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />      
  </system.serviceModel>  
  <system.webServer>  
    <handlers>  
          <clear/>  
          <add name="TestAsyncHttpHandler"   
               path="*.svc"   
               verb="*"   
               type="System.ServiceModel.Activation.ServiceHttpHandlerFactory, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"           
               />  
    </handlers>      
  </system.webServer>  
  
```  
  
## 請參閱  
 [Service Hosting Samples](http://msdn.microsoft.com/zh-tw/f703a3f6-0fba-418a-a92f-7ce75ccfa47e)   
 [Windows Server AppFabric 主控功能](http://go.microsoft.com/fwlink/?LinkId=201276)