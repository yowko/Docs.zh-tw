---
title: "使用二進位資料 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 二進位資料"
  - "WCF Data Services, 資料流"
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 使用二進位資料 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫可讓您透過下列其中一種方式，從 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要擷取及更新二進位資料：  
  
-   當做實體的基本型別屬性。  如果要處理可以輕鬆載入記憶體的小型二進位資料物件，建議使用這個方法。  在此情況下，二進位屬性是資料模型所公開的實體屬性，而資料服務會將二進位資料序列化成為回應訊息中的 base\-64 二進位編碼 XML。  
  
-   當做個別的二進位資源資料流。  如果要存取及變更可能代表相片、影片或是其他任何類型之二進位編碼資料的二進位大型物件 \(BLOB\) 資料，建議使用這個方法。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會使用 HTTP 實作二進位資料的資料流，如 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 中所定義。  在這個機制中，二進位資料會視為媒體資源，它與實體分開但還是與實體有關，稱為媒體連結項目。  如需詳細資訊，請參閱[資料流處理提供者](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)。  
  
> [!TIP]
>  如需如何建立從存放相片之 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務下載二進位影像檔的 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] 用戶端應用程式逐步範例，請參閱下列文章：[資料服務資料流處理提供者系列第 2 部分：從用戶端存取媒體資源資料流](http://go.microsoft.com/fwlink/?LinkId=201637)。  若要下載部落格文章中精選之資料流相片資料服務的範例程式碼，請參閱 MSDN Code Gallery 中的[資料流處理相片資料服務範例](http://go.microsoft.com/fwlink/?LinkId=198988)。  
  
## 實體中繼資料  
 在資料服務中繼資料中，套用到屬於媒體連結項目之實體類型的 `HasStream` 屬性會指出擁有相關媒體資源資料流的實體。  在以下的範例中，`PhotoInfo` 實體是 `HasStream` 屬性所指出，擁有相關媒體資源的媒體連結項目。  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 本主題的其餘範例會示範如何存取及變更媒體資源資料流。  如需如何在 .NET Framework 用戶端應用程式中使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫來取用媒體資源資料流的完整範例，請參閱下列文章：[從用戶端存取媒體資源資料流](http://go.microsoft.com/fwlink/?LinkID=201637)。  
  
## 存取二進位資源資料流  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫提供從 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 架構資料服務存取二進位資源資料流的方法。  下載媒體資源時，您可以使用媒體資源的 URI，或者您可以取得包含媒體資源資料本身的二進位資料流。  您也可以上載媒體資源資料做為二進位資料流。  
  
> [!TIP]
>  如需如何建立從存放相片之 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務下載二進位影像檔的 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] 用戶端應用程式逐步範例，請參閱下列文章：[資料服務資料流處理提供者系列第 2 部分：從用戶端存取媒體資源資料流](http://go.microsoft.com/fwlink/?LinkId=201637)。  若要下載部落格文章中精選之資料流相片資料服務的範例程式碼，請參閱 MSDN Code Gallery 中的[資料流處理相片資料服務範例](http://go.microsoft.com/fwlink/?LinkId=198988)。  
  
### 取得二進位資料流的 URI  
 擷取特定類型的媒體資源 \(例如影像及其他媒體檔案\) 時，在應用程式中使用媒體資源的 URI 通常比處理二進位資料的資料流本身更容易。  若要取得與給定媒體連結項目相關聯的資源資料流 URI，您必須在追蹤實體的 <xref:System.Data.Services.Client.DataServiceContext> 執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> 方法。  下列範例會示範如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> 方法來取得在用戶端上建立新影像所使用的媒體資源資料流 URI：  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### 下載二進位資源資料流  
 擷取媒體資源資料流時，您必須在追蹤媒體連結項目的 <xref:System.Data.Services.Client.DataServiceContext> 執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> 方法。  這個方法會將要求傳送到傳回 <xref:System.Data.Services.Client.DataServiceStreamResponse> 物件的資料服務，而且此物件擁有包含資源之資料流的參考。  當應用程式需要二進位資源做為 <xref:System.IO.Stream> 時，請使用這個方法。  下列範例會示範如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> 方法來擷取在用戶端上建立新影像所使用的資料流：  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria streaming client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria streaming client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  包含二進位資料流之回應訊息中的 Content\-Length 標頭不是由此資料服務所設定。  這個值可能不會反映二進位資料流的實際長度。  
  
### 上載媒體資源做為資料流  
 若要插入或更新媒體資源，請在追蹤實體的 <xref:System.Data.Services.Client.DataServiceContext> 執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 方法。  這個方法會傳送要求給資料服務，此服務中包含從提供的資料流讀取的媒體資源。  下列範例會示範如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 方法，將影像傳送到資料服務：  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 在這個範例中，<xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 方法的呼叫方式是為 `closeStream` 參數提供 `true` 的值。  如此可確保當二進位資料上載到資料服務之後，<xref:System.Data.Services.Client.DataServiceContext> 會關閉資料流。  
  
> [!NOTE]
>  當您呼叫 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 時，並不會將資料流傳送到資料服務，直到呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 為止。  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)