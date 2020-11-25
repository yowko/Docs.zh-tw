---
title: CreateAssemblyNameObject 函式
ms.date: 03/30/2017
api_name:
- CreateAssemblyNameObject
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyNameObject
helpviewer_keywords:
- CreateAssemblyNameObject function [.NET Framework fusion]
ms.assetid: 55c8b41e-fbe4-4ae0-aa29-68fbb2311691
topic_type:
- apiref
ms.openlocfilehash: 995f1064c2f40005c4a19ef034d7edfd668b5d51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704158"
---
# <a name="createassemblynameobject-function"></a>CreateAssemblyNameObject 函式

取得 [IAssemblyName](iassemblyname-interface.md) 實例的介面指標，該實例表示具有指定名稱之元件的唯一識別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateAssemblyNameObject (  
    [out] LPASSEMBLYNAME  *ppAssemblyNameObj,  
    [in]  LPCWSTR         szAssemblyName,  
    [in]  DWORD           dwFlags,  
    [in]  LPVOID          pvReserved  
 );  
```  
  
## <a name="parameters"></a>參數  

 `ppAssemblyNameObj`  
 擴展傳回的 `IAssemblyName` 。  
  
 `szAssemblyName`  
 在要建立新實例的元件名稱 `IAssemblyName` 。  
  
 `dwFlags`  
 在要傳遞至物件的函式的旗標。  
  
 `pvReserved`  
 在保留供未來擴充性之用。 `pvReserved` 必須是 null 參考。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
