---
title: 使用動作實作伺服器端行為
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 5c71cfe8965cf8edbe07ff7ae4c6be95b437bf80
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894263"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>使用動作實作伺服器端行為

OData 動作可實作一種行為，以依據從 OData 服務擷取的資源而動作。 例如，將數位影片視為資源時，您可以對數位影片進行許多動作：簽出、評比/加註或簽入。 這些是管理數位影片之 WCF 資料服務可實作的所有動作範例。 動作描述於 OData 回應中，而這個回應包含可叫用動作的資源。 當使用者要求代表數位影片的資源時，從 WCF 資料服務傳回的回應就會包含可用於該項資源之動作的相關資訊。 動作的可用性可能會取決於資料服務或資源的狀態。 例如，一旦數位影片已簽出之後，就無法由其他使用者簽出。 用戶端只要指定 URL，就可以叫用動作。 例如， `http://MyServer/MovieService.svc/Movies(6)`會識別特定的數位電影，並`http://MyServer/MovieService.svc/Movies(6)/Checkout`在特定電影上叫用動作。 動作可讓您公開服務模型，而不公開資料模型。 繼續處理影片服務範例時，您可能會想要讓使用者評比影片，但不直接以資源的形式公開評比資料。 此時，您可以實作評比動作，讓使用者評比影片，但不直接以資源的形式存取評比資料。
  
## <a name="implementing-an-action"></a>實作動作  
 若要執行服務動作<xref:System.IServiceProvider>，您必須執行、 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))和[IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103))介面。 <xref:System.IServiceProvider>允許 WCF Data Services 取得[IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))的執行。 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))可讓 WCF Data Services 建立、尋找、描述和叫用服務動作。 [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103))可讓您叫用用來執行服務動作行為的程式碼，並取得結果（如果有的話）。 請記住，WCF Data Services 是每次呼叫的 WCF 服務，亦即每次呼叫服務時，都會建立新的服務執行個體。  請確定建立服務時，不會進行任何不必要的工作。  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider> 包含名為 <xref:System.IServiceProvider.GetService%2A> 的方法。 WCF Data Services 會呼叫此方法來擷取許多服務提供者，包括中繼資料服務提供者和資料服務動作提供者。 當系統要求資料服務動作提供者時，傳回您的[IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))執行。  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))包含的方法可讓您取得可用動作的相關資訊。 當您執行[IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))時，您會擴充服務的中繼資料，這是由服務的[IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))執行所定義，並以動作和處理分派給這些動作適當.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 呼叫[AdvertiseServiceAction 方法](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103))，以判斷哪些動作可用於指定的資源。 這個方法只會針對非永遠可用的動作呼叫。 它是用來根據所要求之資源的狀態或服務的狀態，檢查動作是否應該包含在 OData 回應中。 這項檢查的完成方式完全由您自行決定。 如果計算可用性相當耗費資源，而且目前資源位於摘要中，則略過檢查並通告動作就是可接受的作法。 如果目前傳回的資源屬於摘要的一部分，`inFeed` 參數就會設定為 `true`。  
  
#### <a name="createinvokable"></a>CreateInvokable  
 呼叫[CreateInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103))來建立[IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) ，其中包含的委派會封裝執行動作行為的程式碼。 這會建立[IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103))實例，但不會叫用動作。 WCF 資料服務動作有副作用，而且必須搭配更新提供者運作，才能將這些變更儲存至磁碟。 呼叫[IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103))方法時，會從更新提供者的 SaveChanges （）方法呼叫。  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 這個方法會傳回[ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))實例的集合，這些實例代表 WCF 資料服務所公開的所有動作。 [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))是動作的中繼資料標記法，其中包括動作名稱、參數和傳回型別等資訊。  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 這個方法會傳回所有可系結至指定系結參數類型之[ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))實例的集合。 換句話說，所有可在指定資源類型（也稱為系結參數類型）上作用的[ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))。這是在服務傳回資源時使用，以便包含可針對該資源叫用之動作的相關資訊。 這個方法應該只會傳回可繫結至確切繫結參數類型 (無衍生類型) 的動作。 這個方法是在遇到每種類型時，針對每個要求呼叫一次，而且結果由 WCF Data Services 進行快取。  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 這個方法會搜尋指定的[ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) ，並`true`在找到[ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))時傳回。 如果找到， [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))會在`serviceAction` `out`參數中傳回。  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 這個介面會提供一種執行 WCF 資料服務動作的方式。 實作 IDataServiceInvokable 時，您必須負責處理 3 件事：  
  
1. 擷取參數，而且可能要封送處理  
  
2. 將參數分派給呼叫 Invoke() 時實際實作動作的程式碼  
  
3. 儲存來自 Invoke() 的任何結果，以便使用 GetResult() 來擷取這些結果  
  
 參數可能會以 Token 的形式傳遞。 這是因為您可以寫入使用代表資源之 Token 的資料服務提供者，如果是這種情況，您可能必須先將這些 Token 轉換 (封送處理) 成實際資源，然後再分派給實際動作。 在封送處理參數之後，它必須處於可編輯的狀態，如此一來，在叫用動作時所發生的資源變更，就會儲存並寫入磁片。  
  
 此介面需要兩個方法：叫用和 GetResult。 Invoke 會叫用實作動作之行為的委派，而 GetResult 會傳回動作的結果。  
  
## <a name="invoking-a-wcf-data-service-action"></a>叫用 WCF 資料服務動作  
 動作是使用 HTTP POST 要求來叫用的。 URL 會依序指定資源和動作名稱。 參數是透過要求的主體傳遞的。 例如，假設有一項名為 MovieService 的服務，而這項服務公開了名為 Rate 的動作。 您就可以使用下列 URL，針對特定的影片叫用 Rate 動作：  
  
 `http://MovieServer/MovieService.svc/Movies(1)/Rate`
  
 Movies(1) 會指定您想要評比的影片，而 Rate 會指定評比動作。 評比的實際值將位於 HTTP 要求的主體中，如下列範例所示：  
  
```http
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
> 上述範例程式碼只能搭配支援 JSON Light 的 WCF Data Services 5.2 和更新版本運作。 如果使用舊版 WCF Data Services，您就必須依照下列方式指定 Json 詳細資訊內容類型：`application/json;odata=verbose`。  
  
 或者，您也可以使用 WCF Data Services 用戶端來叫用動作，如下列程式碼片段所示。  
  
```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
//...  
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```
  
 在上述程式碼片段中，`MoviesModel` 類別的產生方式是使用 Visual Studio，加入 WCF 資料服務的服務參考。  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 4.5](index.md)
- [定義 WCF Data Services](defining-wcf-data-services.md)
- [開發和部署 WCF 資料服務](developing-and-deploying-wcf-data-services.md)
- [自訂資料服務提供者](custom-data-service-providers-wcf-data-services.md)
