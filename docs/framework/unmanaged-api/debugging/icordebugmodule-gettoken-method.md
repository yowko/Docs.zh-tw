---
title: ICorDebugModule::GetToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: 1cf4d82200709971201da60d06d0cb929641a104
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501881"
---
# <a name="icordebugmodulegettoken-method"></a>ICorDebugModule::GetToken 方法
取得此模組之資料表專案的 token。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `pToken`  
 脫銷`mdModule`參考模組中繼資料之標記的指標。  
  
## <a name="remarks"></a>備註  
 Token 可以傳遞至[IMetaDataImport](../metadata/imetadataimport-interface.md)、 [IMetaDataImport2](../metadata/imetadataimport2-interface.md)和[IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md)中繼資料匯入介面。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料](../metadata/index.md)
