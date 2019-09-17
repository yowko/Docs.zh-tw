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
ms.openlocfilehash: 926bdcee3a3c3974c8546f3a6dfe98f0b62c93c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796565"
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual 方法
根據指定的比較旗標，判斷指定的`IAssemblyName`[IAssemblyName](iassemblyname-interface.md) 物件是否等於這個。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `pName`  
 在要`IAssemblyName`與之`IAssemblyName`比較的物件。  
  
 `dwCmpFlags`  
 在影響比較之[ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md)值的位元組合。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.Net Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合列舉](fusion-enumerations.md)
