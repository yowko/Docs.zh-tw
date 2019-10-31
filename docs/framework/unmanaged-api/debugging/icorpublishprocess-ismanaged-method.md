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
ms.openlocfilehash: ad3a357a98cb5ed28a34e4076b5e145903ceaf91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103491"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged 方法
取得值，指出此[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)所參考的進程是否已知具有 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbManaged`  
 脫銷布林值的指標，指出進程是否有 managed 程式碼。 如果進程具有 managed 程式碼，則此值為 `true`;否則，`false`。  
  
## <a name="remarks"></a>備註  
 由於目前的 `ICorPublishProcess` 版本只允許存取具有 managed 程式碼的進程，`IsManaged` 一律會傳回 `true`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorPublishProcess 介面](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
