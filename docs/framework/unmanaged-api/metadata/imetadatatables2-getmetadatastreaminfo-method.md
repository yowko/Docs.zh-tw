---
title: IMetaDataTables2::GetMetaDataStreamInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 756b0ff726c31bf096a1c1b70004c3ff82fe9979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a>IMetaDataTables2::GetMetaDataStreamInfo 方法
取得名稱、 大小和指定之索引處的中繼資料資料流內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ix`  
 [in]要求的中繼資料資料流的索引。  
  
 `ppchName`  
 [out]指標的資料流名稱。  
  
 `ppv`  
 [out]中繼資料資料流的指標。  
  
 `pcb`  
 [out]大小，以位元組為單位的`ppv`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataTables2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [IMetaDataTables 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
