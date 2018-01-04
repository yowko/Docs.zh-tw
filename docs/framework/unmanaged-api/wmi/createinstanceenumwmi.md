---
title: "CreateInstanceEnumWmi 函式 （Unmanaged API 參考）"
description: "CreateInstanceEnumWmi 函式會傳回包含指定的類別符合選取準則的執行個體的列舉值。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CreateInstanceEnumWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CreateInstanceEnumWmi
helpviewer_keywords: CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b796771b07dee28470d37ca3e4292c0a244e056b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createinstanceenumwmi-function"></a>CreateInstanceEnumWmi 函式
傳回列舉值，會傳回符合指定的選取準則指定類別的執行個體。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a>參數

`strFilter`    
[in]類別想要與執行個體的名稱。 此參數不得為`null`。

`lFlags`   
[in]影響此函式的行為的旗標的組合。 下列的值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中： 

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 如果集合，此函式會擷取目前連接的地區設定當地語系化的命名空間中儲存已修改的限定詞。 <br/> 如果未設定，此函數會擷取只儲存立即命名空間中的限定詞。 |
| `WBEM_FLAG_DEEP` | 0 | 列舉會包含這和所有子類別階層架構中。 |
| `WBEM_FLAG_SHALLOW` | 1 | 列舉包含這個類別只能純粹執行個體，但不包括提供此類別中找不到屬性的子類別的所有執行個體。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | 旗標會造成半同步呼叫。 |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | 函數會傳回順向的列舉值。 一般而言，順向的列舉程式會更快，並使用較少的記憶體比傳統的列舉值，但不是允許呼叫[複製](clone.md)。 |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI 會保留 enumration 中物件的指標，直到釋放為止。 | 

建議的旗標是`WBEM_FLAG_RETURN_IMMEDIATELY`和`WBEM_FLAG_FORWARD_ONLY`為了達到最佳效能。

`pCtx`  
[in]一般而言，這個值是`null`。 否則，它是一個指向[IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)可能使用的提供者所提供要求的執行個體的執行個體。

`ppEnum`  
[out]接收列舉值的指標。

`authLevel`  
[in]授權層級。

`impLevel`[in]模擬等級。

`pCurrentNamespace`   
[in]指標[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)物件，代表目前的命名空間。

`strUser`   
[in]使用者名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strPassword`   
[in]密碼。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

`strAuthority`   
[in]使用者的網域名稱。 請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | 使用者沒有權限來檢視指定之類別的執行個體。 |
| `WBEM_E_FAILED` | 0x80041001 | 發生意外的錯誤。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strFilter` 不存在。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI 是可能已停止和重新啟動。 呼叫[ConnectServerWmi](connectserverwmi.md)一次。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前的處理序與 WMI 的遠端程序呼叫 (RPC) 連結失敗。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[iwbemservices:: Createclassenum](https://msdn.microsoft.com/library/aa392097(v=vs.85).aspx)方法。

請注意傳回的列舉值可以有零個元素。

如果函式呼叫失敗，您可以藉由呼叫取得其他錯誤資訊[GetErrorInfo](geterrorinfo.md)函式。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
