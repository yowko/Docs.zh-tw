---
title: _EFN_GetManagedObjectFieldInfo 函式
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: 4c088b7e1096f8b4cad11a3e27b4045e233989ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676214"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a>\_EFN \_ GetManagedObjectFieldInfo 函式

使用所提供的物件指標和欄位名稱來取得從物件開始到欄位的位移以及欄位的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a>參數  

 `Client`  
 在Debug 用戶端的指標。  
  
 `objAddr`  
 在Managed 物件指標。  
  
 szFieldName  
 在功能變數名稱的 managed 物件指標。  
  
 `pValue`  
 擴展域值。 此參數可以是 null。  
  
 `pOffset`  
 擴展從 `objAddr` 到欄位的位移。 此參數可以是 null。  
  
## <a name="remarks"></a>備註  

 如果位移為0，則不會寫入位移。  
  
 如果目前在內容中的執行緒上沒有 managed 程式碼，此函式會傳回 HRESULT SOS_E_NOMANAGEDCODE 具有0xa0 的設備值和錯誤碼0x1000。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](debugging-global-static-functions.md)
