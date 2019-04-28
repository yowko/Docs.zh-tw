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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b8ecc996e14263510e2d0a658cec020696c263
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914495"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult 列舉
表示之兩個組件身分識別，對等，由[CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`ACR_EquivalentFullMatch`|表示所有組件欄位比對中。|  
|`ACR_EquivalentFXUnified`|指出，組件都視為對等的通用語言執行階段 (CLR) 版本統一的.NET Framework 2.0 版中的組件版本號碼為基礎。|  
|`ACR_EquivalentPartialFXUnified`|表示根據.NET Framework 2.0 中的組件版本號碼將 CLR 統一的組件的部分相符。|  
|`ACR_EquivalentPartialMatch`|指出部分相符的組件。|  
|`ACR_EquivalentPartialUnified`|表示根據舊版的版本號碼的統一的組件的部分相符。|  
|`ACR_EquivalentPartialWeakNamed`|指出部分相符的簡單名稱的組件。|  
|`ACR_EquivalentUnified`|指出，組件視為相同的基礎 CLR 版本對應轉換的舊版本的.NET Framework 的版本號碼。|  
|`ACR_EquivalentWeakNamed`|表示忽略其版本號碼的兩個簡單名稱組件之間相符。|  
|`ACR_NonEquivalent`|表示發生在兩個組件之間沒有相符項目。|  
|`ACR_NonEquivalentPartialVersion`|指出兩個組件相符除了其版本號碼，只有部分相符。|  
|`ACR_NonEquivalentVersion`|指出兩個組件相符除了其版本號碼，不相符。|  
|`ACR_Unknown`|指出不相等的原因不明。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **LIBRARY:** 包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CompareAssemblyIdentity 函式](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [融合列舉](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
