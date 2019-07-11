---
title: IAssemblyEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::Clone
helpviewer_keywords:
- Clone method, IAssemblyEnum interface [.NET Framework fusion]
- IAssemblyEnum::Clone method [.NET Framework fusion]
ms.assetid: 0014bb66-590c-486c-9ade-f2133905cd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d288f4ccf91567224546df1a3309a411590a5a12
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779036"
---
# <a name="iassemblyenumclone-method"></a>IAssemblyEnum::Clone 方法
建立這個的淺層複製[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 [out]複製指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyEnum 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
