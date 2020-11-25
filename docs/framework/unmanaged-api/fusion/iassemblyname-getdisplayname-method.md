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
ms.openlocfilehash: 13d71a9da2539c45076e5eb92e153e37c1df4b47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727909"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName 方法

取得這個 [IAssemblyName](iassemblyname-interface.md) 物件所參考之元件的人類可讀取名稱。  
  
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
 擴展字串緩衝區，其中包含參考元件的名稱。  
  
 `pccDisplayName`  
 [in，out] `szDisplayName` 以寬字元為單位的大小，包括 null 結束字元字元。  
  
 `dwDisplayFlags`  
 在 [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) 值的位元組合，這些值會影響的功能 `szDisplayName` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合列舉](fusion-enumerations.md)
