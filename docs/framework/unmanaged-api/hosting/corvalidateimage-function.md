---
title: _CorValidateImage 函式
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178221"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage 函式
驗證託管模組映射，並在載入作業系統載入器後通知它們。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>參數  
 `ImageBase`  
 [在]指向映射的起始位置的指標，以驗證為託管代碼。 圖像必須已載入到記憶體中。  
  
 `FileName`  
 [在]圖像的檔案名。  
  
## <a name="return-value"></a>傳回值  
 此函數返回標準`E_INVALIDARG`值`E_OUTOFMEMORY`、和`E_UNEXPECTED` `E_FAIL`，以及以下值。  
  
|傳回值|描述|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|圖像無效。 此值具有 HRESULT 0xC000007BL。|  
|`STATUS_SUCCESS`|圖像有效。 此值具有 HRESULT 0x0000000L。|  
  
## <a name="remarks"></a>備註  
 在 Windows XP 和更高版本中，作業系統載入程式通過檢查公共物件檔案格式 （COFF） 標頭中的 COM 描述項目錄位來檢查託管模組。 設置位表示託管模組。 如果載入程式檢測到託管模組，它將載入 MsCorEE.dll 和調用`_CorValidateImage`，這將執行以下操作：  
  
- 確認映射是有效的託管模組。  
  
- 將圖像中的進入點更改為通用語言運行時 （CLR） 中的進入點。  
  
- 對於 64 位版本的 Windows，通過將映射從 PE32 轉換為 PE32+ 格式來修改記憶體中的圖像。  
  
- 載入託管模組映射時返回載入程式。  
  
 對於可執行映射，作業系統載入程式然後調用[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函數，而不考慮可執行檔中指定的進入點。 對於 DLL 裝配體映射，載入程式調用[_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)函數。  
  
 `_CorExeMain`或`_CorDllMain`執行以下操作：  
  
- 初始化 CLR。  
  
- 從程式集的 CLR 標頭中查找託管進入點。  
  
- 開始執行。  
  
 卸載託管模組映射時，載入程式調用[_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)函數。 但是，此函數不執行任何操作;因此，此操作不會執行任何操作。它只是返回。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
