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
ms.openlocfilehash: 99f2eb9447bdf43cb57cfe86f35d2c09044ed470
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947620"
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a>Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
會建立[ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)類別的實例 (instance)。  
  
## <a name="syntax"></a>語法  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
## <a name="parameters"></a>參數  
  
## <a name="parameter-values"></a>參數值  
 *operationDescription*  
  
 描述要在產生之工作流程活動中執行的作業，包括作業名稱、傳回型別和參數資訊。 此參數的值不得為**null**。 它應描述會使用訊息合約並接收含有一則訊息之引數的同步作業。 如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
 *configurationName*  
  
 指定端點組態名稱。 這個參數的值不可以是**null**或空白。 如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
 *proxyNamespace*  
  
 指定作業的服務命名空間。 這個參數的值不可以是**null**或空白。 如果沒有滿足這些條件，則不會定義在執行階段使用此類別的建構函式和其他方法的結果。  
  
## <a name="see-also"></a>另請參閱

- [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
