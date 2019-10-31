---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 274bf79175bda9e880b1ef3cf8f125a017ad0734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121663"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法
函式與[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)相同，不同之處在于路徑字串會在結束的 null 字元之後以零填補，讓字串資料成為固定大小的 `MAX_PATH`。 只有在路徑字串長度本身小於 `MAX_PATH`時，才會提供填補。  
  
 這可讓您更輕鬆地撰寫與 PE 檔案不同的工具。  
  
## <a name="syntax"></a>語法  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>傳回值  
 傳回 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>請參閱

- [ISymUnmanagedWriter4 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
