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
ms.openlocfilehash: a76a7a2d4ad68e367e38e175377aff40ce399346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450203"
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`miCodeTypeMask`|Flags that describe code type.|  
|`miIL`|Specifies that the method implementation is Microsoft intermediate language (MSIL).|  
|`miNative`|指定方法實作為原生。|  
|`miOPTIL`|Specifies that the method implementation is OPTIL.|  
|`miRuntime`|Specifies that the method implementation is provided by the common language runtime.|  
|`miManagedMask`|Flags that indicate whether the code is managed or unmanaged.|  
|`miUnmanaged`|Specifies that the method implementation is unmanaged.|  
|`miManaged`|Specifies that the method implementation is managed.|  
|`miForwardRef`|Specifies that the method is defined. This flag is used primarily in merge scenarios.|  
|`miPreserveSig`|Specifies that the method signature cannot be mangled for an HRESULT conversion.|  
|`miInternalCall`|Reserved for internal use by the common language runtime.|  
|`miSynchronized`|Specifies that the method is single-threaded through its body.|  
|`miNoInlining`|指定方法無法內嵌。|  
|`miAggressiveInlining`|Specifies that the method should be inlined if possible.|  
|`miNoOptimization`|Specifies that the method should not be optimized.|  
|`miMaxMethodImplVal`|The maximum valid value for a `CorMethodImpl`.|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
