---
title: "ICeeGen::GetSectionDataLen 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionDataLen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 217a6c87d5152b68e062d9c2a64ec78478f301cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectiondatalen-method"></a>ICeeGen::GetSectionDataLen 方法
取得指定之區段的長度。  
  
 這個方法已經過時，不應使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a>參數  
 `section`  
 [in]資料區段，將擷取其長度。  
  
 `dataLen`  
 [out]傳回指定之區段的長度。  
  
## <a name="remarks"></a>備註  
 呼叫`GetSectionDataLen`只有當您有不由其他方法處理的特殊區段需求。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
