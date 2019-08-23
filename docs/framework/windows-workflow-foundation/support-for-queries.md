---
title: 支援查詢
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948930"
---
# <a name="support-for-queries"></a>支援查詢
SQL 工作流程執行個體存放區會記錄存放區中一組已知的屬性。 使用者可以根據這些屬性查詢執行個體。 下列清單包含其中一些已知的屬性：  
  
- **網站名稱。** 包含服務之網站的名稱。  
  
- **相對的應用程式路徑。** 應用程式的路徑 (相對於網站)。  
  
- **相對服務路徑。** 服務的路徑 (相對於應用程式)。  
  
- **服務名稱。** 服務的名稱。  
  
- **服務命名空間。** 服務所使用之命名空間的名稱。  
  
- **目前的電腦。**  
  
- **最後一部電腦**。 工作流程服務執行個體上一次執行所在的電腦。  
  
> [!NOTE]
> 若為使用工作流程服務主機的自我裝載案例，只會填入後四個屬性。 若為工作流程應用程式案例，則只會填入最後一個屬性。  
  
 工作流程執行階段會提供前三個屬性的值。 工作流程服務主機會提供 [暫止**原因**] 屬性的值。 SQL 工作流程實例存放區本身會提供**上次更新的機器**屬性的值。  
  
 SQL 工作流程執行個體存放區功能亦可讓您指定自訂屬性 (您可以將這些屬性的值存放在持續性資料庫中以及用於查詢中)。 如需自訂升級的詳細資訊, 請參閱[儲存](store-extensibility.md)擴充性。  
  
## <a name="views"></a>檢視  
 執行個體存放區包含下列檢視。 如需進一步的詳細資料, 請參閱[持續性資料庫架構](persistence-database-schema.md)。  
  
### <a name="the-instances-view"></a>Instances 檢視表  
 Instances 檢視表包含下列欄位：  
  
1. **ID**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>ServiceDeployments 檢視表  
 ServiceDeployments 檢視表包含下列欄位：  
  
1. **SiteName**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **ServiceName**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>InstancePromotedProperties 檢視表  
 InstancePromotedProperties 檢視表包含下列欄位。 如需升級屬性的詳細資訊, 請參閱[Store](store-extensibility.md)擴充性主題。  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **PromotionName**  
  
4. **值 #** (從**Value1**到**Value64**的欄位範圍)。
