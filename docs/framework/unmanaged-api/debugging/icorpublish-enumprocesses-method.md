---
title: ICorPublish::EnumProcesses 方法
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2779138a0999e34ad6424d76ddfebbcfdf611d58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses 方法
取得此電腦上執行的受管理處理程序中的列舉值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `Type`  
 值為[COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)列舉，指定要擷取的處理序的類型。 在目前版本中，只有 COR_PUB_MANAGEDONLY 是有效的。  
  
 `ppIEnum`  
 位址指標[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)是列舉值的處理程序的執行個體。  
  
## <a name="remarks"></a>備註  
 處理序的列舉值的集合根據快照集時執行的處理程序`EnumProcesses`方法呼叫。 列舉值將不會包含任何處理序終止之前或之後啟動`EnumProcesses`呼叫。  
  
 `EnumProcesses`方法可能會多次呼叫這個[ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)建立新的最新集合的處理序的執行個體。 現有的集合不會影響的後續呼叫`EnumProcesses`方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub.idl、 CorPub.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorPublish 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
