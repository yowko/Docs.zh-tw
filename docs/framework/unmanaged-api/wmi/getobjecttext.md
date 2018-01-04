---
title: "GetObjectText 函式 （Unmanaged API 參考）"
description: "GetObjectText 函式會傳回物件的文字呈現以 MOF 語法。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b47dc73bb9da71b0c8593aa5758179327d7572d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getobjecttext-function"></a>GetObjectText 函式
傳回物件的文字呈現在受管理物件格式 (MOF) 語法。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`lFlags`  
[in]通常是 0。 如果`WBEM_FLAG_NO_FLAVORS`（或 0x1） 指定，限定詞會包含不含傳播或類別資訊。

`pstrObjectText`   
[out]指標`null`項目。 傳回時，新配置`BSTR`，其中包含物件的 MOF 語法呈現。  

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx)方法。

傳回的 MOF 文字不包含所有物件的相關資訊，但若要能夠重新建立原始物件的 MOF 編譯器足夠資訊。 比方說，沒有傳播的限定詞或父類別的內容會包含。

下列演算法來重新建構方法的參數的文字：

1. 參數會以其識別項值順序 resequenced。
1. 參數指定為`[in]`和`[out]`會結合成單一參數。
 
`pstrObjectText`必須是指向`null`時呼叫的函式; 它必須指向在方法呼叫之前，因為無效的指標將不會重新配置的字串。

## <a name="requirements"></a>需求  
**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
