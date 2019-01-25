---
title: 將資料當做服務公開 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 8e598dde0d85b1d7d4208bf2475a0f6f6eee34a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700984"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>將您的資料公開為服務 (WCF Data Services)

WCF Data Services 整合可讓您更輕鬆地定義服務以公開資料做為 Visual Studio[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要。 建立公開 OData 摘要的資料服務包含下列基本步驟：

1.  **定義資料模型。** WCF 資料服務原本就支援資料模型為基礎[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)。 如需詳細資訊，請參閱[＜How to：建立使用 ADO.NET Entity Framework 資料來源的資料服務](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)。

     WCF Data Services 也支援資料模型傳回的執行個體的 common language runtime (CLR) 物件為基礎的<xref:System.Linq.IQueryable%601>介面。 這樣可以讓您部署 .NET Framework 中以清單、陣列和集合為基礎的資料服務。 若要透過這些資料結構啟用建立、更新及刪除作業，您必須同時實作 <xref:System.Data.Services.IUpdatable> 介面。 如需詳細資訊，請參閱[＜How to：建立資料服務，使用反映提供者](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)。

     更進階的情況下，WCF Data Services 包含一組可讓您定義資料模型，根據晚期繫結資料型別提供者。 如需詳細資訊，請參閱 <<c0> [ 自訂資料服務提供者](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)。

2.  **建立資料服務。** 最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。 如需詳細資訊，請參閱 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)的資訊。

3.  **設定資料服務。** 根據預設，WCF Data Services 會停用實體容器所公開的資源的存取權。 <xref:System.Data.Services.DataServiceConfiguration>介面可讓您設定資源的存取權和服務作業，請指定支援的 OData 中，版本，以及定義其他整個服務的行為，例如，批次行為或可傳回的實體數目上限以單一的回應。 如需詳細資訊，請參閱 <<c0> [ 設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。

如需如何建立以 Northwind 範例資料庫為基礎的簡易資料服務的範例，請參閱 <<c0> [ 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。

## <a name="see-also"></a>另請參閱

- [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [概觀](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)