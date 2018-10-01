---
title: 以時間為基礎的快取原則
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d24fa2ece34d20a3d9e8d6f971eebae5da0f496e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198081"
---
# <a name="time-based-cache-policies"></a>以時間為基礎的快取原則
以時間為基礎的快取原則會使用擷取資源的時間、與資源一起傳回的標頭，以及目前時間，定義快取項目的有效期限。 設定以時間為基礎的快取原則時，您可以使用 <xref:System.Net.Cache.HttpRequestCacheLevel.Default> 時間基礎原則，或建立自訂的時間基礎原則。 為使用超文字傳輸通訊協定 (HTTP) 取得的資源，使用以時間為基礎的預設原則時，確切的快取行為是由快取回應中包含的標頭，以及 RFC 2616 的 13 與 14 一節中所指定的行為來決定，RFC 2616 可在 [http://www.ietf.org](http://www.ietf.org/) 中取得。如需示範如何為 HTTP 資源設定以時間為基礎之預設原則的程式碼範例，請參閱[如何：為應用程式設定以時間為基礎的預設快取原則](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)。 如需示範如何建立和使用快取原則的程式碼範例，請參閱[設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)。  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>判斷快取項目有效期限的準則  
 若要自訂以時間為基礎的快取原則，您可以指定要使用下列一或多個準則來判斷快取項目的有效期限：  
  
-   最長使用期限  
  
-   最長過時  
  
-   最短有效期限  
  
-   快取同步處理日期  
  
> [!NOTE]
>  使用時間為基礎的預設快取原則不應與設定應用程式的預設快取原則混淆。 以時間為基礎的預設原則是可以用於要求或應用程式層級的特定原則。 應用程式的預設快取原則是在要求上未設定原則時生效的原則 (以位置為基礎或以時間為基礎)。 如需設定應用程式之預設快取原則的詳細資料，請參閱<xref:System.Net.WebRequest.DefaultCachePolicy%2A>。  
  
### <a name="maximum-age"></a>最長使用期限  
 最長使用期限原則準則指定可以使用資源快取複本的時間量。 如果資源的快取複本超過指定的時間量，則必須藉由針對伺服器上的內容檢查資源，來重新驗證資源。 如果最長使用期限允許在資源到期後還使用它，則除非同時指定最長過時值，否則不會採用此準則。  
  
### <a name="maximum-staleness"></a>最長過時  
 最長過時原則準則指定在可以使用資源的快取複本，且在內容到期日之後的時間長度。 這是唯一允許在資源過期之後仍使用資源的快取原則準則。  
  
### <a name="minimum-freshness"></a>最短有效期限  
 最短有效期限原則準則指定在可以使用資源的快取複本，且在內容到期日之前的時間長度。 此原則的效果會使快取項目在它的到期日之前便過期，因此最短有效期限和最長過時設定兩者互斥。  
  
## <a name="cache-synchronization-date"></a>快取同步處理日期  
 快取同步處理日期原則準則會藉由針對伺服器上的內容檢查資源的快取複本，判斷它何時必須重新驗證。 如果項目快取後內容已變更，則會從伺服器擷取它、儲存在快取，並傳回到應用程式。 如果內容未變更，其時間戳記會更新，且應用程式會取得快取的內容。  
  
 快取同步處理日期可讓您指定必須重新驗證快取內容的絕對日期。 如果新的快取項目上次重新驗證是在快取同步處理日期之前，仍會發生與伺服器的重新驗證。 如果快取項目重新驗證是在快取同步處理日期之後，而且沒有其他有效期限或伺服器重新驗證需求使快取項目失效，則會使用來自快取的項目。 如果快取同步處理日期設定為未來的日期，則每次要求時都會重新驗證項目，直到快取同步處理日期已過為止。  
  
 下列主題提供結合以時間為基礎之快取原則準則的影響資訊：  
  
-   [快取原則互動 — 最長使用期限和最長過時](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [快取原則互動 - 最長使用期限和最小有效期限](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)  
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
