---
title: "使用動作實作伺服器端行為 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 使用動作實作伺服器端行為
OData 動作可實作一種行為，以依據從 OData 服務擷取的資源而動作。  例如，將數位影片視為資源時，您可以對數位影片進行許多動作：簽出、評比\/加註或簽入。  這些是管理數位影片之 WCF 資料服務可實作的所有動作範例。  動作描述於 OData 回應中，而這個回應包含可叫用動作的資源。  當使用者要求代表數位影片的資源時，從 WCF 資料服務傳回的回應就會包含可用於該項資源之動作的相關資訊。  動作的可用性可能會取決於資料服務或資源的狀態。  例如，一旦數位影片已簽出之後，就無法由其他使用者簽出。  用戶端只要指定 URL，就可以叫用動作。  例如，http:\/\/MyServer\/MovieService.svc\/Movies\(6\) 會識別特定的數位影片，而 http:\/\/MyServer\/MovieService.svc\/Movies\(6\)\/Checkout 會針對特定的影片叫用動作。  動作可讓您公開服務模型，而不公開資料模型。  繼續處理影片服務範例時，您可能會想要讓使用者評比影片，但不直接以資源的形式公開評比資料。  此時，您可以實作評比動作，讓使用者評比影片，但不直接以資源的形式存取評比資料。  
  
 如需實作 WCF 資料服務動作的完整範例，請參閱 [Entity Framework 的 WCF 資料服務動作提供者](http://efactionprovider.codeplex.com/)  
  
## 實作動作  
 若要實作服務動作，您必須實作 <xref:System.IServiceProvider>、<xref:System.Data.Services.Providers.IDataServiceActionProvider> 和 <xref:System.Data.Services.Providers.IDataServiceInvokable> 介面。  <xref:System.IServiceProvider> 可讓 WCF Data Services 取得您的 <xref:System.Data.Services.Providers.IDataServiceActionProvider> 實作。  <xref:System.Data.Services.Providers.IDataServiceActionProvider> 可讓 WCF Data Services 建立、尋找、描述和叫用服務動作。  <xref:System.Data.Services.Providers.IDataServiceInvokable> 可讓您叫用實作服務動作之行為的程式碼，並且取得結果 \(如果有的話\)。  請記住，WCF Data Services 是每次呼叫的 WCF 服務，亦即每次呼叫服務時，都會建立新的服務執行個體。  請確定建立服務時，不會進行任何不必要的工作。  
  
### IServiceProvider  
 <xref:System.IServiceProvider> 包含名為 <xref:System.IServiceProvider.GetService%2A> 的方法。  WCF Data Services 會呼叫此方法來擷取許多服務提供者，包括中繼資料服務提供者和資料服務動作提供者。  當系統要求提供資料服務動作提供者時，請傳回您的 <xref:System.Data.Services.Providers.IDataServiceActionProvider> 實作。  
  
### IDataServiceActionProvider  
 <xref:System.Data.Services.Providers.IDataServiceActionProvider> 包含一些方法，可讓您擷取可用動作的相關資訊。  當您實作 <xref:System.Data.Services.Providers.IDataServiceActionProvider> 時，就會使用動作來擴充服務之 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 實作所定義的服務中繼資料，並且適當地處理這些動作的分派。  
  
#### AdvertiseServiceAction  
 呼叫 <xref:System.Data.Services.Providers.IDataServiceActionProvider.AdvertiseServiceAction%2A> 的目的是要判斷哪些動作可用於指定的資源。  這個方法只會針對非永遠可用的動作呼叫。  它是用來根據所要求之資源的狀態或服務的狀態，檢查動作是否應該包含在 OData 回應中。  這項檢查的完成方式完全由您自行決定。  如果計算可用性相當耗費資源，而且目前資源位於摘要中，則略過檢查並通告動作就是可接受的作法。  如果目前傳回的資源屬於摘要的一部分，`inFeed` 參數就會設定為 `true`。  
  
#### CreateInvokable  
 呼叫 [M:System.Data.Services.Providers.IDataServiceActionProvider.CreateInvokable\(System.Data.Services.DataServiceOperationContext,System.Data.Services.Providers.ServiceAction,System.Object\<xref:System.Data.Services.Providers.IDataServiceActionProvider.CreateInvokable%2A> 的目的是要建立包含委派的 <xref:System.Data.Services.Providers.IDataServiceInvokable>，這個委派會封裝實作動作之行為的程式碼。  這樣會建立 <xref:System.Data.Services.Providers.IDataServiceInvokable> 執行個體，但是不會叫用動作。  WCF 資料服務動作有副作用，而且必須搭配更新提供者運作，才能將這些變更儲存至磁碟。  呼叫 <xref:System.Data.Services.Providers.IDataServiceInvokable.Invoke%2A> 方法是因為呼叫了更新提供者的 SaveChanges\(\) 方法。  
  
#### GetServiceActions  
 這個方法會傳回 <xref:System.Data.Services.Providers.ServiceAction> 執行個體的集合，這些執行個體代表 WCF 資料服務公開的所有動作。  <xref:System.Data.Services.Providers.ServiceAction> 是動作的中繼資料表示，其中包括動作名稱、參數和傳回類型等資訊。  
  
#### GetServiceActionsByBindingParameterType  
 這個方法會傳回所有可繫結至指定繫結參數類型之 <xref:System.Data.Services.Providers.ServiceAction> 執行個體的集合。  也就是說，所有可針對指定之資源類型 \(也稱為繫結參數類型\) 執行的 <xref:System.Data.Services.Providers.ServiceAction>。這個方法是在服務傳回資源時使用，以便加入可針對該項資源叫用之動作的相關資訊。  這個方法應該只會傳回可繫結至確切繫結參數類型 \(無衍生類型\) 的動作。  這個方法是在遇到每種類型時，針對每個要求呼叫一次，而且結果由 WCF Data Services 進行快取。  
  
#### TryResolveServiceAction  
 這個方法會搜尋指定的 <xref:System.Data.Services.Providers.ServiceAction>，而且如果找到 <xref:System.Data.Services.Providers.ServiceAction>，就會傳回 `true`。  如果有找到，就會在 `serviceAction` `out` 參數中傳回 <xref:System.Data.Services.Providers.ServiceAction>。  
  
### IDataServiceInvokable  
 這個介面會提供一種執行 WCF 資料服務動作的方式。  實作 IDataServiceInvokable 時，您必須負責處理 3 件事：  
  
1.  擷取參數，而且可能要封送處理  
  
2.  將參數分派給呼叫 Invoke\(\) 時實際實作動作的程式碼  
  
3.  儲存來自 Invoke\(\) 的任何結果，以便使用 GetResult\(\) 來擷取這些結果  
  
 參數可能會以 Token 的形式傳遞。  這是因為您可以寫入使用代表資源之 Token 的資料服務提供者，如果是這種情況，您可能必須先將這些 Token 轉換 \(封送處理\) 成實際資源，然後再分派給實際動作。  封送處理參數之後，它必須處於可編輯狀態，如此一來，叫用動作時對資源進行的任何變更才會儲存並寫入磁碟。  
  
 這個介面需要兩個方法：Invoke 和 GetResult。  Invoke 會叫用實作動作之行為的委派，而 GetResult 會傳回動作的結果。  
  
## 叫用 WCF 資料服務動作  
 動作是使用 HTTP POST 要求來叫用的。  URL 會依序指定資源和動作名稱。  參數是透過要求的主體傳遞的。  例如，假設有一項名為 MovieService 的服務，而這項服務公開了名為 Rate 的動作。  您就可以使用下列 URL，針對特定的影片叫用 Rate 動作：  
  
 http:\/\/MovieServer\/MovieService.svc\/Movies\(1\)\/Rate  
  
 Movies\(1\) 會指定您想要評比的影片，而 Rate 會指定評比動作。  評比的實際值將位於 HTTP 要求的主體中，如下列範例所示：  
  
```  
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
  
```  
  
> [!WARNING]
>  上述範例程式碼只能搭配支援 JSON Light 的 WCF Data Services 5.2 和更新版本運作。  如果使用舊版 WCF Data Services，您就必須依照下列方式指定 Json 詳細資訊內容類型：`application/json;odata=verbose`。  
  
 或者，您也可以使用 WCF Data Services 用戶端來叫用動作，如下列程式碼片段所示。  
  
```  
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
            //...  
            context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );           
```  
  
 在上述程式碼片段中，`MoviesModel` 類別的產生方式是使用 Visual Studio，加入 WCF 資料服務的服務參考。  
  
## 請參閱  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)   
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [開發和部署 WCF Data Services](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)   
 [自訂資料服務提供者](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)