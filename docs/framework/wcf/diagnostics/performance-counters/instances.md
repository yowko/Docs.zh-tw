---
title: 執行個體
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916392"
---
# <a name="instances"></a>執行個體
計數器名稱：執行個體。  
  
## <a name="description"></a>描述  
 服務目前包含的執行個體內容數。  
  
 多數時候，執行個體內容數會與執行個體數相同。 不過，下列案例為此規則的例外狀況。  
  
- 服務方法會明確呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。  
  
- <xref:System.ServiceModel.ReleaseInstanceMode> 套用至 <xref:System.ServiceModel.OperationBehaviorAttribute> 執行個體。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.OperationBehaviorAttribute>
