---
title: StackOverflowType 列舉
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: bbdc68721378e6bbb09f5e4eade08e2e6e03b097
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729904"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType 列舉

包含值，這些值表示堆疊溢位事件的根本原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`SO_ClrEngine`|堆疊溢位是由執行引擎所造成。|  
|`SO_Managed`|堆疊溢位是由 managed 程式碼所造成。|  
|`SO_Other`|堆疊溢位是由非受控碼所造成。|  
  
## <a name="remarks"></a>備註  

 這項資訊會透過呼叫 [IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md) 方法傳遞給主機。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載列舉](hosting-enumerations.md)
