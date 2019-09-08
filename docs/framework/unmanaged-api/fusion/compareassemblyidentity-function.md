---
title: CompareAssemblyIdentity 函式
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52d3af38bd09ce5864c25d27e148dbd7f4639b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795453"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity 函式
比較兩個元件識別，以判斷它們是否相等。  
  
## <a name="syntax"></a>語法  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a>參數  
 `pwzAssemblyIdentity1`  
 在比較中第一個元件的文字識別。  
  
 `fUnified1`  
 在布林值旗標，表示的使用者指定的`pwzAssemblyIdentity1`統一。  
  
 `pwzAssemblyIdentity2`  
 在比較中第二個元件的文字識別。  
  
 `fUnified2`  
 在布林值旗標，表示的使用者指定的`pwzAssemblyIdentity2`統一。  
  
 `pfEquivalent`  
 脫銷指出兩個元件是否相等的布林值旗標。  
  
 `pResult`  
 脫銷包含比較之詳細資訊的[AssemblyComparisonResult](assemblycomparisonresult-enumeration.md)列舉。  
  
## <a name="return-value"></a>傳回值  
 `pfEquivalent`傳回布林值，指出兩個元件是否相等。 `pResult`傳回其中一個`AssemblyComparisonResult`值，以提供更詳細的`pfEquivalent`值原因。  
  
## <a name="remarks"></a>備註  
 `CompareAssemblyIdentity``pwzAssemblyIdentity1`檢查和`pwzAssemblyIdentity2`是否相等。 `pfEquivalent`在下列一個`true`或多個情況下，會設為：  
  
- 這兩個元件身分識別是相等的。 若為強式名稱元件，則對等需要元件名稱、版本、公開金鑰標記和文化特性都相同。 對於簡單命名的元件而言，對等的必須符合元件名稱和文化特性。  
  
- 這兩個元件識別都會參考在 .NET Framework 上執行的元件。 `true`即使元件版本號碼不相符，這個條件也會傳回。  
  
- 這兩個元件不是 managed 元件， `fUnified1`而`fUnified2`是或已`true`設定為。  
  
 `fUnified`旗標指出，最高至強式名稱元件版本號碼的所有版本號碼，都視為與強式名稱元件相等。 例如，如果的值`pwzAssemblyIndentity1`為 "MyAssembly，version = 3.0.0.0，culture = 中性，publicKeyToken = ..."，且的`fUnified1`值為`true`，則表示從0.0.0.0 到3.0.0.0 的所有 MyAssembly 版本都應該是視為對等。 在這種情況下， `pwzAssemblyIndentity2`如果參考與相同的`pwzAssemblyIndentity1`元件，但其版本號碼較低， `pfEquivalent`則會設定為`true`。 如果`pwzAssemblyIdentity2`參考較高的版本號碼， `pfEquivalent`只有在的`true`值`fUnified2`為時`true`，才會設定為。  
  
 `pResult`參數包含為何將兩個元件視為相等或不相等的特定資訊。 如需詳細資訊，請參閱[AssemblyComparisonResult 列舉](assemblycomparisonresult-enumeration.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](fusion-global-static-functions.md)
- [AssemblyComparisonResult 列舉](assemblycomparisonresult-enumeration.md)
