---
title: ISymUnmanagedSourceServerModule::GetSourceServerData 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176574"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a>ISymUnmanagedSourceServerModule::GetSourceServerData 方法
返回模組的源伺服器資料。 調用方必須使用`CoTaskMemFree`釋放資源。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a>參數  
 `pDataByteCount`  
 [出]指向`ULONG32`接收源伺服器資料的大小（以位元組為單位）的指標。  
  
 `ppData`  
 [出]指向返回`pDataByteCount`值的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，S_OK;否則，E_FAIL或其他錯誤代碼。  
  
## <a name="requirements"></a>需求  
 **標題：** 科西姆.伊德爾，科西姆.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedSourceServerModule 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
