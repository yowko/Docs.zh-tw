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
ms.openlocfilehash: dfe247bda75c3695c7c09b85729b4e057c13c62d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692627"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged 方法

取得值，這個值會指出這個 [ICorPublishProcess](icorpublishprocess-interface.md) 所參考的進程是否知道有 managed 程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>參數  

 `pbManaged`  
 擴展布林值的指標，指出進程是否有 managed 程式碼。 `true`如果進程具有 managed 程式碼，則值為，否則為 `false` 。  
  
## <a name="remarks"></a>備註  

 由於目前的版本 `ICorPublishProcess` 只允許存取具有 managed 程式碼的進程，因此 `IsManaged` 一律會傳回 `true` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl、CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorPublishProcess 介面](icorpublishprocess-interface.md)
