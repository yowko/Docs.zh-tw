---
title: 自訂資料服務提供者 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: 4c92bf2f4e75b78cd6236c023246cc6c999086fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186688"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>自訂資料服務提供者 (WCF Data Services)

WCF Data Services 包含一組提供者，可讓您根據晚期繫結資料類型來定義資料模型。  
  
|提供者|描述|  
|--------------|-----------------|  
|中繼資料提供者|這是核心自訂資料服務提供者，可讓您透過實作 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 介面，在執行階段定義自訂的資料模型。|  
|查詢提供者|此提供者可讓您針對使用 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 介面定義的自訂資料模型執行查詢。 查詢提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceQueryProvider> 介面而建立的。|  
|更新提供者|此提供者可讓您更新在自訂資料服務提供者中公開的型別，並且管理並行。 更新提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> 介面建立的|  
|分頁提供者|此提供者可搭配自訂資料服務提供者使用，以啟用伺服器驅動的分頁支援。 自訂資料服務的分頁提供者是透過實作 <xref:System.Data.Services.Providers.IDataServicePagingProvider> 介面而建立的。|  
|資料流處理提供者|此提供者可讓您將二進位大型物件資料型別公開為資料流。 資料流處理提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> 介面而建立的。 資料流處理提供者也可以搭配 Entity Framework 和反映資料來源提供者使用。 如需詳細資訊，請參閱 [資料流程提供者](streaming-provider-wcf-data-services.md)。|  
  
## <a name="see-also"></a>另請參閱

- [資料服務提供者](data-services-providers-wcf-data-services.md)
- [Entity Framework 提供者](entity-framework-provider-wcf-data-services.md)
- [反映提供者](reflection-provider-wcf-data-services.md)
