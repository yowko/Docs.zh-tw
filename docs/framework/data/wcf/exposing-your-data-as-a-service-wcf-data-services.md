---
title: 將資料當做服務公開 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 1dc1f0ec12c50c4c97b141a34b468e3367ead75e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780308"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>以服務形式公開您的資料（WCF Data Services）

WCF Data Services 與 Visual Studio 整合，可讓您更輕鬆地定義服務，以將資料[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]公開為摘要。 建立公開 OData 摘要的資料服務包含下列基本步驟：

1. **定義資料模型。** WCF Data Services 原本就支援以[ADO.NET Entity Framework](../adonet/ef/index.md)為基礎的資料模型。 如需詳細資訊，請參閱[如何：使用 ADO.NET Entity Framework 資料來源](create-a-data-service-using-an-adonet-ef-data-wcf.md)建立資料服務。

     WCF Data Services 也支援以傳回<xref:System.Linq.IQueryable%601>介面實例之 common language runtime （CLR）物件為基礎的資料模型。 這樣可以讓您部署 .NET Framework 中以清單、陣列和集合為基礎的資料服務。 若要透過這些資料結構啟用建立、更新及刪除作業，您必須同時實作 <xref:System.Data.Services.IUpdatable> 介面。 如需詳細資訊，請參閱[如何：使用反映提供者](create-a-data-service-using-rp-wcf-data-services.md)建立資料服務。

     針對更先進的案例，WCF Data Services 包含一組提供者，可讓您根據晚期繫結的資料類型來定義資料模型。 如需詳細資訊，請參閱[自訂資料服務提供者](custom-data-service-providers-wcf-data-services.md)。

2. **建立資料服務。** 最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。 如需詳細資訊，請參閱 [Defining WCF Data Services](defining-wcf-data-services.md)的資訊。

3. **設定資料服務。** 根據預設，WCF Data Services 會停用實體容器所公開的資源存取權。 <xref:System.Data.Services.DataServiceConfiguration>介面可讓您設定對資源和服務作業的存取、指定支援的 OData 版本，以及定義其他整個服務的行為，例如，批次處理行為或可傳回的最大實體數目在單一回應中。 如需詳細資訊，請參閱設定[資料服務](configuring-the-data-service-wcf-data-services.md)。

如需如何建立以 Northwind 範例資料庫為基礎的簡單資料服務的範例，請參閱[快速入門](quickstart-wcf-data-services.md)。

## <a name="see-also"></a>另請參閱

- [快速入門](getting-started-with-wcf-data-services.md)
- [概觀](wcf-data-services-overview.md)
