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
ms.openlocfilehash: 34b5f3bd5908d3833a2223b078f8d796234641be
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134443"
---
# <a name="iassemblyenumclone-method"></a>IAssemblyEnum::Clone 方法
建立這個[IAssemblyEnum](iassemblyenum-interface.md)物件的淺層複本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 脫銷複製的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IAssemblyEnum 介面](iassemblyenum-interface.md)
