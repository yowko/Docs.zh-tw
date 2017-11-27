---
title: "ICorDebugAppDomain::GetName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590bfb5d7d8cac8e322bddfe6258ad9bf377dad6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
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
  
#### <a name="parameters"></a>參數  
 `cchName`  
 [in] `szName` 陣列的大小。 設定此值為零可放在查詢模式中這個方法。  
  
 `pcchName`  
 [out]名稱或中實際傳回的字元數的大小的指標`szName`。 在查詢模式中，這個值會讓呼叫者知道如何多大的緩衝區配置的名稱。  
  
 `szName`  
 [out]陣列，其中會儲存在應用程式定義域的名稱。  
  
## <a name="remarks"></a>備註  
 偵錯工具呼叫`GetName`方法一次，若要取得之名稱所需的緩衝區大小。 偵錯工具會配置緩衝區，然後再呼叫第二次方法來填滿緩衝區。 第一次呼叫，以取得名稱的大小指*查詢模式*。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
