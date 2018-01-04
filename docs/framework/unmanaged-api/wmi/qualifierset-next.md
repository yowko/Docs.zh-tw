---
title: "QualifierSet_Next 函式 （Unmanaged API 參考）"
description: "QualifierSet_Next 函式會擷取下一步的限定詞列舉型別。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Next
helpviewer_keywords: QualifierSet_Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01a9c9d162039547849597aaa9c8a6fa38a31455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next 函式
擷取列舉型別呼叫啟動下一步的限定詞[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式。   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>參數

`vFunc`   
[in]未使用這個參數。

`ptr`   
[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。

`lFlags`   
[in]保留。 這個參數必須是 0。

`pstrName`   
[out]限定詞的名稱。 如果`null`，這個參數已忽略; 否則`pstrName`應該不指向有效`BSTR`或發生記憶體流失。 如果不是 null，函式一律會配置新`BSTR`當傳回`WBEM_S_NO_ERROR`。

`pVal`   
[out]成功時，辨識符號的值。 如果函式失敗，`VARIANT`指向`pVal`則不會修改。 如果這個參數是`null`，會忽略此參數。

`plFlavor`   
[out]接收限定詞標註的長指標。 如果不想要的類別資訊，這個參數可以是`null`。 

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼叫端沒有呼叫[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 使用開始新的列舉型別沒有足夠的記憶體。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 沒有多個限定詞會保留在列舉型別。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx)方法。

您呼叫`QualifierSet_Next`重複列舉所有的限定詞，直到函式傳回的函式`WBEM_S_NO_MORE_DATA`。 若要終止列舉早期，呼叫[QualifierSet_EndEnumeration](qualifierset-endenumeration.md)函式。

傳回在列舉期間的限定詞的順序是未定義。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
