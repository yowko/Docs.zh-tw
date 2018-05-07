---
title: NextMethod 函式 （Unmanaged API 參考）
description: NextMethod 函式會擷取列舉中的下一個方法。
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd4559663194cb845fb0cc040e1f6739e38caa0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nextmethod-function"></a>NextMethod 函式
擷取下一個方法呼叫開始列舉型別中的[BeginMethodEnumeration](beginmethodenumeration.md)。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`lFlags`  
[in]保留。 這個參數必須是 0。

`pName`  
[out]指標指向`null`之前呼叫。 當函式傳回時，新的位址`BSTR`，其中包含方法名稱。 

`ppSignatureIn`  
[out]接收資料指標的指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)包含`in`方法的參數。 

`ppSignatureOut`  
[out]接收資料指標的指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)包含`out`方法的參數。 

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有不需要呼叫[ `BeginEnumeration` ](beginenumeration.md)函式。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有其他內容。 |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)方法。

呼叫端會開始將列舉序列呼叫[BeginMethodEnumeration](beginmethodenumeration.md)函式，，然後再呼叫 [NextMethod] 函式，直到此函數會傳回`WBEM_S_NO_MORE_DATA`。 （選擇性） 呼叫端會完成序列藉由呼叫[EndMethodEnumeration](endmethodenumeration.md)。 呼叫端可能會提早終止列舉型別，藉由呼叫[EndMethodEnumeration](endmethodenumeration.md)在任何時間。

## <a name="example"></a>範例

如需 c + + 的範例，請參閱[IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx)方法。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
