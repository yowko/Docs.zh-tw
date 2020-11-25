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
ms.openlocfilehash: 9ce3afded5f914ecf970d8db738becc7f5cfff84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723138"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock 方法

取得程式碼基底的區段區塊。  
  
 這個方法已經過時，不應該使用。  
  
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
 在要從其中取得程式碼基底區塊的區段。  
  
 `len`  
 在要抓取之區塊的長度。  
  
 `align`  
 在相對於區段開頭的位元組，用來對齊區塊的第一個位元組。 這是區段內區塊的位置。  
  
 `ppBytes`  
 擴展接收已抓取區塊位址之位置的指標。  
  
## <a name="remarks"></a>備註  

 `GetSectionBlock`只有當您有不是由其他方法處理的特殊區段需求時，才需要呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICeeGen 介面](iceegen-interface.md)
