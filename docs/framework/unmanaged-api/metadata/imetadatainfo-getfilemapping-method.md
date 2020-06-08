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
ms.openlocfilehash: 5ef5d9ae3da4dff13a461162f0ba3466d3d8192c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501257"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping 方法
取得對應檔案的記憶體區域，以及對應的類型。  
  
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
 脫銷對應檔案開頭的指標。  
  
 `pcbData`  
 脫銷對應區域的大小。 如果 `pdwMappingType` 是 `fmFlat` ，這就是檔案的大小。  
  
 `pdwMappingType`  
 脫銷表示對應類型的[CorFileMapping](corfilemapping-enumeration.md)值。 Common language runtime （CLR）的目前執行一律會傳回 `fmFlat` 。 保留其他值供以後使用。 不過，您應該一律驗證傳回的值，因為未來版本或服務版本可能會啟用其他值。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|`S_OK`|所有輸出都會填滿。|  
|`E_INVALIDARG`|傳遞 Null 做為引數值。|  
|`COR_E_NOTSUPPORTED`|CLR 執行無法提供記憶體區域的相關資訊。 這可能因為以下原因而發生：<br /><br /> -中繼資料範圍已以 `ofWrite` 或旗標開啟 `ofCopyMemory` 。<br />-中繼資料範圍在沒有旗標的情況下開啟 `ofReadOnly` 。<br />- [IMetaDataDispenser：： OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md)方法只會用來開啟檔案的中繼資料部分。<br />-檔案不是可移植的可執行檔（PE）。 **注意：** 這些條件取決於 CLR 的執行，而且可能會在未來的 CLR 版本中減弱。|  
  
## <a name="remarks"></a>備註  
 `ppvData`只有在基礎中繼資料範圍已開啟時，指向的記憶體才有效。  
  
 為了讓這個方法能夠正常執行，當您藉由呼叫[IMetaDataDispenser：： OpenScope](imetadatadispenser-openscope-method.md)方法，將磁片上檔案的中繼資料對應至記憶體時，您必須指定 `ofReadOnly` 旗標，而且不得指定 `ofWrite` 或旗標 `ofCopyMemory` 。  
  
 針對每個範圍所選擇的檔案對應類型，是特定的 CLR 執行。 不能由使用者設定。 CLR 目前的執行一律 `fmFlat` 會傳回中的 `pdwMappingType` ，但在未來的 clr 版本或特定版本的未來服務版本中，這可能會變更。 您應該一律檢查中傳回的值 `pdwMappingType` ，因為不同的類型會有不同的版面配置和位移。  
  
 不支援為三個參數傳遞 Null。 方法會傳回 `E_INVALIDARG` ，而且不會填入任何輸出。 忽略對應類型或區域大小可能會導致異常程式終止。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataInfo 介面](imetadatainfo-interface.md)
- [CorFileMapping 列舉](corfilemapping-enumeration.md)
