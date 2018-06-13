---
title: 在用戶端應用程式中使用資料服務 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: b25489de9a64ba4f1938e4d52c1cc677a218495b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365289"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>在用戶端應用程式中使用資料服務 (WCF 資料服務)
您可以存取服務公開[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要將 URI 提供給 Web 瀏覽器。 URI 可提供資源的位址，而要求訊息會傳送至這些位址，以存取或變更資源所代表的基礎資料。 瀏覽器會發出 HTTP GET 命令，並且以 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的形式傳回要求的資源。 如需詳細資訊，請參閱[從網頁瀏覽器存取服務](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)。  
  
 雖然 Web 瀏覽器可用來測試 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務是否會傳回預期的資料，但是同時讓您建立、更新及刪除資料的實際執行 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務通常會以應用程式程式碼或網頁中的指令碼語言來存取。 本主題概略說明如何存取[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]從用戶端應用程式摘要。  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>使用 REST 語意存取與變更資料  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 有助於確保公開服務之間的互通性[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要與取用應用程式[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要。 應用程式存取及變更資料[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]為基礎的服務，可藉由傳送要求訊息的特定 HTTP 動作與位址應該執行的動作依據的實體資源的 URI。 當必須提供實體資料時，會在訊息本文中以特定編碼的裝載形式提供。  
  
### <a name="http-actions"></a>HTTP 動作  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 可支援下列 HTTP 動作，在定址資源代表的實體資料上，執行建立、讀取、更新，以及刪除作業：  
  
-   **HTTP GET** -這是從瀏覽器存取資源時的預設動作。 要求訊息中不會提供任何承載，同時會以包含所要求之資料的承載傳回回應方法。  
  
-   **HTTP POST** -將新的實體資料插入至提供的資源。 要插入的資料會於要求訊息的承載中提供。 回應訊息的裝載包含新建立之實體的資料。 其中包括任何自動產生的索引鍵值。 標頭亦包含定址新實體資源的 URI。  
  
-   **HTTP DELETE** -刪除指定的資源所代表的實體資料。 要求或回應訊息中不會出現任何承載。  
  
-   **HTTP PUT** -取代現有的要求之資源的要求訊息的裝載中提供新資料的實體資料。  
  
-   **HTTP MERGE** -由於執行刪除再插入資料來源，只為了變更實體資料的效率不足而[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]引進了新的 HTTP MERGE 動作。 要求訊息的承載包含在定址實體資源中必須變更的屬性。 由於 HTTP 規格中未定義 HTTP MERGE，因此可能需要進行額外處理，才能透過非 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 感知的伺服器來路由傳送 HTTP MERGE 要求。  
  
 如需詳細資訊，請參閱[OData： 作業](http://go.microsoft.com/fwlink/?LinkId=185792)。  
  
### <a name="payload-formats"></a>承載格式  
 若為 HTTP PUT、HTTP POST 或 HTTP MERGE 要求，要求訊息的裝載會包含您傳送至資料服務的實體資料。 承載的內容取決於訊息的資料格式。 所有動作 (DELETE 除外) 的 HTTP 回應也包含此類承載。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 存取及變更資料與服務支援下列裝載格式：  
  
-   **Atom** -的 XML 型訊息編碼，可定義[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]做為 Atom 發行通訊協定 (AtomPub) 資料交換透過 HTTP 的 Web 摘要、 podcast、 wiki 及 XML 型網際網路功能的延伸。 如需詳細資訊，請參閱[OData: Atom 格式](http://go.microsoft.com/fwlink/?LinkId=185794)。  
  
-   **JSON** -JavaScript Object Notation (JSON) 是輕量型資料交換格式，取決於 JavaScript 程式設計語言的子集。 如需詳細資訊，請參閱[OData: JSON 格式](http://go.microsoft.com/fwlink/?LinkId=185795)。  
  
 HTTP 要求訊息的標頭中會要求裝載的訊息格式。 如需詳細資訊，請參閱[OData： 作業](http://go.microsoft.com/fwlink/?LinkID=185792)。  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>使用用戶端程式庫存取及變更資料  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含用戶端程式庫可讓您更輕鬆地取用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]從.NET Framework 和 Silverlight 為基礎的用戶端應用程式摘要。 這些程式庫會簡化 HTTP 訊息的傳送與接收。 他們也會將訊息承載轉譯為代表實體資料的 CLR 物件。 用戶端程式庫具有兩個核心類別： <xref:System.Data.Services.Client.DataServiceContext> 和 <xref:System.Data.Services.Client.DataServiceQuery%601>。 這些類別可讓您查詢資料服務，然後使用傳回的實體資料當做 CLR 物件。 如需詳細資訊，請參閱[WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)和[WCF Data Services (Silverlight)](http://msdn.microsoft.com/library/c0cd9f4b-1372-48e4-9935-c8421239da30)。  
  
 您可以使用**加入服務參考**將參考加入至資料服務的 Visual Studio 中的對話方塊。 此工具會從參考的資料服務要求服務中繼資料，並產生代表資料服務的 <xref:System.Data.Services.Client.DataServiceContext>，同時也會產生代表實體的用戶端資料服務類別。 如需詳細資訊，請參閱[產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。  
  
 有一些程式庫可讓您可用來取用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]其他種類的用戶端應用程式中的摘要。 如需詳細資訊，請參閱[OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796)。  
  
## <a name="see-also"></a>另請參閱  
 [存取資料服務資源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
