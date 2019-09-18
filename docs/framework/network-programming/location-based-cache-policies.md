---
title: 以位置為基礎的快取原則
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
ms.openlocfilehash: e6896452fce89f69b40f1d03332355df72d93211
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047671"
---
# <a name="location-based-cache-policies"></a>以位置為基礎的快取原則
以位置為基礎的快取原則，會根據所要求資源可以使用的位置，定義有效快取項目的有效期限。 如果使用它不違反伺服器指定的重新驗證需求，快取的資源即為有效。 使用 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 類別建構函式可以程式設計方式建立以位置為基礎的快取原則。 以位置為基礎的原則類型，是使用 <xref:System.Net.Cache.RequestCacheLevel> 或 <xref:System.Net.Cache.HttpRequestCacheLevel> 列舉值傳遞至建構函式。 如需程式碼範例來建立以位置為基礎的快取原則，請參閱[如何：為應用程式設定以位置為基礎的快取原則](how-to-set-a-location-based-cache-policy-for-an-application.md)。 下列各節說明超文字傳輸通訊協定 (http 和 https) 資源的每種以位置為基礎的快取原則。  
  
## <a name="cache-if-available-policy"></a>可用時快取原則  
 如果有效的要求資源位於本機快取，則會使用快取的資源；否則，會向伺服器傳送資源要求。 如果在用戶端與伺服器之間的任何快取中都能取得要求的資源，中繼快取即可滿足要求。  
  
## <a name="cache-only-policy"></a>僅限快取原則  
 如果有效的要求資源位在本機快取，則會使用快取的資源。 當指定這個快取原則層級時，如果項目不在本機快取，就會擲回 <xref:System.Net.WebException> 例外狀況。  
  
## <a name="cache-or-next-cache-only-policy"></a>僅限快取或下一個快取原則  
 如果有效的要求資源位在本機快取或區域網路的中繼快取，則會使用快取的資源。 否則會擲回 <xref:System.Net.WebException> 例外狀況。 在 HTTP 快取通訊協定中，這是使用 only-if-cached 的快取控制指示詞所達成。  
  
## <a name="no-cache-no-store-policy"></a>無快取且無存放區原則  
 要求的資源絕不會從任何快取使用，也絕不會放在任何快取中。 如果要求的資源出現在本機快取中，它會被移除。 這個原則層級指出也應該移除資源的中繼快取。 在 HTTP 快取通訊協定中，這是使用 no-store 的快取控制指示詞所達成。  
  
## <a name="refresh-policy"></a>重新整理原則  
 如果要求的資源是從伺服器取得，或在本機快取以外的快取中找到，就可以使用。 在中繼快取滿足要求之前，該快取必須重新向伺服器驗證其快取的項目。 在 HTTP 快取通訊協定中，這是使用 max-age = 0 的快取控制指示詞和 no-cache Pragma 標頭所達成。  
  
## <a name="reload-policy"></a>重新載入原則  
 必須從伺服器取得要求的資源。 回應可能是儲存在本機快取中。 在 HTTP 快取通訊協定中，這是使用 no-cache 的快取控制指示詞和 no-cache Pragma 標頭所達成。  
  
## <a name="revalidate-policy"></a>重新驗證原則  
 比較快取中的資源複本和伺服器上的複本。 如果伺服器上的複本較新，就會用它來滿足要求，並取代快取中的複本。 如果快取中的複本和伺服器上的版本相同，就使用快取的複本。 在 HTTP 快取通訊協定中，使用條件式要求即可達成。  
  
## <a name="see-also"></a>另請參閱

- [網路應用程式的快取管理](cache-management-for-network-applications.md)
- [快取原則](cache-policy.md)
- [以時間為基礎的快取原則](time-based-cache-policies.md)
- [設定網路應用程式的快取功能](configuring-caching-in-network-applications.md)
- [\<requestCaching> 項目 (網路設定)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
