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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178297"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult 列舉
指示由[比較裝配標識](compareassemblyidentity-function.md)函數確定的兩個程式集標識的等效性。  
  
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
|`ACR_EquivalentFullMatch`|指示比較中的所有程式集欄位匹配。|  
|`ACR_EquivalentFXUnified`|指示基於 .NET Framework 版本 2.0 中程式集版本 2.0 中程式集版本編號的通用語言執行階段版本 （CLR） 統一，將程式集視為等效。|  
|`ACR_EquivalentPartialFXUnified`|指示基於 .NET 框架 2.0 中程式集版本號的 CLR 統一的程式集的部分匹配。|  
|`ACR_EquivalentPartialMatch`|指示程式集的部分匹配。|  
|`ACR_EquivalentPartialUnified`|指示基於版本號的舊統一的程式集的部分匹配。|  
|`ACR_EquivalentPartialWeakNamed`|指示簡單命名程式集的部分匹配。|  
|`ACR_EquivalentUnified`|指示基於 .NET Framework 舊版本中版本號的 CLR 統一，將程式集視為等效。|  
|`ACR_EquivalentWeakNamed`|指示兩個簡單命名的程式集之間的匹配，其版本號被忽略。|  
|`ACR_NonEquivalent`|指示兩個程式集之間沒有匹配。|  
|`ACR_NonEquivalentPartialVersion`|指示兩個程式集匹配，但版本號除外，只有部分匹配。|  
|`ACR_NonEquivalentVersion`|指示兩個程式集匹配，但版本號不匹配。|  
|`ACR_Unknown`|指示非等價的原因尚不清楚。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** 融合.h  
  
 **庫：** 作為資源包含在 MsCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CompareAssemblyIdentity 函式](compareassemblyidentity-function.md)
- [融合列舉](fusion-enumerations.md)
