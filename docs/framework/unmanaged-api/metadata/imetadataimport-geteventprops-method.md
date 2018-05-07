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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac1ecb73257782888c963082953ed243177a86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps 方法
取得指定的事件語彙基元，包括宣告類型、 新增和移除方法的委派，以及任何旗標和其他相關聯的資料所代表事件的中繼資料資訊。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `ev`  
 [in]事件中繼資料語彙基元，代表要取得的中繼資料的事件。  
  
 `pClass`  
 [out]代表宣告的事件類別的 TypeDef 語彙基元指標。  
  
 `szEvent`  
 [out]事件所參考的名稱`ev`。  
  
 `pchEvent`  
 [in]所要求的長度，以寬字元`szEvent`。  
  
 `pdwEventFlags`  
 [out]傳回的寬字元的長度`szEvent`。  
  
 `ptkEventType`  
 [out]TypeRef 或 TypeDef 中繼資料語彙基元，代表的指標<xref:System.Delegate>事件型別。  
  
 `pmdAddOn`  
 [out]代表加入事件處理常式的方法中繼資料語彙基元的指標。  
  
 `pmdRemoveOn`  
 [out]代表移除事件處理常式的方法中繼資料語彙基元的指標。  
  
 `pmdFire`  
 [out]代表引發事件的方法中繼資料語彙基元的指標。  
  
 `rmdOtherMethod`  
 [out]陣列的其他方法與事件相關聯的語彙基元指標。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。  
  
 `pcOtherMethod`  
 [out]傳回的 token 數目`rmdOtherMethod`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
