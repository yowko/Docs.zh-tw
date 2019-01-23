---
title: HOW TO：將現有實體附加至 DataServiceContext (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 2a515609feff343b6e917bf420a06cfb9dc468df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614220"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>HOW TO：將現有實體附加至 DataServiceContext (WCF Data Services)
當實體已經存在於資料服務時，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫可讓您附加物件，表示實體直接<xref:System.Data.Services.Client.DataServiceContext>且不需先執行查詢。 如需詳細資訊，請參閱 <<c0> [ 更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立這項服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立現有的 `Customer` 物件，此物件包含要儲存至資料服務的變更。 系統會將物件附加至內容，並呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 方法，將附加物件標記為 <xref:System.Data.Services.Client.EntityStates.Modified>，然後再呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法。  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>另請參閱
- [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
