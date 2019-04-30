---
title: IMetaDataInfo::GetFileMapping 方法
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c6a9473a698e4635c8b5cc9fb58963334dfd65e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992273"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping 方法
取得記憶體區域的對應的檔，以及對應的類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppvData`  
 [out]對應檔的開頭指標。  
  
 `pcbData`  
 [out]對應區域的大小。 如果`pdwMappingType`是`fmFlat`，這是檔案的大小。  
  
 `pdwMappingType`  
 [out]A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)值，指出對應的類型。 目前的實作的 common language runtime (CLR) 永遠傳回`fmFlat`。 其他值保留供日後使用。 不過，您一律應該確認傳回的值，因為其他值可能會在未來版本中啟用，或服務版本。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|所有的輸出會填滿。|  
|`E_INVALIDARG`|傳遞 NULL 做為引數的值。|  
|`COR_E_NOTSUPPORTED`|CLR 實作無法提供記憶體區域的相關資訊。 這種情形，原因如下：<br /><br /> -在中繼資料範圍以開啟`ofWrite`或`ofCopyMemory`旗標。<br />-在中繼資料範圍已開啟但`ofReadOnly`旗標。<br />- [Imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法用來開啟 僅中繼資料檔案的一部分。<br />-檔案不是可攜式執行檔 (PE) 檔案。 **注意：** 這些條件取決於 CLR 實作中，而且可能會減弱在未來的 CLR 版本。|  
  
## <a name="remarks"></a>備註  
 記憶體的`ppvData`指向無效，只要基礎的中繼資料範圍已開啟。  
  
 為了讓此方法才能運作，當您將磁碟上檔案的中繼資料對應到記憶體上呼叫[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，您必須指定`ofReadOnly`旗標，您必須指定`ofWrite`或`ofCopyMemory`旗標。  
  
 選擇每個範圍的檔案對應類型是 CLR 的指定實作的特定項目。 它不能由使用者設定。 目前實作的 clr 一律會傳回`fmFlat`在`pdwMappingType`，但這在 CLR 的版本，或未來的特定版本的服務版本可以在未來變更。 您一律應該檢查傳回的值`pdwMappingType`，因為不同的版面配置和位移，會有不同的型別。  
  
 不支援將傳遞的任何三個參數都是 NULL。 此方法會傳回`E_INVALIDARG`，且沒有任何輸出會填入。 忽略對應型別或區域的大小，可能會導致程式異常終止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataInfo 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping 列舉](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
