---
title: 聯合範例
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144665"
---
# <a name="federation-sample"></a>聯合範例
這個範例將示範聯合安全性。  
  
## <a name="sample-details"></a>範例詳細資料  
 Windows 通信基礎 （WCF） 支援通過 部署聯合安全體系結構`wsFederationHttpBinding`。 `wsFederationHttpBinding` 提供安全、可靠以及可互通的繫結，其中包括使用 HTTP 做為要求/回覆通訊的基礎傳輸機制，以及採用文字/XML 做為編碼的 Wire 格式。 有關 WCF 中的聯合的詳細資訊，請參閱[聯合](../../../../docs/framework/wcf/feature-details/federation.md)。  
  
 本案例由 4 個部分組成：  
  
- BookStore 服務  
  
- BookStore STS  
  
- HomeRealm STS  
  
- BookStore 用戶端  
  
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
  
1. 用戶端使用 Windows 認證，向 HomeRealm STS 驗證。  
  
2. HomeRealm STS 發行可用來向 BookStore STS 進行驗證的權杖。  
  
3. 用戶端使用 HomeRealm STS 所發行的權杖，向 BookStore STS 驗證。  
  
4. BookStore STS 發行可用來向 BookStore 服務進行驗證的權杖。  
  
5. 用戶端使用 BookStore STS 所發行的權杖，向 BookStore 服務驗證。  
  
6. 用戶端會存取 `BuyBook` 作業。  
  
 請參閱下列指示，以了解如何安裝和執行這個範例。  
  
> [!NOTE]
> 您必須具有**對 wwwroot**目錄的寫入權限才能運行此示例。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 開啟 SDK 命令視窗。 在範例的路徑中，執行 Setup.bat。 這會建立範例所需的虛擬目錄，並安裝具有適當權限的必要憑證。  
  
    > [!NOTE]
    > Setup.bat 批次檔是設計用來從 Windows SDK 命令提示字元執行。 它要求 MSSDK 環境變數指向安裝 SDK 的目錄。 這個環境變數是自動在 Windows SDK 命令提示字元中設定。 在 Windows Vista 上，必須確保安裝了 IIS 6.0 管理相容性，因為設置使用 IIS 管理員腳本。 在 Windows Vista 上回合設定腳本需要管理員許可權。  
  
2. 在視覺化工作室中打開聯合樣本.sln，並從 **"生成"** 功能表中選擇 **"生成解決方案**"。 這會建置通用專案檔、Bookstore 服務、Bookstore STS、HomeRealm STS，然後將它們部署在 IIS 中。 還會建置 Bookstore 用戶端應用程式，並將可執行檔 BookStoreClient.exe 放置在 FederationSample\BookStoreClient\bin\Debug 資料夾中。  
  
3. 按兩下 BookStoreClient.exe。 BookStoreClient 視窗隨即顯示。  
  
4. 您可以通過按一下"**流覽書籍"** 來流覽書店中提供的書籍。  
  
5. 要購買特定書籍，請挑選清單中的圖書，然後按一下"**購買書籍**"。 應用程式隨即啟動，然後會使用 Windows 驗證向 HomeRealm 安全性權杖服務進行驗證。  
  
     此範例已設定為允許使用者購買價值在 $15 (含) 以下的書籍。 嘗試購買價值超過 15 美元的書籍，會導致用戶端從「書店服務」(Book Store Service) 收到「拒絕存取」訊息。  
  
    > [!NOTE]
    > 此範例不會在使用者購買之後更新其信用額度限制。 您可以在使用者的 (固定) 信用額度限制以內重複購買書籍。  
  
#### <a name="to-clean-up"></a>若要清除  
  
1. 執行 Cleanup.bat。 這會刪除安裝期間建立的虛擬目錄，也會移除安裝期間所安裝的憑證。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
