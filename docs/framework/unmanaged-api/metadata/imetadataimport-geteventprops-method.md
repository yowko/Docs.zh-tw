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
ms.openlocfilehash: 138be940c6a03fc58e488e344455946bdb832bab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777789"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps 方法
取得指定的事件語彙基元，包括宣告的型別、 新增和移除方法委派，和任何旗標和其他相關聯的資料所代表的事件的中繼資料資訊。  
  
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
  
## <a name="parameters"></a>參數  
 `ev`  
 [in]事件中繼資料語彙基元，表示要取得中繼資料的事件。  
  
 `pClass`  
 [out]表示宣告該事件之類別的 TypeDef 語彙基元指標。  
  
 `szEvent`  
 [out]所參考的事件名稱`ev`。  
  
 `pchEvent`  
 [in]所要求的長度，寬字元`szEvent`。  
  
 `pdwEventFlags`  
 [out]傳回寬字元的長度`szEvent`。  
  
 `ptkEventType`  
 [out]TypeRef 或 TypeDef 中繼資料語彙基元，代表指標<xref:System.Delegate>事件型別。  
  
 `pmdAddOn`  
 [out]表示將事件處理常式方法的中繼資料語彙基元指標。  
  
 `pmdRemoveOn`  
 [out]表示移除事件處理常式方法的中繼資料語彙基元指標。  
  
 `pmdFire`  
 [out]表示引發事件的方法中繼資料語彙基元指標。  
  
 `rmdOtherMethod`  
 [out]與事件相關聯的其他方法的語彙基元指標的陣列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。  
  
 `pcOtherMethod`  
 [out]權杖中傳回的數目`rmdOtherMethod`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
