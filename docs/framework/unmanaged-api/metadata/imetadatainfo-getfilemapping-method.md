---
title: "IMetaDataInfo::GetFileMapping 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f974230dc5ddf2a663f05fc06850f49f1de6e773
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>參數  
 `ppvData`  
 [out]對應檔的開頭指標。  
  
 `pcbData`  
 [out]對應區域的大小。 如果`pdwMappingType`是`fmFlat`，這是檔案的大小。  
  
 `pdwMappingType`  
 [out]A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)值，指出對應的類型。 目前實作的 common language runtime (CLR) 一律會傳回`fmFlat`。 其他值被保留供未來使用。 不過，您應該一律確認傳回的值，因為可能在未來版本中啟用其他值，或服務版本。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|所有輸出會填都滿。|  
|`E_INVALIDARG`|傳遞 NULL 做為引數的值。|  
|`COR_E_NOTSUPPORTED`|CLR 實作無法提供記憶體區域的相關資訊。 這種情形，原因如下：<br /><br /> -在中繼資料範圍以開啟`ofWrite`或`ofCopyMemory`旗標。<br />-在中繼資料範圍已開啟但`ofReadOnly`旗標。<br />- [Imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法用來開啟僅中繼資料檔案的一部分。<br />-檔案不是可移植執行檔 (PE) 檔案。 **注意：**這些條件取決於 CLR 實作，並可可能會影響在未來的 CLR 版本。|  
  
## <a name="remarks"></a>備註  
 記憶體的`ppvData`指向無效，只要基礎中繼資料範圍已開啟。  
  
 為了讓您藉由呼叫對應到記憶體中的磁碟上檔案的中繼資料時使用這個方法[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，您必須指定`ofReadOnly`旗標，而且您必須指定`ofWrite`或`ofCopyMemory`旗標。  
  
 選擇每個範圍的檔案對應類型是 CLR 的特定實作的特定項目。 無法由使用者設定。 目前實作的 clr 一律會傳回`fmFlat`中`pdwMappingType`，但可能會變更在未來版本的 CLR 或未來的指定版本的版本更新服務。 請務必檢查傳回的值`pdwMappingType`，因為不同類型會有不同的版面配置和位移。  
  
 不支援傳遞任何三個參數為 NULL。 方法會傳回`E_INVALIDARG`，和輸出會填滿。 忽略對應型別或區域的大小，可能會導致程式異常終止。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataInfo 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [CorFileMapping 列舉](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
