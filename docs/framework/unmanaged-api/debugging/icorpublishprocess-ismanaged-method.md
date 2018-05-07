---
title: ICorPublishProcess::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3fc25f76ef0f848fc29ffbed12b653d1c59c1f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged 方法
取得值，指出是否處理程序參考這個[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)稱為具有 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pbManaged`  
 [out]布林值，指出是否處理具有 managed 程式碼指標。 值是`true`如果處理程序具有 managed 程式碼; 否則`false`。  
  
## <a name="remarks"></a>備註  
 因為最新版`ICorPublishProcess`只允許存取具有 managed 程式碼的處理序`IsManaged`一律會傳回`true`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub.idl、 CorPub.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorPublishProcess 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
