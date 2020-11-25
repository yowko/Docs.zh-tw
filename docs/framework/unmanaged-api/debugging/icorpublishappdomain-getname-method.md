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
ms.openlocfilehash: d6b05333b9e02c4202c0fd9bdee9b5c055aa4da3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694356"
---
# <a name="icorpublishappdomaingetname-method"></a>ICorPublishAppDomain::GetName 方法

取得此 [ICorPublishAppDomain](icorpublishappdomain-interface.md)所表示之應用程式域的名稱。  
  
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
 擴展陣列中傳回的寬字元數（包含 null 字元）的指標 `szName` 。  
  
 `szName`  
 擴展要在其中儲存名稱的陣列。  
  
## <a name="remarks"></a>備註  

 如果 `szName` 不是 null，方法會 `GetName` 複製到多 `cchName` 個字元， (包括) 的 null 結束字元 `szName` 。 如果在中傳回非 null，則 `pcchName` 名稱中的實際字元數 (包括 null 結束字元) 會儲存在 `szName` 陣列中。  
  
 `GetName`無論複製了多少個字元，方法都會傳回 S_OK HRESULT。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl、CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorPublishAppDomain 介面](icorpublishappdomain-interface.md)
