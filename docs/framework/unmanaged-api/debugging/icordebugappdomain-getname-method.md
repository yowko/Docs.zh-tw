---
title: ICorDebugAppDomain::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 2c9aa6792885c685195049948a540453b1f5235e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110315"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName 方法
取得應用程式域的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cchName`  
 [in] `szName` 陣列的大小。 將此值設定為零，以將此方法置於查詢模式。  
  
 `pcchName`  
 脫銷`szName`中實際傳回的名稱大小或字元數的指標。 在查詢模式中，此值可讓呼叫者知道要為名稱配置的緩衝區大小。  
  
 `szName`  
 脫銷儲存應用程式功能變數名稱稱的陣列。  
  
## <a name="remarks"></a>備註  
 偵錯工具會呼叫 `GetName` 方法一次，以取得名稱所需的緩衝區大小。 偵錯工具會配置緩衝區，然後第二次呼叫方法來填滿緩衝區。 第一次呼叫，以取得名稱的大小，稱為「*查詢模式*」。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
