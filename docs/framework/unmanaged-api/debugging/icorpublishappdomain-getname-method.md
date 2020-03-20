---
title: ICorPublishAppDomain::GetName 方法
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178410"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName 方法
獲取此[ICorPublishAppDomain](icorpublishappdomain-interface.md)表示的應用程式域的名稱。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a>參數  
 `cchName`  
 [in] `szName` 陣列的大小。  
  
 `pcchName`  
 [出]陣列中返回的指向寬字元數（包括空字元）的`szName`指標。  
  
 `szName`  
 [出]要在其中存儲名稱的陣列。  
  
## <a name="remarks"></a>備註  
 如果`szName`為非空，`GetName`則該方法將最多複製到`cchName`字元（包括空結束字元）到`szName`中。 如果在 中`pcchName`返回非 null，則名稱中（包括空結束字元）中的實際字元數存儲在陣列中`szName`。  
  
 無論`GetName`複製的字元數如何，該方法都會返回S_OK HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾普布.idl， 科爾普布.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorPublishAppDomain 介面](icorpublishappdomain-interface.md)
