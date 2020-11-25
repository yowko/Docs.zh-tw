---
title: AssemblyComparisonResult 列舉
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: cde25a9507006c89ef6490c13ae82033f04c2931
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731029"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult 列舉

指出兩個元件身分識別的相等（由 [CompareAssemblyIdentity](compareassemblyidentity-function.md) 函式所決定）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>成員  
  
|成員名稱|描述|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|表示比較中的所有元件欄位都相符。|  
|`ACR_EquivalentFXUnified`|表示根據 common language runtime 版本 (CLR) .NET Framework 2.0 版中的元件版本號碼統一，來將元件視為相等。|  
|`ACR_EquivalentPartialFXUnified`|根據 .NET Framework 2.0 中元件版本號碼的 CLR 統一，表示元件的部分相符。|  
|`ACR_EquivalentPartialMatch`|表示元件的部分相符。|  
|`ACR_EquivalentPartialUnified`|表示以舊版統一的版本號碼為基礎的元件部分相符。|  
|`ACR_EquivalentPartialWeakNamed`|表示單純命名元件的部分相符。|  
|`ACR_EquivalentUnified`|表示根據舊版 .NET Framework 中的版本號碼 CLR 統一，將元件視為相同。|  
|`ACR_EquivalentWeakNamed`|表示兩個簡單命名的元件（其版本號碼已被忽略）之間的相符項。|  
|`ACR_NonEquivalent`|指出兩個元件之間沒有相符的結果。|  
|`ACR_NonEquivalentPartialVersion`|指出兩個元件的版本號碼除外，但只有部分相符。|  
|`ACR_NonEquivalentVersion`|指出兩個元件的版本號碼除外，但不符。|  
|`ACR_Unknown`|指出不知道非等位的原因。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CompareAssemblyIdentity 函式](compareassemblyidentity-function.md)
- [融合列舉](fusion-enumerations.md)
