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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5da2936a46dcf3d8f69acc3367db64712165b0cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock 方法
取得區段的區塊程式碼基底。  
  
 這個方法已經過時，不應使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a>參數  
 `section`  
 [in]要從中擷取的程式碼基底區塊 > 一節。  
  
 `len`  
 [in]要擷取區塊的長度。  
  
 `align`  
 [in]相對於開頭的區段中，用來對齊區塊的第一個位元組的位元組。 這是指區塊的區段內的位置。  
  
 `ppBytes`  
 [out]接收的擷取區塊位址的位置指標。  
  
## <a name="remarks"></a>備註  
 呼叫`GetSectionBlock`只有當您有不由其他方法處理的特殊區段需求。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
