---
title: "CLR_DEBUGGING_VERSION 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 092024f3f4e6fc1bc923ae2a299c5d9c21f1b1b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingversion-structure"></a>CLR_DEBUGGING_VERSION 結構
定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。  
  
## <a name="syntax"></a>語法  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`wStructVersion`|結構版本號碼|  
|`wMajor`|主要版本號碼。|  
|`wMinor`|次要版本號碼。|  
|`wBuild`|組建編號。|  
|`wRevision`|修訂編號。|  
  
## <a name="remarks"></a>備註  
 `CLR_DEBUGGING_VERSION`結構等同於 COR_VERSION 結構中，不過，`CLR_DEBUGGING_VERSION`結構提供額外的結構版本 欄位 (`wStructVersion`)。 目前，此欄位必須設定為零。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
