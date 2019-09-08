---
title: IAssemblyName::GetDisplayName 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f48f2d95829d2c8111065e5f4ede4e43a16d63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796660"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName 方法
取得這個[IAssemblyName](iassemblyname-interface.md)物件所參考之元件的人類可讀名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `szDisplayName`  
 脫銷包含所參考元件名稱的字串緩衝區。  
  
 `pccDisplayName`  
 [in、out]`szDisplayName`以寬字元為單位的大小，包括 null 結束字元字元。  
  
 `dwDisplayFlags`  
 在[ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md)值的位元組合，會影響的功能`szDisplayName`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合列舉](fusion-enumerations.md)
