---
title: HOW TO：將摘要同時公開為 Atom 和 RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: 4780e43679d461509911a4abda689a0c16112e4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493421"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a>HOW TO：將摘要同時公開為 Atom 和 RSS
Windows Communication Foundation (WCF) 可讓您建立公開新聞訂閱摘要的服務。 本主題討論如何同時使用 Atom 1.0 和 RSS 2.0，建立可公開新聞訂閱摘要的新聞訂閱服務。 此服務會公開可傳回任何一種新聞訂閱格式的端點。 為了簡要說明，此範例中使用的服務為自我裝載。 在實際執行環境中，此類型的服務會在 IIS 或 WAS 下裝載。 如需不同的 WCF 裝載選項的詳細資訊，請參閱[主控](../../../../docs/framework/wcf/feature-details/hosting.md)。  
  
### <a name="to-create-a-basic-syndication-service"></a>若要建立基本新聞訂閱服務  
  
1.  使用以 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性標記的介面來定義服務合約。 每個公開為新聞訂閱摘要的作業，都會傳回 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 物件。 請注意 <xref:System.ServiceModel.Web.WebGetAttribute> 的參數。 `UriTemplate` 會指定用來叫用此服務作業的 URL。 這個參數的字串包含常值和變數在大括號 ({*格式*})。 此變數對應至服務作業的 `format` 參數。 如需詳細資訊，請參閱<xref:System.UriTemplate>。 `BodyStyle` 會影響此服務作業所傳送與接收之訊息的寫入方式。 <xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> 會指定傳送至此服務作業，以及來自此服務作業的資料都不得透過基礎結構定義的 XML 元素來包裝。 如需詳細資訊，請參閱<xref:System.ServiceModel.Web.WebMessageBodyStyle>。  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  請使用 <xref:System.ServiceModel.ServiceKnownTypeAttribute> 來指定此介面中由服務作業所傳回的型別。  
  
2.  實作服務合約。  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  建立 <xref:System.ServiceModel.Syndication.SyndicationFeed> 物件並新增作者、分類和描述。  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  建立幾個 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件。  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  新增 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件至摘要。  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  使用格式參數來傳回要求的格式。  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>若要裝載服務  
  
1.  建立 <xref:System.ServiceModel.Web.WebServiceHost> 物件。 除非在程式碼或組態中指定端點，否則 <xref:System.ServiceModel.Web.WebServiceHost> 類別會在服務的基底位址上自動加入端點。 在這個範例中，沒有指定端點，因此會公開預設端點。  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  開啟服務主機、從服務載入摘要、顯示摘要，並等候使用者按下 ENTER。  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>若要使用 HTTP GET 呼叫 GetBlog  
  
1.  開啟 Internet Explorer 並輸入下列 URL，然後按下 ENTER。 http://localhost:8000/BlogService/GetBlog  
  
     URL 包含服務的基底位址 (http://localhost:8000/BlogService)，相對位址的端點，以及要呼叫的服務作業。  
  
### <a name="to-call-getblog-from-code"></a>若要從程式碼呼叫 GetBlog()  
  
1.  使用基底位址與您要呼叫的方法建立 <xref:System.Xml.XmlReader>。  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  呼叫靜態 <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> 方法，傳入剛才建立的 <xref:System.Xml.XmlReader>。  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     這會叫用服務作業，並在新的 <xref:System.ServiceModel.Syndication.SyndicationFeed> 中填入服務作業所傳回的格式器。  
  
3.  存取摘要物件。  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a>範例  
 以下是這個範例的完整程式碼清單。  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 在編譯先前的程式碼時，請參考 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>
