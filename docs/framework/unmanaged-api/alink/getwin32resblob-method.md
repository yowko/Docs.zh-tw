---
title: GetWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f40b99c0a81bf0f2b622c7d23157dbb5736df1ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob 方法
擷取 Win32 資源 blob。 設定組件選項之後呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `AssemblyID`  
 組件的識別碼。  
  
 `FileToken`  
 用來擷取建構的 Win32 版本資源時所要使用的檔名語彙基元檔案  
  
 `fDll`  
 如果檔案是 DLL，false EXE，則為 TRUE。  
  
 `pszIconFile`  
 要插入資源 blob 的選擇性圖示。  
  
 `ppResBlob`  
 接收資源 blob。  
  
 `pcbResBlob`  
 接收 blob 的大小。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
