---
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5fd96f390b0bba60d1b95d20273bbf670208d41
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836651"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a>IMetaDataDispenserEx::OpenScopeOnITypeInfo 方法
這個方法尚未實作。 如果呼叫，它會傳回 E_NOTIMPL。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pITI`  
 [in]指標[ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo)提供要開啟範圍的類型資訊的介面。  
  
 `dwOpenFlags`  
 [in]開啟模式的旗標。  
  
 `riid`  
 [in]所需的介面。  
  
 `ppIUnk`  
 [out]傳回的介面指標的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱 <<c2> [ 系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataDispenserEx 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
