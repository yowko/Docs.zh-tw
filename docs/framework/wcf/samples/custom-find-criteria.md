---
title: 自訂尋找準則
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 699260fcef7680710f721d213dbf1126ebf7a896
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836731"
---
# <a name="custom-find-criteria"></a>自訂尋找準則
此範例示範如何使用邏輯建立自訂範圍比對，以及如何實作自訂探索服務。 用戶端使用自訂範圍比對功能來精簡並進一步建立在 WCF 探索之系統提供的尋找功能之上。 此範例包含的案例如下：  
  
1.  用戶端要尋找計算機服務。  
  
2.  若要精簡其搜尋範圍，用戶端必須使用自訂範圍比對規則。  
  
3.  根據這個規則，如果端點符合用戶端指定的任何範圍，服務就會向用戶端回應。  
  
## <a name="demonstrates"></a>示範  
  
-   建立自訂探索服務。  
  
-   透過演算法實作自訂範圍比對。  
  
## <a name="discussion"></a>討論  
 用戶端會尋找"OR"類型比對準則。 如果端點上的範圍符合用戶端提供的任何範圍，服務就會回應。 在此情況下，用戶端會在下列清單中尋找擁有任何範圍的計算機服務：  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 若要達成這個目的，用戶端會引導服務依照 URI 傳入自訂範圍比對來使用自訂範圍比對規則。 若要簡化自訂範圍比對，服務所使用的自訂探索服務必須了解自訂範圍比對並實作相關聯的比對邏輯。  
  
 開啟用戶端專案中的 Program.cs 檔案。 請注意，`ScopeMatchBy` 物件的 `FindCriteria` 欄位會設定為特定的 URI。 此識別碼會傳送到服務中。 如果服務不了解這個規則，就會忽略用戶端的尋找要求。  
  
 開啟服務專案。 實作自訂探索服務要使用三個檔案：  
  
1.  **AsyncResult.cs**： 這是實作`AsyncResult`所需的探索方法。  
  
2.  **CustomDiscoveryService.cs**： 這個檔案會實作自訂探索服務。 此實作會擴充 <xref:System.ServiceModel.Discovery.DiscoveryService> 類別並覆寫必要的方法。 請注意 <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> 方法的實作。 此方法會檢查用戶端是否依照規則指定自訂範圍比對。 這是用戶端先前指定的相同自訂 URI。 如果指定的自訂規則，則會遵循實作"OR"比對邏輯的程式碼路徑。  
  
     這個自訂邏輯會通過服務所擁有之每個端點上的所有範圍。 如果有任何端點的範圍符合用戶端提供的任何範圍，探索服務會將該端點加入至傳回用戶端的回應中。  
  
3.  **CustomDiscoveryExtension.cs**： 實作探索服務的最後一個步驟是將這項實作自訂探索服務至服務主機。 此處所使用的協助程式類別為 `CustomDiscoveryExtension` 類別。 此類別會擴充 <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> 類別。 使用者必須覆寫 <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> 方法。 在此情況下，方法會傳回之前建立之自訂探索服務的執行個體。 `PublishedEndpoints` 是 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>，其中包含加入至 <xref:System.ServiceModel.ServiceHost> 的所有應用程式端點。 自訂探索服務使用這個端點填入其內部清單。 使用者也可以加入其他端點中繼資料。  
  
 最後，開啟 Program.cs。 請注意，<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 和 `CustomDiscoveryExtension` 都會加入至主機中。 一旦完成這個動作，而且主機所擁有的端點可用來接收探索訊息之後，應用程式就可以使用自訂探索服務。  
  
 請注意，用戶端不需知道位址，就能找到此服務。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  開啟包含專案的方案。  
  
2.  建置專案。  
  
3.  執行服務應用程式。  
  
4.  執行用戶端應用程式。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
