---
title: 快取原則
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
ms.openlocfilehash: 33043652e11beb374843d43c9683ff4b7928eb3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112797"
---
# <a name="cache-policy"></a>快取原則
快取原則所定義的規則用來判斷是否可以使用所要求資源的快取複本來滿足要求。 應用程式指定有效期限的用戶端快取需求，但有效的快取原則是由用戶端快取需求、伺服器內容到期需求和伺服器重新驗證需求所決定。 用戶端快取原則與伺服器需求的互動一律會導致最保守的快取原則，協助確保將最新內容傳回給用戶端應用程式。  
  
 快取原則是以位置為基礎或以時間為基礎。 以位置為基礎的快取原則會根據所要求資源可以使用的位置，定義快取項目的有效期限。 以時間為基礎的快取原則會使用擷取資源的時間、與資源一起傳回的標頭，以及目前時間，定義快取項目的有效期限。 大部分的應用程式可以使用以時間為基礎的預設快取原則，以實作可從[網際網路工程任務推動小組 (IETF)](https://www.ietf.org/) 網站取得之 RFC 2616 中所指定的快取原則。  
  
 下表中所述的類別是用來指定快取原則。  
  
|類別名稱|說明|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|針對使用 <xref:System.Net.HttpWebRequest> 物件所要求的資源，代表以位置為基礎和以時間為基礎的快取原則。|  
|<xref:System.Net.Cache.RequestCachePolicy>|針對使用 <xref:System.Net.WebRequest> 物件所要求的資源，代表以位置為基礎的快取原則或以 <xref:System.Net.Cache.RequestCacheLevel.Default> 時間為基礎的快取原則。|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|指定值，用來建立以時間為基礎之 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|指定值，用來建立以位置為基礎和以時間為基礎之 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。|  
|<xref:System.Net.Cache.RequestCacheLevel>|指定值，用來建立以位置為基礎或 <xref:System.Net.Cache.RequestCacheLevel.Default> 以時間為基礎的 <xref:System.Net.Cache.RequestCachePolicy> 物件。|  
  
 您可以定義應用程式所提出之所有要求或個別要求的快取原則。 當您同時指定應用程式層級快取原則和要求層級快取原則時，會使用要求層級原則。 您可以透過程式設計方式或是使用應用程式或電腦組態檔，來指定應用程式層級快取原則。 如需詳細資訊，請參閱 [\<requestCaching> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)。  
  
 若要建立快取原則，您必須建立 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 類別的執行個體來建立原則物件。 若要在要求上指定原則，請將要求的 <xref:System.Net.WebRequest.CachePolicy%2A> 屬性設定為原則物件。 以程式設計方式設定應用程式層級原則時，請將 <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> 屬性設定為原則物件。  
  
 如需示範如何建立和使用快取原則的程式碼範例，請參閱[設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)。  
  
## <a name="see-also"></a>另請參閱

- [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
