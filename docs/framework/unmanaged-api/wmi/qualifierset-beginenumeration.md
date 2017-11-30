---
title: "QualifierSet_BeginEnumeration 函式 （Unmanaged API 參考）"
description: "QualifierSet_BeginEnumeration 函式會重設物件的辨識符號的列舉值。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_BeginEnumeration
helpviewer_keywords: QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f66df772032b8e96b4956f3ed9a5818e961bd919
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetbeginenumeration-function"></a>QualifierSet_BeginEnumeration 函式
將物件的辨識符號的列舉值重設列舉的開頭。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>參數

`vFunc`   
[in]未使用這個參數。

`ptr`   
[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。

`lFlags`   
[in]旗標或描述中值的位元組合[備註](#remarks)區段，指定要包含在列舉中的限定詞。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags`參數無效。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二個呼叫`QualifierSet_BeginEnumeration`所沒有的中間呼叫[ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 使用開始新的列舉型別沒有足夠的記憶體。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx)方法。

若要列舉所有的物件上的限定詞，必須呼叫這個方法的第一個呼叫之前[QualifierSet_Next](qualifierset-next.md)。 限定詞會列舉中的順序被保證能夠針對指定的列舉型別而異。

可以做為傳遞的旗標`lEnumFlags`引數中所定義*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中。   

|常數  |值  |描述  |
|---------|---------|---------|
|  | 0 | 傳回所有限定詞的名稱。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 傳回目前的屬性或物件特定限定詞的名稱。 <br/> 屬性： 返回 （包括覆寫） 的屬性特定辨識符號，並不是這些限定詞傳播從類別定義。 <br/> 執行個體： 傳回只可使用特定執行個體的限定詞名稱。 <br/> 類別： 返回衍生的類別 beiong 特定只限定詞。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 傳回的傳播限定詞的名稱，從另一個物件。 <br/> 屬性： 傳回僅限定詞傳播給這個屬性從類別定義中，而不從本身的屬性。 <br/> 執行個體： 傳回傳播這些辨識符號，從類別定義。 <br/> 類別： 傳回繼承自父類別的只有這些限定詞的名稱。 |

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
