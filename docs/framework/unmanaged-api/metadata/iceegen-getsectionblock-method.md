---
title: ICeeGen::GetSectionBlock 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176080"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock 方法
獲取代碼庫的節塊。  
  
 此方法已過時，不應使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a>參數  
 `section`  
 [在]從中檢索代碼庫塊的部分。  
  
 `len`  
 [在]要檢索的塊的長度。  
  
 `align`  
 [在]相對於節的開頭的位元組，用於對齊塊的第一個位元組。 這是塊在節內的位置。  
  
 `ppBytes`  
 [出]指向接收檢索的塊位址的位置的指標。  
  
## <a name="remarks"></a>備註  
 僅當`GetSectionBlock`您有特殊節要求時，其他方法未處理，才調用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
