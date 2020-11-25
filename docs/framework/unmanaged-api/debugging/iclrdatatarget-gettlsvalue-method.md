---
title: ICLRDataTarget::GetTLSValue 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: f6066774961b3fba2c466e156296907efc2e53df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703404"
---
# <a name="iclrdatatargetgettlsvalue-method"></a>ICLRDataTarget::GetTLSValue 方法

從執行緒區域儲存區取得值， (目標進程中指定之執行緒的 TLS) 。 Common language runtime (CLR) 資料存取服務會呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a>參數  

 `threadID`  
 在目標進程中線程的作業系統識別碼。  
  
 `index`  
 在位置的索引。 在指定之執行緒的本機存放區中，此值必須是有效的索引。  
  
 `value`  
 擴展 `CLRDATA_ADDRESS` 值的指標，指定從指定的 TLS 位置傳回的值。  
  
## <a name="remarks"></a>備註  

 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
