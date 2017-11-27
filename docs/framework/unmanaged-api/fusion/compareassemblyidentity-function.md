---
title: "CompareAssemblyIdentity 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: CompareAssemblyIdentity
helpviewer_keywords: CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d9d7b4934d4295ee799fb13d3d749e6b977e644
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity 函式
比較兩個組件識別，以判斷它們是否相等。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a>參數  
 `pwzAssemblyIdentity1`  
 [in]文字中比較的第一個組件識別。  
  
 `fUnified1`  
 [in]布林旗標，指出使用者指定的統一`pwzAssemblyIdentity1`。  
  
 `pwzAssemblyIdentity2`  
 [in]文字中比較的第二個組件識別。  
  
 `fUnified2`  
 [in]布林旗標，指出使用者指定的統一`pwzAssemblyIdentity2`。  
  
 `pfEquivalent`  
 [out]布林值旗標，指出兩個組件是否相等。  
  
 `pResult`  
 [out][AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)列舉，其中包含比較的詳細的資訊。  
  
## <a name="return-value"></a>傳回值  
 `pfEquivalent`傳回布林值，指出兩個組件是否相等。 `pResult`傳回的其中一個`AssemblyComparisonResult`值，來提供深度的值的詳細的原因`pfEquivalent`。  
  
## <a name="remarks"></a>備註  
 `CompareAssemblyIdentity`檢查是否`pwzAssemblyIdentity1`和`pwzAssemblyIdentity2`相等。 `pfEquivalent`設定為`true`在一或多個下列條件：  
  
-   兩個組件識別是相等的。 強式名稱組件，相等的條件組件名稱、 版本、 公開金鑰語彙基元和文化特性相同。 簡單名稱的組件為相等的條件相符的組件名稱和文化特性。  
  
-   這兩個組件識別是指.NET Framework 執行的組件。 此條件傳回`true`即使組件版本號碼不相符。  
  
-   兩個組件不是 managed 組件，但`fUnified1`或`fUnified2`設`true`。  
  
 `fUnified`旗標指出強式名稱組件的版本號碼的所有版本號碼會都視為等於強式名稱組件。 例如，如果的值`pwzAssemblyIndentity1`是"MyAssembly，版本 = 3.0.0.0，culture = neutral，publicKeyToken =..."，和值`fUnified1`是`true`，這表示應該從版本 0.0.0.0 3.0.0.0 開始 MyAssembly 的所有版本視為對等項目。 在這種情況下，如果`pwzAssemblyIndentity2`指的是相同的組件`pwzAssemblyIndentity1`，不同之處在於它有較低的版本號碼，`pfEquivalent`設`true`。 如果`pwzAssemblyIdentity2`較高的版本號碼，是指`pfEquivalent`設`true`才值`fUnified2`是`true`。  
  
 `pResult`參數包含兩個組件為何被視為相等或不相等的特定資訊。 如需詳細資訊，請參閱[AssemblyComparisonResult 列舉](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [AssemblyComparisonResult 列舉](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
