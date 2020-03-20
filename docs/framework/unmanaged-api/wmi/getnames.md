---
title: 獲取名稱功能（非託管 API 引用）
description: GetNames 函數檢索物件屬性的名稱。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174949"
---
# <a name="getnames-function"></a>GetNames 函式
擷取物件屬性的子集合或所有名稱。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a>參數

`vFunc`  
[在]此參數未使用。

`ptr`  
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`wszQualifierName`  
[在]指向有效的`LPCWSTR`指標，用於指定作為篩選器一部分運行的限定詞名稱。 有關詳細資訊，請參閱[備註](#remarks)部分。 這個參數可以是 `null`。

`lFlags`  
[在]位欄位的組合。 有關詳細資訊，請參閱[備註](#remarks)部分。

`pQualifierValue`[在]指向初始化到篩選器`VARIANT`值的有效結構的指標。 這個參數可以是 `null`。

`pstrNames`  
[出]包含`SAFEARRAY`屬性名稱的結構。 在輸入時，此參數必須始終是指向`null`的指標。 有關詳細資訊，請參閱[備註](#remarks)部分。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 出現了一個普遍的失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一個或多個參數無效，或指定了不正確的標誌和參數組合。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbem ClassObject 的調用：：getNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)方法。

返回的命名由標誌和參數的組合控制。 例如，函數可以返回所有屬性的名稱，也可以僅返回鍵屬性的名稱。  主篩選器在`lFlags`參數中指定，其他參數因它而異。

中`lFlags`的標誌值是位欄位

可以作為`lEnumFlags`參數傳遞的標誌是在*WbemCli.h*標標頭檔中定義的位欄位，也可以將它們定義為代碼中的常量。  您可以將每個組中的一個標誌與任何其他組的任何標誌合併。 但是，來自同一組的標誌是互斥的。

| 組 1 標誌 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | 返回所有屬性名稱。 `strQualifierName`未`pQualifierVal`使用。 |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | 僅返回具有`strQualifierName`參數指定名稱限定詞的屬性。 如果使用此標誌，則必須指定`strQualifierName`。 |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  僅返回沒有`strQualifierName`參數指定名稱限定詞的屬性。 如果使用此標誌，則必須指定`strQualifierName`。 |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | 僅返回具有`wszQualifierName`參數指定名稱限定詞且值與`pQualifierVal`結構指定的值相同的屬性。 如果使用此標誌，則必須同時指定 a`wszQualifierName`和 。 `pQualifierValue` |

| 組 2 標誌 |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 僅返回定義鍵的屬性的名稱。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 僅返回作為物件引用的屬性名稱。 |

| 組 3 標誌 |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 僅返回屬於最派生類的屬性名稱。 從父類中排除屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 僅返回屬於父類的屬性名稱。 |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 僅返回系統屬性的名稱。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 僅返回非系統屬性的名稱。 |

如果函數返回`SAFEARRAY``WBEM_S_NO_ERROR`，則始終分配新函數，並且`pstrNames`始終設置為指向它。 如果沒有與指定篩選器匹配的屬性，則返回的陣列可以具有 0 個元素。 如果函數返回的值，`WBM_S_NO_ERROR`則不返回新`SAFEARRAY`結構。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
