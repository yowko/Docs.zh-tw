---
title: "自訂資料服務提供者 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 90e837739edc74ee469f42720f52789ee1c8f6fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a>自訂資料服務提供者 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含一組提供者，可讓您根據晚期繫結的資料型別定義資料模型。  
  
|提供者|描述|  
|--------------|-----------------|  
|中繼資料提供者|這是核心自訂資料服務提供者，可讓您透過實作 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 介面，在執行階段定義自訂的資料模型。|  
|查詢提供者|此提供者可讓您針對使用 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 介面定義的自訂資料模型執行查詢。 查詢提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceQueryProvider> 介面而建立的。|  
|更新提供者|此提供者可讓您更新在自訂資料服務提供者中公開的型別，並且管理並行。 更新提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> 介面建立的|  
|分頁提供者|此提供者可搭配自訂資料服務提供者使用，以啟用伺服器驅動的分頁支援。 自訂資料服務的分頁提供者是透過實作 <xref:System.Data.Services.Providers.IDataServicePagingProvider> 介面而建立的。|  
|資料流處理提供者|此提供者可讓您將二進位大型物件資料型別公開為資料流。 資料流處理提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> 介面而建立的。 資料流處理提供者也可以搭配 Entity Framework 和反映資料來源提供者使用。 如需詳細資訊，請參閱[資料流處理提供者](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)。|  
  
 如需詳細資訊，請參閱文章[自訂資料服務提供者](http://go.microsoft.com/fwlink/?LinkID=186850)和[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]提供者中的工具組[OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069)。  
  
## <a name="see-also"></a>另請參閱  
 [資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Entity Framework 提供者](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [反映提供者](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
