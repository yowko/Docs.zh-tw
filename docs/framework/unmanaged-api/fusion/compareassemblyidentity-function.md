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
ms.openlocfilehash: da32ce6a40378a6f88cf71bd7707be2079d71068
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717587"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity 函式

比較兩個元件身分識別，以判斷它們是否相等。  
  
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
 在指出使用者指定之統一的布林值旗標 `pwzAssemblyIdentity1` 。  
  
 `pwzAssemblyIdentity2`  
 在比較中第二個元件的文字識別。  
  
 `fUnified2`  
 在指出使用者指定之統一的布林值旗標 `pwzAssemblyIdentity2` 。  
  
 `pfEquivalent`  
 擴展指出兩個元件是否相等的布林旗標。  
  
 `pResult`  
 擴展包含比較之詳細資訊的 [AssemblyComparisonResult](assemblycomparisonresult-enumeration.md) 列舉。  
  
## <a name="return-value"></a>傳回值  

 `pfEquivalent` 傳回布林值，指出兩個元件是否相等。 `pResult` 傳回其中一個 `AssemblyComparisonResult` 值，以提供更詳細的值原因 `pfEquivalent` 。  
  
## <a name="remarks"></a>備註  

 `CompareAssemblyIdentity` 檢查 `pwzAssemblyIdentity1` 和是否 `pwzAssemblyIdentity2` 相等。 `pfEquivalent``true`在下列一或多個情況下，會設定為：  
  
- 這兩個元件身分識別是相等的。 針對強式名稱元件，相等要求元件名稱、版本、公開金鑰 token 和文化特性必須相同。 針對簡單命名的元件，等的需要符合元件名稱和文化特性。  
  
- 這兩個元件身分識別都會參考在 .NET Framework 上執行的元件。 `true`即使元件版本號碼不相符，也會傳回這個條件。  
  
- 這兩個元件並非 managed 元件，而 `fUnified1` 是 `fUnified2` 設定為 `true` 。  
  
 `fUnified`旗標會指出強式名稱元件的版本號碼最多會視為相當於強式名稱元件。 例如，如果的值 `pwzAssemblyIndentity1` 為 "MyAssembly，version = 3.0.0.0，culture = 中性，publicKeyToken = ..."，而的值 `fUnified1` 為 `true` ，則這表示從0.0.0.0 到3.0.0.0 的所有 MyAssembly 版本都應視為相等。 在這種情況下，如果 `pwzAssemblyIndentity2` 參考相同的元件 `pwzAssemblyIndentity1` ，但它的版本號碼較低， `pfEquivalent` 則會設定為 `true` 。 如果 `pwzAssemblyIdentity2` 參考較高的版本號碼， `pfEquivalent` 則 `true` 只有當的值為時，才會設定為 `fUnified2` `true` 。  
  
 `pResult`參數包含為何將兩個元件視為相等或不相等的特定資訊。 如需詳細資訊，請參閱 [AssemblyComparisonResult 列舉](assemblycomparisonresult-enumeration.md)。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合全域靜態函式](fusion-global-static-functions.md)
- [AssemblyComparisonResult 列舉](assemblycomparisonresult-enumeration.md)
