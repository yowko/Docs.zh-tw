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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c88c12646a13e5a24f2475bd2db04c8c831141c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781759"
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
  
|成員|說明|  
|------------|-----------------|  
|`miCodeTypeMask`|描述程式碼類型的旗標。|  
|`miIL`|指定方法實作是 Microsoft intermediate language (MSIL)。|  
|`miNative`|指定方法實作為原生。|  
|`miOPTIL`|指定方法實作為 OPTIL。|  
|`miRuntime`|指定方法實作由通用語言執行平台。|  
|`miManagedMask`|表示程式碼是否為 managed 或 unmanaged 的旗標。|  
|`miUnmanaged`|指定方法實作為非受控。|  
|`miManaged`|指定方法實作管理。|  
|`miForwardRef`|指定已定義的方法。 這個旗標時，可使用主要合併。|  
|`miPreserveSig`|指定方法簽章不會受損 HRESULT 轉換。|  
|`miInternalCall`|保留供內部使用的 common language runtime。|  
|`miSynchronized`|指定的方法是單一執行緒，透過其主體。|  
|`miNoInlining`|指定方法無法內嵌。|  
|`miAggressiveInlining`|指定方法應內嵌的話。|  
|`miNoOptimization`|指定未最佳化的方法。|  
|`miMaxMethodImplVal`|最大有效值`CorMethodImpl`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
