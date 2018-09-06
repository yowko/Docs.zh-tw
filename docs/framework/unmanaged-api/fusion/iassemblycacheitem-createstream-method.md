---
title: IAssemblyCacheItem::CreateStream 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b3242e8ae29b9d21dc50d3ea0476967e9746f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031371"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream 方法
建立具有指定的名稱和格式的資料流。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFlags`  
 [in]支援下列值： 旗標。  
  
 `pszStreamName`  
 [in]若要建立資料流的名稱。  
  
 `dwFormat`  
 [in]若要串流處理檔案的格式。  
  
 `dwFormatFlags`  
 [in]支援下列值： 格式特有的旗標。  
  
 `ppIStream`  
 [out]傳回的位址指標[IStream](/windows/desktop/api/objidl/nn-objidl-istream)執行個體。  
  
 `puliMaxSize`  
 [in，選用]所參考的資料流的大小上限`ppIStream`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IAssemblyCacheItem 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
