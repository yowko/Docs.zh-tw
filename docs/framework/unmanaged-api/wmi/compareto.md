---
title: CompareTo 函式 （Unmanaged API 參考）
description: CompareTo 函式會比較的物件，與其他的 WMI 物件。
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bde25ae7455dd7fe35fe1a0a43bb2a6b560c0e3e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43456353"
---
# <a name="compareto-function"></a>CompareTo 函式
比較物件與另一個 Windows 管理物件。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```
HRESULT CompareTo (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo 
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用此參數。

`ptr`  
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`flags`  
[in]指定物件特性時應考量的比較旗標的位元組合。 請參閱[備註](#remarks)節的詳細資訊。

`pCompareTo`  

[in]比較的物件。 `pcompareTo` 必須是有效[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體，它不能是`null`。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 第二次呼叫`BeginEnumeration`而不需要的介入呼叫進行[ `EndEnumeration` ](endenumeration.md)。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_DIFFERENT` | 0x40003 | 物件不相同。 |
| `WBEM_S_SAME` | 0 | 物件是相同的比較旗標為基礎。 |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto)方法。

可以做為傳遞的旗標`lEnumFlags`中所定義的引數*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。 您可以藉由指定下列旗標的位元組合，指定在比較中涉及的個別特性：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | 忽略來源 （伺服器和其來源的命名空間）。 |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | 忽略所有的限定詞 (包括**金鑰**並**動態**) |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | 忽略屬性的預設值。 這個旗標僅適用於比較的類別。 |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | 忽略限定詞標註。 這個旗標仍限定詞納入考量，但會忽略類型差異，例如傳用規則並覆寫限制。 |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | 忽略大小寫比較字串值。 這適用於字串和限定詞的值。 屬性和限定詞的名稱比較一律會區分大小寫，不論是否設定此旗標的。 |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | 假設正在比較的物件都是相同類別的執行個體的序列。 因此，這個旗標會比較執行個體相關資訊僅供參考。 您可以使用這個旗標來最佳化效能。 如果物件不在相同類別中，則結果為未定義。 |

或者，您也可以指定單一複合旗標，如下所示：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | 請考慮在比較中的所有功能。 |

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
