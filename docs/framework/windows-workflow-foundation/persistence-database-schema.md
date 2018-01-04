---
title: "持續性資料庫結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34f69f4c-df81-4da7-b281-a525a9397a5c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc758f85b4f8b0bec5c00979f42d3f7b2ea7b182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-database-schema"></a>持續性資料庫結構描述
本主題描述 SQL 工作流程執行個體存放區所支援的公用檢視表。  
  
## <a name="instances-view"></a>Instances 檢視表  
 **執行個體**檢視包含在資料庫中的所有工作流程執行個體相關的一般資訊。  
  
|資料行名稱|資料行型別|描述|  
|-----------------|-----------------|-----------------|  
|InstanceId|UniqueIdentifier|工作流程執行個體的識別碼。|  
|PendingTimer|DateTime|表示工作流程在 Delay 活動上遭到封鎖，將在計時器逾時後繼續執行。 如果工作流程未遭到封鎖，不需等候計時器逾時，此值可以是 null。|  
|CreationTime|DateTime|表示建立工作流程的時間。|  
|LastUpdatedTime|DateTime|表示上次工作流程保存到資料庫的時間。|  
|ServiceDeploymentId|BigInt|做為 [ServiceDeployments] 檢視表的外部索引鍵。 如果目前工作流程執行個體是 Web 主控服務的執行個體，則此資料行有值，否則設為 NULL。|  
|SuspensionExceptionName|Nvarchar(450)|表示造成工作流程暫止的例外狀況類型 (例如 InvalidOperationException)。|  
|SuspensionReason|Nvarchar(max)|表示工作流程執行個體暫止的原因。 如果例外狀況造成工作流程暫止，則此資料行包含與例外狀況相關聯的訊息。<br /><br /> 如果執行個體是手動暫止，則此資料行包含使用者指定的暫止執行個體之原因。|  
|ActiveBookmarks|Nvarchar(max)|如果工作流程執行個體閒置中，此屬性表示執行個體封鎖所在的書籤。 如果執行個體不是處於閒置狀態，則此資料行為 NULL。|  
|CurrentMachine|Nvarchar(128)|表示目前在記憶體中載入工作流程執行個體的電腦名稱。|  
|LastMachine|Nvarchar(450)|表示載入工作流程執行個體的最後一部電腦。|  
|ExecutionStatus|Nvarchar(450)|表示工作流程的目前執行狀態。 可能的狀態包含**執行**，**閒置**， **Closed**。|  
|IsInitialized|位元|表示工作流程執行個體是否已初始化。 初始化的工作流程執行個體是至少已保存一次的工作流程執行個體。|  
|IsSuspended|位元|表示工作流程執行個體是否已暫止。|  
|IsCompleted|位元|表示工作流程執行個體是否已完成執行。 **注意：** Iif **InstanceCompletionAction**屬性設定為**DeleteAll**，從在完成時檢視並移除執行個體。|  
|EncodingOption|TinyInt|描述用來序列化資料屬性的編碼方式。<br /><br /> -0 – 無編碼<br />-1 – GzipStream|  
|ReadWritePrimitiveDataProperties|Varbinary(max)|包含的序列化執行個體資料屬性將在執行個體載入時提供回到工作流程執行階段。<br /><br /> 每個基本屬性都是原生 CLR 類型，這表示不需要特殊組件還原序列化 Blob。|  
|WriteOnlyPrimitiveDataProperties|Varbinary(max)|包含的序列化執行個體資料屬性在執行個體載入時不會提供回到工作流程執行階段。<br /><br /> 每個基本屬性都是原生 CLR 類型，這表示不需要特殊組件還原序列化 Blob。|  
|ReadWriteComplexDataProperties|Varbinary(max)|包含的序列化執行個體資料屬性將在執行個體載入時提供回到工作流程執行階段。<br /><br /> 還原序列化程式需要此 Blob 中所儲存之所有物件類型的知識。|  
|WriteOnlyComplexDataProperties|Varbinary(max)|包含的序列化執行個體資料屬性在執行個體載入時不會提供回到工作流程執行階段。<br /><br /> 還原序列化程式需要此 Blob 中所儲存之所有物件類型的知識。|  
|IdentityName|Nvarchar(max)|工作流程定義的名稱。|  
|IdentityPackage|Nvarchar(max)|建立工作流程時指定的封裝資訊 (例如組件名稱)。|  
|組建|BigInt|工作流程版本的組建編號。|  
|主要|BigInt|工作流程版本的主要編號。|  
|次要|BigInt|工作流程版本的次要編號。|  
|修訂|BigInt|工作流程版本的修訂編號。|  
  
> [!CAUTION]
>  **執行個體**檢視也包含 Delete 觸發程序。 具有適當權限的使用者可以對此檢視表執行 Delete 陳述式，從資料庫強制移除工作流程執行個體。 直接從檢視表刪除，建議只當做最後手段，因為刪除工作流程執行階段底下的執行個體會造成非預期的結果。 請改用工作流程執行個體管理端點，讓工作流程執行階段結束執行個體。 如果您想要從檢視表刪除大量執行個體，請確認沒有使用中的執行階段正在操作這些執行個體。  
  
## <a name="servicedeployments-view"></a>ServiceDeployments 檢視表  
 **ServiceDeployments**檢視包含所有的 Web 部署資訊 (IIS / WAS) 裝載工作流程服務。 屬於 Web 主控每個工作流程執行個體會包含**ServiceDeploymentId**參考此檢視中的資料列。  
  
|資料行名稱|資料行型別|描述|  
|-----------------|-----------------|-----------------|  
|ServiceDeploymentId|BigInt|此檢視表的主索引鍵。|  
|SiteName|Nvarchar(max)|表示包含工作流程服務的網站名稱 (例如**Default Web Site**)。|  
|RelativeServicePath|Nvarchar(max)|代表相對於指向工作流程服務之網站的虛擬路徑  （例如： **/app1/PurchaseOrderService.svc**)。|  
|RelativeApplicationPath|Nvarchar(max)|代表相對於指向包含工作流程服務之應用程式的網站的虛擬路徑  (例如**/app1**)。|  
|ServiceName|Nvarchar(max)|代表工作流程服務的名稱  (例如**PurchaseOrderService**)。|  
|ServiceNamespace|Nvarchar(max)|代表工作流程服務的命名空間  (例如**MyCompany**)。|  
  
 ServiceDeployments 檢視表也包含 Delete 觸發程序。 具有適當權限的使用者可以對此檢視表執行 Delete 陳述式，從資料庫移除 ServiceDeployment 項目。 請注意：  
  
1.  從這個檢視表刪除項目會耗用大量成本，因為在執行這項作業之前整個資料庫必須鎖定， 以避免工作流程執行個體可能參考不存在之 ServiceDeployment 項目的狀況。 只在停機 / 維護時段，才從此檢視表刪除。  
  
2.  任何嘗試刪除的項目中參考的 ServiceDeployment 資料列**執行個體**檢視將會導致任何作業。 您只能刪除零參考的 ServiceDeployment 資料列。  
  
## <a name="instancepromotedproperties-view"></a>InstancePromotedProperties 檢視表  
 **InstancePromotedProperties**檢視包含所有升級屬性所指定的使用者資訊。 已提升的屬性是做為第一級屬性，供使用者用於查詢以擷取執行個體。  例如，使用者可以加入 PurchaseOrder 提升，永遠都會儲存在訂單成本**Value1**資料行。 這可讓使用者查詢成本超過特定值的所有採購單。  
  
|資料行型別|資料行型別|描述|  
|-|-|-|  
|InstanceId|UniqueIdentifier|工作流程執行個體的識別碼。|  
|EncodingOption|TinyInt|描述用來序列化已提升之二進位屬性的編碼方式。<br /><br /> -0 – 無編碼<br />-1 – GZipStream|  
|PromotionName|Nvarchar(400)|與此執行個體相關聯之提升的名稱。 在此資料行中加入泛型資料行內容需要有 PromotionName。<br /><br /> 例如，PurchaseOrder 的 PromotionName 可以表示 Value1 包含訂單成本、Value2 包含下訂單的客戶名稱、Value 3 包含客戶地址等等。|  
|Value[1-32]|SqlVariant|Value[1-32] 包含可儲存在 SqlVariant 資料行中的值。 單一提升不可包含超過 32 個 SqlVariants。|  
|Value[33-64]|Varbinary(max)|Value[33-64] 包含序列化值。例如，Value33 可以包含採購項目的 JPEG。 單一提升不可包含超過 32 個二進位屬性。|  
  
 InstancePromotedProperties 檢視表為結構描述繫結，這表示使用者可以加入一個或多個資料行的索引，以便對此檢視表最佳化查詢。  
  
> [!NOTE]
>  索引檢視表需要更多儲存空間，而增加額外的處理負擔。 請參閱[改善效能與 SQL Server 2008 索引檢視表](http://go.microsoft.com/fwlink/?LinkId=179529)如需詳細資訊。
