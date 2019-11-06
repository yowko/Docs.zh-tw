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
ms.openlocfilehash: 5dbb5dc483bc5a08c59606654d55b5a62266e509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134373"
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
 [in、out]以寬字元為單位的 `szDisplayName` 大小，包括 null 結束字元字元。  
  
 `dwDisplayFlags`  
 在[ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md)值的位元組合，這個組合會影響 `szDisplayName`的功能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合列舉](fusion-enumerations.md)
