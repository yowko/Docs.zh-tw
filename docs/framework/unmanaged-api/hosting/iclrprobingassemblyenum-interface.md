---
title: ICLRProbingAssemblyEnum 介面
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
ms.openlocfilehash: 6df08889af30542af5a128cbffc38a57ce640fde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728923"
---
# <a name="iclrprobingassemblyenum-interface"></a>ICLRProbingAssemblyEnum 介面

提供的方法可讓主機使用 common language runtime (CLR) 內部的元件身分識別資訊，來取得元件的探查識別，而不需要建立或瞭解該身分識別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Get 方法](iclrprobingassemblyenum-get-method.md)|取得位於指定索引處的元件識別。|  
  
## <a name="remarks"></a>備註  

 [ICLRAssemblyIdentityManager：： GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)之類的方法會傳回 `ICLRProbingAssemblyEnum` 實例。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [裝載介面](hosting-interfaces.md)
