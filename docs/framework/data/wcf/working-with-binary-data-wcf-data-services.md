---
title: 使用二進位資料 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
ms.openlocfilehash: 35e7cc666307d589f21c128734df10430a1a8588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779629"
---
# <a name="working-with-binary-data-wcf-data-services"></a>使用二進位資料 (WCF 資料服務)

用戶端程式庫可讓您使用下列其中一種方式[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] ，從摘要中取出和更新二進位資料： [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]

- 當做實體的基本型別屬性。 如果要處理可以輕鬆載入記憶體的小型二進位資料物件，建議使用這個方法。 在此情況下，二進位屬性是資料模型所公開的實體屬性，而資料服務會將二進位資料序列化成為回應訊息中的 base-64 二進位編碼 XML。

- 當做個別的二進位資源資料流。 如果要存取及變更可能代表相片、影片或是其他任何類型之二進位編碼資料的二進位大型物件 (BLOB) 資料，建議使用這個方法。

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]使用中[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]定義的 HTTP 來執行二進位資料的資料流程處理。 在此機制中，二進位資料會被視為與實體（稱為媒體連結專案）不同的媒體資源。 如需詳細資訊，請參閱[串流處理提供者](streaming-provider-wcf-data-services.md)。

> [!TIP]
> 如需如何建立可從[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]儲存相片之服務下載二進位影像檔的 Windows Presentation Foundation （WPF）用戶端應用程式的逐步範例，請參閱文章[資料服務串流提供者系列-部分2：從用戶端](https://go.microsoft.com/fwlink/?LinkId=201637)存取媒體資源串流。 若要下載 blog 文章中精選的串流相片資料服務範例程式碼，請參閱 MSDN 程式碼庫中的[串流處理相片資料服務範例](https://go.microsoft.com/fwlink/?LinkId=198988)。

## <a name="entity-metadata"></a>實體中繼資料

在資料服務中繼資料中，套用到屬於媒體連結項目之實體類型的 `HasStream` 屬性會指出擁有相關媒體資源資料流的實體。 在下列範例中， `PhotoInfo`實體是具有相關媒體資源的媒體連結專案，以`HasStream`屬性工作表示。

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

本主題的其餘範例會示範如何存取及變更媒體資源資料流。 如需如何使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫在 .NET Framework 用戶端應用程式中取用媒體資源串流的完整範例，請參閱[從用戶端存取媒體資源串流](https://go.microsoft.com/fwlink/?LinkID=201637)文章。

## <a name="accessing-the-binary-resource-stream"></a>存取二進位資源資料流

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫提供從 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 架構資料服務存取二進位資源資料流的方法。 下載媒體資源時，您可以使用媒體資源的 URI，或者您可以取得包含媒體資源資料本身的二進位資料流。 您也可以上載媒體資源資料做為二進位資料流。

> [!TIP]
> 如需如何建立可從[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]儲存相片之服務下載二進位影像檔的 Windows Presentation Foundation （WPF）用戶端應用程式的逐步範例，請參閱文章[資料服務串流提供者系列-部分2：從用戶端](https://go.microsoft.com/fwlink/?LinkId=201637)存取媒體資源串流。 若要下載 blog 文章中精選的串流相片資料服務範例程式碼，請參閱 MSDN 程式碼庫中的[串流處理相片資料服務範例](https://go.microsoft.com/fwlink/?LinkId=198988)。

### <a name="getting-the-uri-of-the-binary-stream"></a>取得二進位資料流的 URI

擷取特定類型的媒體資源 (例如影像及其他媒體檔案) 時，在應用程式中使用媒體資源的 URI 通常比處理二進位資料的資料流本身更容易。 若要取得與給定媒體連結項目相關聯的資源資料流 URI，您必須在追蹤實體的 <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> 執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceContext> 方法。 下列範例會示範如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> 方法來取得在用戶端上建立新影像所使用的媒體資源資料流 URI：

[!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photowindow.xaml.cs#getreadstreamuri)]
[!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photowindow.xaml.vb#getreadstreamuri)]

### <a name="downloading-the-binary-resource-stream"></a>下載二進位資源資料流

擷取媒體資源資料流時，您必須在追蹤媒體連結項目的 <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> 執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceContext> 方法。 這個方法會將要求傳送到傳回 <xref:System.Data.Services.Client.DataServiceStreamResponse> 物件的資料服務，而且此物件擁有包含資源之資料流的參考。 當應用程式需要二進位資源做為 <xref:System.IO.Stream> 時，請使用這個方法。 下列範例會示範如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> 方法來擷取在用戶端上建立新影像所使用的資料流：

[!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_streaming_client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
[!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_streaming_client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]

> [!NOTE]
> 包含二進位資料流之回應訊息中的 Content-Length 標頭不是由此資料服務所設定。 這個值可能不會反映二進位資料流的實際長度。

### <a name="uploading-a-media-resource-as-a-stream"></a>上載媒體資源做為資料流

若要插入或更新媒體資源，請在追蹤實體的 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceContext> 方法。 這個方法會傳送要求給資料服務，此服務中包含從提供的資料流讀取的媒體資源。 下列範例會示範如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 方法，將影像傳送到資料服務：

[!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_client/cs/photodetailswindow.xaml.cs#setsavestream)]
[!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_client/vb/photodetailswindow.xaml.vb#setsavestream)]

在這個範例中，<xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 方法的呼叫方式是為 `true` 參數提供 `closeStream` 的值。 如此可確保當二進位資料上載到資料服務之後，<xref:System.Data.Services.Client.DataServiceContext> 會關閉資料流。

> [!NOTE]
> 當您呼叫 <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> 時，並不會將資料流傳送到資料服務，直到呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 為止。

## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
- [將資料繫結至控制項](binding-data-to-controls-wcf-data-services.md)
