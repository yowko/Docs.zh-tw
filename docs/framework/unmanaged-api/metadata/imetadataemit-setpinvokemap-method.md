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
ms.openlocfilehash: 4c68754bc44fe035fd8e7143c52895928beae395
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175586"
---
# <a name="imetadataemitsetpinvokemap-method"></a>IMetaDataEmit::SetPinvokeMap 方法
設置或更改方法的 PInvoke 簽名的功能，由之前調用[IMetaDataEmit：:DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)定義。  
  
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
 [在]映射`mdToken`資訊應用於的。  
  
 `dwMappingFlags`  
 [在]PInvoke 用於執行映射的標誌。 這是值的`CorPinvokeMap`位元遮罩。  
  
 `szImportName`  
 [在]本機 DLL 中的目標匯出的名稱。  
  
 `mrImportDLL`  
 [在]目標`mdModuleRef`非託管 DLL 的權杖。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MSCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
