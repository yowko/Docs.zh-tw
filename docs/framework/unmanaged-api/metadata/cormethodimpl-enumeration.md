---
title: CorMethodImpl 列舉
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: 40e82997e58292a10f5e960cc9d9785d9ea8946a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676968"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl 列舉

包含值，這些值描述方法實作功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`miCodeTypeMask`|描述程式碼類型的旗標。|  
|`miIL`|指定方法執行是 Microsoft 中繼語言 (MSIL) 。|  
|`miNative`|指定方法實作為原生。|  
|`miOPTIL`|指定方法實 OPTIL。|  
|`miRuntime`|指定方法實作為 common language runtime 所提供。|  
|`miManagedMask`|旗標，指出程式碼是否為 managed 或非受控。|  
|`miUnmanaged`|指定方法執行未受管理。|  
|`miManaged`|指定方法執行為 managed。|  
|`miForwardRef`|指定定義方法。 此旗標主要用於合併案例中。|  
|`miPreserveSig`|指定方法簽章不能因 HRESULT 轉換而改變。|  
|`miInternalCall`|保留給 common language runtime 內部使用。|  
|`miSynchronized`|指定方法透過其主體為單一執行緒。|  
|`miNoInlining`|指定方法無法內嵌。|  
|`miAggressiveInlining`|指定應該盡可能內嵌方法。|  
|`miNoOptimization`|指定不應優化方法。|  
|`miMaxMethodImplVal`|的最大有效值 `CorMethodImpl` 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
