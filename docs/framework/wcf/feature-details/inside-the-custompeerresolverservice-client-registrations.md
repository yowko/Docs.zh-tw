---
title: CustomPeerResolverService 內部：用戶端註冊
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 3d1e1c6493da54bc3ae0e74a33985da59382ea52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619785"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>CustomPeerResolverService 內部：用戶端註冊
網狀結構中的每一個節點都會將自己的端點資訊透過 `Register` 函式發佈給解析程式服務。 解析程式服務會儲存這項資訊做為註冊記錄。 這份記錄會包含該節點的唯一識別碼 (RegistrationID) 以及端點資訊 (PeerNodeAddress)。  
  
## <a name="stale-records-and-expiration-time"></a>失效記錄與到期時間  
 在理想的狀況下，當節點要脫離網狀結構時，該節點會呼叫 `Unregister` 函式，這個函式會讓解析程式服務移除該註冊記錄。 有時候，節點在呼叫 `Unregister` 前即已關閉或變得無法存取，而留下失效的註冊記錄。  
  
 解析程式服務中的失效記錄可能會導致無法連線。 如果嘗試連線到網狀結構的某一個節點收到來自解析程式服務失效連線資訊，則可能需要更久的時間，才能順利加入該網狀結構。 失效的記錄也會佔用記憶體。 如果不進行有效的清除程序，用於儲存註冊資訊的快取記憶體終究會發生溢位，且毀損解析程式服務。  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> 會標記每一筆記錄的到期時間 (DateTime)，也會儲存到期時間做為記錄的一部分。 服務會利用到期時間識別失效的記錄。 自訂實作也應該可以完成類似的工作。  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval 及 CleanupInterval  
 `RefreshInterval` 的 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> 屬性會定義註冊記錄保存在服務註冊查詢表中的有效期限。 指定給這個屬性的時間長度傳遞給特定記錄後，該記錄即失效且會標記為必須刪除。  
  
 `CleanupInterval` 的 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> 屬性會告知服務搜尋與刪除失效註冊記錄的頻率。 `CleanupInterval` 的設定值應該大於或等於服務上的 `RefreshInterval`。  
  
 若要實作自己的解析程式服務，必須自行撰寫可以移除失效註冊記錄的維護函式。 有幾個方式可做到這點：  
  
- **定期維護**:設定計時器，定期著手進行並瀏覽您的資料存放區，刪除舊的記錄。 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> 會使用這個方法。  
  
- **被動刪除**:而不是主動定期搜尋失效記錄的作法，您可以識別和您的服務正在執行另一個函式時，刪除過時的記錄。 可能會延遲對解析程式用戶端發出之要求的回應時間，但是這可以省去設定計時器的作法，對於只有少數節點會在不呼叫 `Unregister` 而離開網狀結構的情況，也比較有效率。  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime 與 Refresh  
 當一個節點註冊到解析程式服務時，該節點會收到來自服務的 <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> 物件。 指定新的時間量的 `RegistrationLifetime`，註冊項目將在經過這段時間後到期並由解析程式服務移除。 例如，假設 `RegistrationLifetime` 為 2 分鐘，那麼節點必須在 2 分鐘內呼叫 `Refresh`，才能確保記錄的更新狀況且沒有被刪除。 解析程式服務收到 `Refresh` 要求時，服務會檢查該記錄並且重設到期時間。 Refresh 會連同 <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> 屬性傳回 `RegistrationLifetime` 物件。  
  
## <a name="see-also"></a>另請參閱

- [對等解析程式](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
