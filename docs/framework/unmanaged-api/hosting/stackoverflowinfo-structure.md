---
title: StackOverflowInfo 結構
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: a8a57cfcaf36949d4d10c6ec267a5f55a2aee5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729924"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo 結構

儲存發生溢位的型別，以及因為溢位所擲回之例外狀況的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`soType`|[StackOverflowType](stackoverflowtype-enumeration.md)列舉的值，這個值會指定溢位的型別。|  
|`pExceptionInfo`|Win32 物件的指標 `EXCEPTION_POINTERS` ，其中包含例外狀況記錄與電腦無關的例外狀況記錄，以及在發生例外狀況時，具有電腦相依描述的內容記錄。|  
  
## <a name="remarks"></a>備註  

 `StackOverflowInfo`物件會傳遞給事件的[IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md)方法 `Event_StackOverflow` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](hosting-structures.md)
