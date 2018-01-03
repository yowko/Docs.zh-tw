---
title: "ICorDebugChainEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e78340d26e4a7ab67fa6c312b1dbd537c5c0a28c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumnext-method"></a>ICorDebugChainEnum::Next 方法
取得 ICorDebugChain 執行個體的指定的數目從列舉型別，從目前位置開始。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]數目`ICorDebugChain`要擷取的執行個體。  
  
 `chains`  
 [out]陣列的指標，其中每個指向`ICorDebugChain`物件，代表鏈結。  
  
 `pceltFetched`  
 [out]數目的指標`ICorDebugChain`實際傳回的執行個體。 這個值可以是 null 如果`celt`是其中一個。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
