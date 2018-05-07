---
title: IAssemblyName::IsEqual 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 043394541f5ed91b85a57f4cb13c61cca442bfec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual 方法
決定指定[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件是否等於此`IAssemblyName`，根據指定的比較旗標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pName`  
 [in]`IAssemblyName`物件要與這個比較`IAssemblyName`。  
  
 `dwCmpFlags`  
 [in]位元組合[ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)影響比較的值。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [融合列舉](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
