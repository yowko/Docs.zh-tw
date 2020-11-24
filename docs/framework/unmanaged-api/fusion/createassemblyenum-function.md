---
title: CreateAssemblyEnum 函式
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
ms.openlocfilehash: b7e3696121475885f5061bd96eb6905d7ccae734
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683169"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum 函式

取得 [IAssemblyEnum](iassemblyenum-interface.md) 實例的指標，該實例可以使用指定的 [IAssemblyName](iassemblyname-interface.md)來列舉元件中的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>參數  

 `pEnum`  
 擴展包含所要求指標之記憶體位置的指標 `IAssemblyEnum` 。  
  
 `pUnkReserved`  
 在保留供未來擴充性之用。 `pUnkReserved` 必須是 null 參考。  
  
 `pName`  
 在所 `IAssemblyName` 要求元件的。 這個名稱是用來篩選列舉。 它可以是 null，以列舉全域組件快取中的所有元件。  
  
 `dwFlags`  
 在用來修改列舉值行為的旗標。 此參數只包含 [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) 列舉中的一個位。  
  
 `pvReserved`  
 在保留供未來擴充性之用。 `pvReserved` 必須是 null 參考。  
  
## <a name="remarks"></a>備註  

 `dwFlags`參數只包含列舉中的一個位 `ASM_CACHE_FLAGS` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyEnum 介面](iassemblyenum-interface.md)
- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
