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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7939f7b1c0c725bb4e8c642bc38121dd755da5e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785134"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName 方法
取得應用程式定義域的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cchName`  
 [in] `szName` 陣列的大小。 將此值設定為零，這個方法放置在查詢模式中。  
  
 `pcchName`  
 [out]名稱或中實際傳回的字元數的大小的指標`szName`。 在查詢模式中，這個值會讓呼叫者知道如何多大的緩衝區配置的名稱。  
  
 `szName`  
 [out]陣列，其中會儲存應用程式定義域的名稱。  
  
## <a name="remarks"></a>備註  
 偵錯工具呼叫`GetName`方法一次，若要取得之名稱所需的緩衝區大小。 偵錯工具會配置緩衝區，，然後再呼叫第二次的方法來填滿緩衝區。 第一次呼叫中，若要取得名稱的大小指*查詢模式*。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
