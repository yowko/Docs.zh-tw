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
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175261"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping 方法
獲取映射檔的記憶體區域和映射類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppvData`  
 [出]指向映射檔開頭的指標。  
  
 `pcbData`  
 [出]映射區域的大小。 如果是`pdwMappingType``fmFlat`，則這是檔的大小。  
  
 `pdwMappingType`  
 [出]指示映射類型的[CorFile 映射](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)值。 公共語言運行時 （CLR） 的當前實現始終返回`fmFlat`。 保留其他值供以後使用。 但是，應始終驗證返回的值，因為將來的版本或服務版本中可能會啟用其他值。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|所有輸出都已填充。|  
|`E_INVALIDARG`|Null 作為參數值傳遞。|  
|`COR_E_NOTSUPPORTED`|CLR 實現不能提供有關記憶體區域的資訊。 這可能因為以下原因而發生：<br /><br /> - 中繼資料作用域已打開`ofWrite`，`ofCopyMemory`或 標誌。<br />- 中繼資料作用域在沒有`ofReadOnly`標誌的情況下打開。<br />- [IMetaDataDispenser：：OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)方法僅用於打開檔的中繼資料部分。<br />- 該檔不是可攜式可執行檔 （PE）。 **注：** 這些條件取決於 CLR 實現，並且將來版本的 CLR 可能會減弱。|  
  
## <a name="remarks"></a>備註  
 只要基礎中繼資料`ppvData`作用域處於打開狀態，指向的記憶體才有效。  
  
 為了使此方法正常工作，當您通過調用[IMetaDataDispenser：：openScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法將磁片檔的元資料對應到記憶體時，必須指定`ofReadOnly`標誌，並且不能指定`ofWrite`或`ofCopyMemory`標誌。  
  
 每個作用域的檔案對應類型的選擇特定于 CLR 的給定實現。 使用者無法設置它。 CLR 的當前實現始終在`fmFlat`中`pdwMappingType`返回，但這可能在 CLR 的未來版本或給定版本的將來服務版本中更改。 應始終在 中`pdwMappingType`檢查返回的值，因為不同類型的佈局和偏移量將不同。  
  
 不支援為三個參數中的任何一個傳遞 Null。 該方法返回`E_INVALIDARG`，並且不會填充任何輸出。 忽略映射類型或區域大小可能會導致異常程式終止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataInfo 介面](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping 列舉](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
