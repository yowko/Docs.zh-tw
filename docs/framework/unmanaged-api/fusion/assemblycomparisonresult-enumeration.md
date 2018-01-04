---
title: "AssemblyComparisonResult 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyComparisonResult
api_location: fusion.dll
api_type: COM
f1_keywords: AssemblyComparisonResult
helpviewer_keywords: AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2c38561a804a331df102a600d4b0b0f6312aaa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult 列舉
指出兩個組件識別是否相等由[CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)函式。  
  
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
|`ACR_EquivalentFXUnified`|指出的組件都會被視為相等的通用語言執行階段 (CLR) 版本統一的.NET Framework 2.0 版中的組件版本號碼為基礎。|  
|`ACR_EquivalentPartialFXUnified`|表示 CLR 統一的.NET Framework 2.0 中的組件版本號碼為基礎的組件的部分相符。|  
|`ACR_EquivalentPartialMatch`|表示組件的部分相符。|  
|`ACR_EquivalentPartialUnified`|表示根據舊的版本號碼的統一的組件的部分相符。|  
|`ACR_EquivalentPartialWeakNamed`|指出部分相符的簡單名稱的組件。|  
|`ACR_EquivalentUnified`|指出的組件都會被視為相等 CLR 統一的舊版本的.NET framework 的版本號碼為基礎。|  
|`ACR_EquivalentWeakNamed`|表示兩個簡單名稱的組件，已忽略其版本號碼之間相符。|  
|`ACR_NonEquivalent`|指出兩個組件之間沒有相符項目。|  
|`ACR_NonEquivalentPartialVersion`|指出兩個組件相符除了其版本號碼，只有部分相符。|  
|`ACR_NonEquivalentVersion`|指出兩個組件相符除了其版本號碼，並不相符。|  
|`ACR_Unknown`|指出不相等的原因不明。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [CompareAssemblyIdentity 函式](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [融合列舉](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
