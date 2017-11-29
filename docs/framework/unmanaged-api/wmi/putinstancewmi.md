---
title: "PutInstanceWmi 函式 （Unmanaged API 參考）"
description: "PutInstanceWmi 函式會建立或更新現有類別的執行個體。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7a4ffce4789fb59d84778d02b41910c974216bd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi 函式
建立或更新現有類別的執行個體。 WMI 存放庫會寫入執行個體。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>參數

`pInst`    
[in]要寫入的執行個體的指標。

`lFlags`   
[in]影響此函式的行為的旗標的組合。 下列的值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中： 

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果設定，WMI 不會儲存任何限定詞與**Amended**類別。 </br> 如果未設定，它會假設，此物件不會進行當地語系化，且所有限定詞 storedwith 這個執行個體。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 如果不存在，或是覆寫它，如果它已經存在，請建立執行個體。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | 更新執行個體。 若要成功呼叫必須存在之執行個體。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | 建立執行個體。 如果已經有該執行個體，呼叫將會失敗。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 |

`pCtx`  
[in]一般而言，這個值是`null`。 否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可用的提供者所提供的要求的類別的執行個體。 

`ppCallResult`  
[out]如果`null`，不使用這個參數。 如果`lFlags`包含`WBEM_FLAG_RETURN_IMMEDIATELY`，函式立即傳回且`WBEM_S_NO_ERROR`。 `ppCallResult`參數接收新的指標[IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx)物件。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有權限來更新指定類別的執行個體。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生意外的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 支援這個執行個體的類別無效。 |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null`屬性不能指定`null`，例如，標示**索引**或**Not_Null**限定詞。 |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | 指定的執行個體不是有效的。 (例如，呼叫`PutInstanceWmi`類別會傳回此值。) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`指定的旗標，但執行個體已經存在。 |
| `WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`中指定了`lFlags`，但執行個體不存在。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 是可能已停止和重新啟動。 呼叫[ConnectServerWmi](connectserverwmi.md)一次。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx)方法。

`PutInstanceWmi`函式建立執行個體，並更新現有的類別的執行個體的支援。  如何根據`pCtx`設定參數時，部分或所有執行個體的屬性會更新。 

當執行個體所指`pInst`屬於 Windows 管理子類別，呼叫的所有提供者負責從子類別衍生的類別。 所有這些提供者必須原始成功`PutInstanceWmi`要求才能成功。 支援的最上層的類別階層架構中的提供者會呼叫第一次。 按呼叫順序會繼續進行的最上層類別的子類別，然後從上到下直到 Windows 管理到達的提供者擁有所指向的執行個體的類別`pInst`。
Windows 管理未呼叫提供者的任何子類別的執行個體。 

當應用程式必須更新所屬的類別階層架構中，執行個體`pInst`參數必須指向包含要修改之屬性的執行個體。 也就是說，請考慮目標執行個體屬於**ClassB**。 **ClassB**執行個體是衍生自**ClassA**，和**ClassA**定義屬性**PropA**。 如果應用程式就會想要變更的值**PropA**中**ClassB**執行個體，它必須設定`pInst`該執行個體，而不是執行個體**ClassA**.

呼叫`PutInstanceWmi`不允許抽象類別的執行個體上。

如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
