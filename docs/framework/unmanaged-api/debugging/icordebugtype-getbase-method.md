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
ms.openlocfilehash: cff527aa7cde6a13667d47d030a0ef7db96ad5ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122338"
---
# <a name="icordebugtypegetbase-method"></a>ICorDebugType::GetBase 方法
取得 ICorDebugType 的介面指標，表示此 `ICorDebugType`所代表之類型的基底類型（如果有的話）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>參數  
 `pBase`  
 脫銷表示基底類型之 `ICorDebugType` 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 查閱類型的基底類型對於執行一般偵錯工具功能很有用，例如，列印出物件或其父類別的所有欄位。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
