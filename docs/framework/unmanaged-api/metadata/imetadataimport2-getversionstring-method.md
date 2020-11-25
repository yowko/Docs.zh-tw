---
title: IMetaDataImport2::GetVersionString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 3e62b1177c0161883ad03086723cc43b71292df5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702559"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString 方法

取得用來建立元件之執行時間的版本號碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>參數  

 `pwzBuf`  
 擴展要儲存指定版本之字串的陣列。  
  
 `ccBufSize`  
 在陣列的大小（以寬字元為單位） `pwzBuf` 。  
  
 `pccBufSize`  
 擴展陣列中傳回的寬字元數，包括 null 結束字元 `pwzBuf` 。  
  
## <a name="remarks"></a>備註  

 `GetVersionString`方法會取得目前中繼資料範圍的內建版本。 如果從未儲存過範圍，它將不會有內建的版本，並且會傳回空字串。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport2 介面](imetadataimport2-interface.md)
- [IMetaDataImport 介面](imetadataimport-interface.md)
