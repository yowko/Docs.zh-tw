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
ms.openlocfilehash: 3d3fd88a2c1ac90f823b23d8d2bcb5b177a625c3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109003"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult 列舉
表示由[CompareAssemblyIdentity](compareassemblyidentity-function.md)函式決定的兩個元件識別是否相等。  
  
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
  
## <a name="members"></a>Members  
  
|成員名稱|描述|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|表示比較中的所有元件欄位都相符。|  
|`ACR_EquivalentFXUnified`|指出元件會根據 .NET Framework 版本2.0 中元件版本號碼的通用語言執行時間版本（CLR）統一而視為對等。|  
|`ACR_EquivalentPartialFXUnified`|根據 .NET Framework 2.0 中元件版本號碼的 CLR 統一，指出元件的部分相符。|  
|`ACR_EquivalentPartialMatch`|表示元件的部分相符。|  
|`ACR_EquivalentPartialUnified`|根據版本號碼的舊版統一，指出元件的部分相符。|  
|`ACR_EquivalentPartialWeakNamed`|表示只有命名元件的部分相符。|  
|`ACR_EquivalentUnified`|指出元件會根據舊版 .NET Framework 中的 CLR 統一版本號碼，視為對等。|  
|`ACR_EquivalentWeakNamed`|表示兩個單純命名的元件（其版本號碼已略過）之間的相符項。|  
|`ACR_NonEquivalent`|表示兩個元件之間沒有相符的。|  
|`ACR_NonEquivalentPartialVersion`|指出兩個元件是否相符，但只符合部分的版本號碼。|  
|`ACR_NonEquivalentVersion`|表示兩個元件相符，但不符合其版本號碼。|  
|`ACR_Unknown`|指出非等位的原因不是已知的。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [CompareAssemblyIdentity 函式](compareassemblyidentity-function.md)
- [融合列舉](fusion-enumerations.md)
