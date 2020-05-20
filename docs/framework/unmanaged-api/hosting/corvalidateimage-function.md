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
ms.openlocfilehash: 8841fab0517353849ef99594bcbd03dda772c766
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616498"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage 函式
驗證受管理的模組映射，並在載入作業系統載入器之後通知它。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>參數  
 `ImageBase`  
 在要驗證為 managed 程式碼之影像起始位置的指標。 映射必須已經載入記憶體中。  
  
 `FileName`  
 在影像的檔案名。  
  
## <a name="return-value"></a>傳回值  
 此函式會傳回標準值 `E_INVALIDARG` 、、 `E_OUTOFMEMORY` `E_UNEXPECTED` 和 `E_FAIL` ，以及下列值。  
  
|傳回值|說明|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|映射無效。 此值具有 HRESULT 0xC000007BL。|  
|`STATUS_SUCCESS`|此映射有效。 此值具有 HRESULT 0x00000000L。|  
  
## <a name="remarks"></a>備註  
 在 Windows XP 和更新版本中，作業系統載入器會藉由檢查通用物件檔案格式（COFF）標頭中的 COM 描述專案錄位來檢查受控模組。 設定的位表示受控模組。 如果載入器偵測到受管理的模組，它會載入 Mscoree.dll 並呼叫 `_CorValidateImage` ，這會執行下列動作：  
  
- 確認映射是有效的受控模組。  
  
- 將影像中的進入點變更為 common language runtime （CLR）中的進入點。  
  
- 若是64位版本的 Windows，請將記憶體中的影像從 PE32 轉換為 PE32 + 格式，以修改該映射。  
  
- 載入 managed 模組映射時，返回載入器。  
  
 對於可執行映射，作業系統載入器會接著呼叫[_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)函式，而不論可執行檔中所指定的進入點為何。 對於 DLL 元件影像，載入器會呼叫[_CorDllMain](cordllmain-function.md)函式。  
  
 `_CorExeMain`或會 `_CorDllMain` 執行下列動作：  
  
- 初始化 CLR。  
  
- 從元件的 CLR 標頭尋找 managed 進入點。  
  
- 開始執行。  
  
 當卸載受控模組映射時，載入器會呼叫[_CorImageUnloading](corimageunloading-function.md)函式。 不過，此函數不會執行任何動作;它只會傳回。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
