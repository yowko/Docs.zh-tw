---
title: ESymbolReadingPolicy 列舉
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
ms.openlocfilehash: 42ce1f02294db98c5c593a5f16de5226703d5f9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733707"
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy 列舉

包含值，這些值會設定用來讀取程式資料庫 (PDB) 檔的原則。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`eSymbolReadingAlways`|指定偵錯工具應一律讀取 PDB 檔案。|  
|`eSymbolReadingFullTrustOnly`|指定偵錯工具應該唯讀取與完全信任元件相關聯的 PDB 檔案。|  
|`eSymbolReadingNever`|指定偵錯工具絕對不應讀取 PDB 檔案。|  
  
## <a name="remarks"></a>備註  

 `ESymbolReadingPolicy`列舉會搭配[ICLRDebugManager：： SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md)方法使用。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
