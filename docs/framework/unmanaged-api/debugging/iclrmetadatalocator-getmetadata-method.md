---
title: ICLRMetadataLocator::GetMetadata 方法
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: f0ba2342e9704ba06dd1d3612f699298c734a5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723515"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata 方法

由 common language runtime 呼叫 (CLR) 資料存取服務來取得影像的中繼資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a>參數  

 `imagePath`  
 在字串，指定影像檔案的路徑。  
  
 `imageTimestamp`  
 在影像檔案的時間戳記。  
  
 `imageSize`  
 在影像檔案的大小。  
  
 `mvid`  
 在影像的全域唯一識別碼。  
  
 `mdRva`  
 在中繼資料 (RVA) 的相對虛擬位址。 位址是相對於映射基底位址。  
  
 `flags`  
 在保留供日後使用。  
  
 `bufferSize`  
 在要在其中放置中繼資料的緩衝區大小。  
  
 `buffer`  
 擴展要在其中放置中繼資料的緩衝區。  
  
 `dataSize`  
 擴展傳回的中繼資料大小。  
  
## <a name="remarks"></a>備註  

 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRMetadataLocator 介面](iclrmetadatalocator-interface.md)
