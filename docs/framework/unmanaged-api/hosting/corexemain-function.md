---
title: _CorExeMain 函式
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
ms.openlocfilehash: 935ac478fb966315e81fdcc004761038b28e3178
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616586"
---
# <a name="_corexemain-function"></a>_CorExeMain 函式
初始化 common language runtime （CLR），尋找可執行元件的 CLR 標頭中的 managed 進入點，然後開始執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>備註  
 此函式是由 managed 可執行元件所建立之進程中的載入器所呼叫。 對於 DLL 元件，載入器會改為呼叫[_CorDllMain](cordllmain-function.md)函式。  
  
 無論影像檔案中指定的進入點為何，作業系統載入器都會呼叫這個方法。  
  
 在 Windows 98、Windows ME、Windows NT 和 Windows 2000 中，函式 `_CorExeMain` 會透過作業系統載入器中的修復間接呼叫。 在所有其他版本的 Windows 中，作業系統載入器會直接呼叫它。  
  
 如需詳細資訊，請參閱[_CorValidateImage](corvalidateimage-function.md)主題中的「備註」一節。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料全域靜態函式](../metadata/metadata-global-static-functions.md)
