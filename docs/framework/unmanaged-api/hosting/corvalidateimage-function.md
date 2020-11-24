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
ms.openlocfilehash: 2d49a40610bd0e1a7629594e245bde9eacfcc06d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687973"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage 函式

驗證受管理的模組映射，並在載入作業系統載入器之後通知作業系統載入器。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>參數  

 `ImageBase`  
 在要驗證為 managed 程式碼之影像的開始位置指標。 映射必須已經載入記憶體中。  
  
 `FileName`  
 在影像的檔案名。  
  
## <a name="return-value"></a>傳回值  

 此函數會傳回標準值 `E_INVALIDARG` 、 `E_OUTOFMEMORY` 、 `E_UNEXPECTED` 和 `E_FAIL` ，以及下列值。  
  
|傳回值|描述|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|映射無效。 此值具有 HRESULT 0xC000007BL。|  
|`STATUS_SUCCESS`|映射是有效的。 此值具有 HRESULT 0x00000000L。|  
  
## <a name="remarks"></a>備註  

 在 Windows XP 和更新版本中，作業系統載入器會檢查 managed 模組，方法是檢查通用物件檔案格式的 COM 描述專案錄位 (COFF) 標頭。 設定位表示受控模組。 如果載入器偵測到受管理的模組，它會載入 MsCorEE.dll 和呼叫 `_CorValidateImage` ，以執行下列動作：  
  
- 確認映射是有效的受控模組。  
  
- 將影像中的進入點變更為 common language runtime (CLR) 中的進入點。  
  
- 若為64位版本的 Windows，請將記憶體中的映射從 PE32 轉換為 PE32 + format，以修改記憶體中的影像。  
  
- 載入 managed 模組映射時，返回載入器。  
  
 針對可執行檔映射，作業系統載入器接著會呼叫 [_CorExeMain](corexemain-function.md) 函式，而不論可執行檔中指定的進入點為何。 針對 DLL 元件映射，載入器會呼叫 [_CorDllMain](cordllmain-function.md) 函式。  
  
 `_CorExeMain` 或 `_CorDllMain` 執行下列動作：  
  
- 初始化 CLR。  
  
- 從元件的 CLR 標頭尋找 managed 進入點。  
  
- 開始執行。  
  
 卸載 managed 模組映射時，載入器會呼叫 [_CorImageUnloading](corimageunloading-function.md) 函式。 不過，此函數不會執行任何動作;它只會傳回。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
