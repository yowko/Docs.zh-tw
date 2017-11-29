---
title: "聯合範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b66bf65ba6165902eb90191a262f2715424d8b7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="federation-sample"></a>聯合範例
這個範例將示範聯合安全性。  
  
## <a name="sample-details"></a>範例詳細資料  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 透過 `wsFederationHttpBinding` 提供部署聯合安全性架構的支援。 `wsFederationHttpBinding` 提供安全、可靠以及可互通的繫結，其中包括使用 HTTP 做為要求/回覆通訊的基礎傳輸機制，以及採用文字/XML 做為編碼的 Wire 格式。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]中的同盟[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請參閱[同盟](../../../../docs/framework/wcf/feature-details/federation.md)。  
  
 本案例由 4 個部分組成：  
  
-   BookStore 服務  
  
-   BookStore STS  
  
-   HomeRealm STS  
  
-   BookStore 用戶端  
  
 BookStore 服務支援兩項作業：`BrowseBooks` 和 `BuyBook`。 它允許匿名存取 `BrowseBooks` 作業，但是要求必須有通過驗證的存取權才能存取 `BuyBooks` 作業。 驗證的形式採用 BookStore STS 所發行的權杖。 BookStore 服務的組態檔會使用 `wsFederationHttpBinding`，將用戶端指向 BookStore STS。  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 BookStore STS 接著會要求用戶端使用 HomeRealm STS 所發行的權杖進行驗證。 同樣地，BookStore STS 的組態檔也會使用 `wsFederationHttpBinding`，將用戶端指向 HomeRealm STS。  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 在存取 `BuyBook` 作業時，事件的順序如下：  
  
1.  用戶端使用 Windows 認證，向 HomeRealm STS 驗證。  
  
2.  HomeRealm STS 發行可用來向 BookStore STS 進行驗證的權杖。  
  
3.  用戶端使用 HomeRealm STS 所發行的權杖，向 BookStore STS 驗證。  
  
4.  BookStore STS 發行可用來向 BookStore 服務進行驗證的權杖。  
  
5.  用戶端使用 BookStore STS 所發行的權杖，向 BookStore 服務驗證。  
  
6.  用戶端會存取 `BuyBook` 作業。  
  
 請參閱下列指示，以了解如何安裝和執行這個範例。  
  
> [!NOTE]
>  您必須擁有寫入權限**wwwroot**才能執行此範例的目錄。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  開啟 SDK 命令視窗。 在範例的路徑中，執行 Setup.bat。 這會建立範例所需的虛擬目錄，並安裝具有適當權限的必要憑證。  
  
    > [!NOTE]
    >  Setup.bat 批次檔是設計用來從 Windows SDK 命令提示字元執行。 它要求 MSSDK 環境變數指向安裝 SDK 的目錄。 這個環境變數是自動在 Windows SDK 命令提示字元中設定。 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上，您必須確定已安裝 IIS 6.0 管理相容性，因為安裝會使用 IIS 系統管理員指令碼。 在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上執行安裝指令碼時，需要系統管理員權限。  
  
2.  在 Visual Studio 中開啟 FederationSample.sln，然後選取**建置方案**從**建置**功能表。 這會建置通用專案檔、Bookstore 服務、Bookstore STS、HomeRealm STS，然後將它們部署在 IIS 中。 還會建置 Bookstore 用戶端應用程式，並將可執行檔 BookStoreClient.exe 放置在 FederationSample\BookStoreClient\bin\Debug 資料夾中。  
  
3.  按兩下 BookStoreClient.exe。 BookStoreClient 視窗隨即顯示。  
  
4.  您可以按一下瀏覽書店中的書籍**瀏覽書籍**。  
  
5.  若要購買特定書籍，在清單中選取活頁簿，然後按一下**購買書籍**。 應用程式隨即啟動，然後會使用 Windows 驗證向 HomeRealm 安全性權杖服務進行驗證。  
  
     此範例已設定為允許使用者購買價值在 $15 (含) 以下的書籍。 嘗試購買價值超過 15 美元的書籍，會導致用戶端從「書店服務」(Book Store Service) 收到「拒絕存取」訊息。  
  
    > [!NOTE]
    >  此範例不會在使用者購買之後更新其信用額度限制。 您可以在使用者的 (固定) 信用額度限制以內重複購買書籍。  
  
#### <a name="to-clean-up"></a>若要清除  
  
1.  執行 Cleanup.bat。 這會刪除安裝期間建立的虛擬目錄，也會移除安裝期間所安裝的憑證。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
  
## <a name="see-also"></a>另請參閱
