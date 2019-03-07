---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.date: 03/30/2017
ms.topic: reference
api_name:
- Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location:
- Microsoft.VisualStudio.Activities.dll
api_type:
- Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
ms.openlocfilehash: b44b20a83068278fb35345220f45051a7c4177f2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498701"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a>Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
建立的執行個體[Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)類別。  
  
## <a name="syntax"></a>語法  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a>參數  
  
## <a name="parameter-values"></a>參數值  
 *operationDescription*  
  
 描述要在產生之工作流程活動中執行的作業，包括作業名稱、傳回型別和參數資訊。 此參數的值不能**null**。 它應描述會使用訊息合約並接收含有一則訊息之引數的同步作業。 如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
 *configurationName*  
  
 指定端點組態名稱。 此參數的值不能是**null**或空白。 如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
 *proxyNamespace*  
  
 指定作業的服務命名空間。 此參數的值不能是**null**或空白。 如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
## <a name="see-also"></a>另請參閱
- [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
