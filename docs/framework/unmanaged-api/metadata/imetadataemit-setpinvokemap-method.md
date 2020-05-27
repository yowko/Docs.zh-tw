---
title: IMetaDataEmit::SetPinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
ms.openlocfilehash: 0d34c7a2992a2779b96ec87f1a0175d8fcbce34a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007789"
---
# <a name="imetadataemitsetpinvokemap-method"></a>IMetaDataEmit::SetPinvokeMap 方法
設定或變更方法之 PInvoke 簽章的功能，如先前的 IMetaDataEmit 呼叫所定義[：:D 的 efinepinvokemap](imetadataemit-definepinvokemap-method.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPinvokeMap (
    [in]  mdToken      tk,
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,
    [in]  mdModuleRef  mrImportDLL
);  
```  
  
## <a name="parameters"></a>參數  
 `tk`  
 在`mdToken`套用對應資訊的。  
  
 `dwMappingFlags`  
 在PInvoke 用來執行對應的旗標。 這是值的位元遮罩 `CorPinvokeMap` 。  
  
 `szImportName`  
 在原生 DLL 中的目標匯出名稱。  
  
 `mrImportDLL`  
 在`mdModuleRef`目標非受控 DLL 的 token。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
