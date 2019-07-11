---
title: ICorDebugType::GetBase 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c24d6e9c42a091eafbe6d4bdee2bb4e055fd8852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772043"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase 方法
取得的介面指標來代表基底型別，如果有的話，表示這個型別的 ICorDebugType `ICorDebugType`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>參數  
 `pBase`  
 [out]位址指標`ICorDebugType`表示基底型別的物件。  
  
## <a name="remarks"></a>備註  
 查閱基底型別是有用來實作常見的偵錯工具功能，例如列印出的物件或其父類別的所有欄位。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
