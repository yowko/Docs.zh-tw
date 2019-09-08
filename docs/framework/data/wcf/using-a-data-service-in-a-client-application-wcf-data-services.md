---
title: 在用戶端應用程式中使用資料服務 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 050c1a67a367a6dd5175c535fe89fb0010ae8cbc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790289"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>在用戶端應用程式中使用資料服務 (WCF 資料服務)
您可以藉由提供 Web 瀏覽器[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]的 URI，來存取公開摘要的服務。 URI 可提供資源的位址，而要求訊息會傳送至這些位址，以存取或變更資源所代表的基礎資料。 瀏覽器會發出 HTTP GET 命令，並且以 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的形式傳回要求的資源。 如需詳細資訊，請參閱[從網頁瀏覽器存取服務](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)。  
  
 雖然 Web 瀏覽器可用來測試 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務是否會傳回預期的資料，但是同時讓您建立、更新及刪除資料的實際執行 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務通常會以應用程式程式碼或網頁中的指令碼語言來存取。 本主題提供如何從用戶端應用程式[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]存取摘要的總覽。  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>使用 REST 語意存取與變更資料  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]有助於保證公開[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]的服務與取用摘要的應用程式之間的互通性。 應用程式會藉由傳送特定[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]HTTP 動作的要求訊息，以及處理應該執行動作之實體資源的 URI，來存取及變更以為基礎之服務中的資料。 當必須提供實體資料時，會在訊息本文中以特定編碼的裝載形式提供。  
  
### <a name="http-actions"></a>HTTP 動作  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 可支援下列 HTTP 動作，在定址資源代表的實體資料上，執行建立、讀取、更新，以及刪除作業：  
  
- **HTTP GET** -這是從瀏覽器存取資源時的預設動作。 要求訊息中不會提供任何承載，同時會以包含所要求之資料的承載傳回回應方法。  
  
- **HTTP POST**會將新的實體資料插入提供的資源中。 要插入的資料會於要求訊息的承載中提供。 回應訊息的裝載包含新建立之實體的資料。 其中包括任何自動產生的索引鍵值。 標頭亦包含定址新實體資源的 URI。  
  
- **HTTP 刪除**-刪除指定資源所代表的實體資料。 要求或回應訊息中不會出現任何承載。  
  
- **HTTP PUT** -以要求訊息的承載中提供的新資料取代所要求資源中的現有實體資料。  
  
- **HTTP merge** -由於只為了變更實體資料而執行刪除，然後在資料來源中插入， [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]因此會引進新的 HTTP merge 動作。 要求訊息的承載包含在定址實體資源中必須變更的屬性。 由於 HTTP 規格中未定義 HTTP MERGE，因此可能需要進行額外處理，才能透過非 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 感知的伺服器來路由傳送 HTTP MERGE 要求。  
  
 如需詳細資訊， [請參閱 OData：作業](https://go.microsoft.com/fwlink/?LinkId=185792)。  
  
### <a name="payload-formats"></a>承載格式  
 若為 HTTP PUT、HTTP POST 或 HTTP MERGE 要求，要求訊息的裝載會包含您傳送至資料服務的實體資料。 承載的內容取決於訊息的資料格式。 所有動作 (DELETE 除外) 的 HTTP 回應也包含此類承載。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]支援使用下列裝載格式來存取和變更服務的資料：  
  
- **Atom** -由[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]定義為 atom 發行通訊協定（AtomPub）之延伸的 XML 型訊息編碼，可透過 HTTP 交換 Web 摘要、播客、wiki 和 XML 型網際網路功能的資料。 如需詳細資訊， [請參閱 OData：Atom 格式](https://go.microsoft.com/fwlink/?LinkId=185794)。  
  
- **Json** JAVASCRIPT 物件標記法（json）是輕量的資料交換格式，以 JavaScript 程式設計語言的子集為基礎。 如需詳細資訊， [請參閱 OData：JSON 格式](https://go.microsoft.com/fwlink/?LinkId=185795)。  
  
 HTTP 要求訊息的標頭中會要求裝載的訊息格式。 如需詳細資訊， [請參閱 OData：作業](https://go.microsoft.com/fwlink/?LinkID=185792)。  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>使用用戶端程式庫存取及變更資料  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]包含用戶端程式庫，可讓您更輕鬆[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]地從 .NET Framework 和 Silverlight 架構的用戶端應用程式取用摘要。 這些程式庫會簡化 HTTP 訊息的傳送與接收。 他們也會將訊息承載轉譯為代表實體資料的 CLR 物件。 用戶端程式庫具有兩個核心類別： <xref:System.Data.Services.Client.DataServiceContext> 和 <xref:System.Data.Services.Client.DataServiceQuery%601>。 這些類別可讓您查詢資料服務，然後使用傳回的實體資料當做 CLR 物件。 如需詳細資訊，請參閱[WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)和[WCF Data Services （Silverlight）](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))。  
  
 您可以使用 Visual Studio 中的 [**加入服務參考**] 對話方塊，將參考加入至資料服務。 此工具會從參考的資料服務要求服務中繼資料，並產生代表資料服務的 <xref:System.Data.Services.Client.DataServiceContext>，同時也會產生代表實體的用戶端資料服務類別。 如需詳細資訊，請參閱[產生資料服務用戶端程式庫](generating-the-data-service-client-library-wcf-data-services.md)。  
  
 有一些可供您使用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]的程式設計程式庫，可讓您在其他類型的用戶端應用程式中取用摘要。 如需詳細資訊，請參閱[ODATA SDK](https://go.microsoft.com/fwlink/?LinkId=185796)。  
  
## <a name="see-also"></a>另請參閱

- [存取資料服務資源](accessing-data-service-resources-wcf-data-services.md)
- [快速入門](quickstart-wcf-data-services.md)
