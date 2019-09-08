---
title: CompareTo 函式（非受控 API 參考）
description: CompareTo 函數會比較物件與另一個 WMI 物件。
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
ms.openlocfilehash: 2ec42dff333422e247a11b4a3a5b9aed9bd316fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798782"
---
# <a name="compareto-function"></a>CompareTo 函式

將物件與另一個 Windows 管理物件比較。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`flags`\
在旗標的位元組合，指定要考慮比較的物件特性。 如需詳細資訊，請參閱[備註](#remarks)一節。

`pCompareTo`\
在要比較的物件。 `pCompareTo`必須是有效的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例;不能是`null`。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生未指定的錯誤。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 第二次呼叫`BeginEnumeration`時，不需要介入的[`EndEnumeration`](endenumeration.md)呼叫。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_DIFFERENT` | 0x40003 | 物件不同。 |
| `WBEM_S_SAME` | 0 | 根據比較旗標，物件是相同的。 |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto)方法的呼叫。

可當做`lEnumFlags`引數傳遞的旗標會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數。 您可以藉由指定下列旗標的位元組合，指定涉及比較的個別特性：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | 2 | 忽略來源（伺服器及其來源的命名空間）。 |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | 1 | 忽略所有限定詞（包括**金鑰**和**動態**） |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | 4 | 忽略屬性的預設值。 此旗標僅適用于類別的比較。 |
| `WBEM_FLAG_IGNORE_FLAVOR` | 0x20 | 略過辨識符號類別。 此旗標仍會將限定詞納入考慮，但會忽略類似傳播規則和覆寫限制的類別區別。 |
| `WBEM_FLAG_IGNORE_CASE` | 0x10 | 比較字串值時，忽略大小寫。 這同時適用于字串和辨識符號值。 不論是否已設定此旗標，屬性和限定詞名稱的比較一律會區分大小寫。 |
| `WBEM_FLAG_IGNORE_CLASS` | 0x8 | 假設要比較的物件是相同類別的實例。 因此，此旗標只會比較與實例相關的資訊。 使用此旗標來優化效能。 如果物件不是相同的類別，則結果會是未定義的。 |

或者，您可以指定單一複合旗標，如下所示：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | 0 | 請考慮比較中的所有功能。 |

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
