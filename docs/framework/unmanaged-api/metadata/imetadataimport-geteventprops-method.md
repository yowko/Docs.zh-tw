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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177262"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps 方法
獲取由指定事件權杖表示的事件的中繼資料資訊，包括聲明類型、代理的添加和刪除方法以及任何標誌和其他關聯資料。  
  
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
 [在]表示要獲取其中繼資料的事件中繼資料權杖。  
  
 `pClass`  
 [出]指向表示聲明事件的類的 TypeDef 權杖的指標。  
  
 `szEvent`  
 [出]引用`ev`的事件的名稱。  
  
 `pchEvent`  
 [在]請求的長度以寬字元。 `szEvent`  
  
 `pdwEventFlags`  
 [出]返回的長度以寬字元。 `szEvent`  
  
 `ptkEventType`  
 [出]指向表示事件<xref:System.Delegate>類型的 TypeRef 或 TypeDef 中繼資料權杖的指標。  
  
 `pmdAddOn`  
 [出]指向中繼資料權杖的指標，表示為事件添加處理常式的方法。  
  
 `pmdRemoveOn`  
 [出]指向表示刪除事件處理常式的方法的中繼資料權杖的指標。  
  
 `pmdFire`  
 [出]指向表示引發事件的方法的中繼資料權杖的指標。  
  
 `rmdOtherMethod`  
 [出]指向與事件關聯的其他方法的權杖指標陣列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。  
  
 `pcOtherMethod`  
 [出]在 中`rmdOtherMethod`返回的權杖數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
