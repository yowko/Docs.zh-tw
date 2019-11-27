---
title: IMetaDataImport::GetEventProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 18fe0c834506d0ac4cd15fd7af4c4f15904b0f81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437582"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps 方法
取得指定的事件 token 所代表之事件的中繼資料資訊，包括宣告類型、委派的加入和移除方法，以及任何旗標和其他相關聯的資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a>參數  
 `ev`  
 在事件元資料標記，代表要取得中繼資料的事件。  
  
 `pClass`  
 脫銷TypeDef token 的指標，代表宣告事件的類別。  
  
 `szEvent`  
 脫銷`ev`所參考的事件名稱。  
  
 `pchEvent`  
 在要求的 `szEvent`長度（以寬字元為單位）。  
  
 `pdwEventFlags`  
 脫銷以 `szEvent`的寬字元傳回的長度。  
  
 `ptkEventType`  
 脫銷表示事件之 <xref:System.Delegate> 類型的 TypeRef 或 TypeDef 元資料標記的指標。  
  
 `pmdAddOn`  
 脫銷元資料標記的指標，表示新增事件處理常式的方法。  
  
 `pmdRemoveOn`  
 脫銷元資料標記的指標，表示移除事件處理常式的方法。  
  
 `pmdFire`  
 脫銷元資料標記的指標，表示引發事件的方法。  
  
 `rmdOtherMethod`  
 脫銷與事件相關聯之其他方法的 token 指標陣列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。  
  
 `pcOtherMethod`  
 脫銷`rmdOtherMethod`中傳回的權杖數目。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
