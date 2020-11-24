---
title: FUSION_INSTALL_REFERENCE 結構
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
ms.openlocfilehash: d5ff08e62b94d7f164b103ae0535bb62e4e60aea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688805"
---
# <a name="fusion_install_reference-structure"></a>FUSION_INSTALL_REFERENCE 結構

表示應用程式對應用程式已安裝在全域組件快取中之元件的參考。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`cbSize`|結構的大小（以位元組為單位）。|  
|`dwFlags`|保留供未來擴充性之用。 這個值必須是 0 (零) 。|  
|`guidScheme`|加入參考的實體。 這個欄位可以具有下列其中一個值：<br /><br /> -FUSION_REFCOUNT_MSI_GUID：使用 Microsoft Windows Installer 所安裝的應用程式所參考的元件。 `szIdentifier`欄位設定為 `MSI` ，而且 `szNonCanonicalData` 欄位設定為 `Windows Installer` 。 此配置用於 Windows 並存元件。<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID：應用程式會參考出現在 [ **新增/移除程式** ] 介面中的元件。 `szIdentifier`欄位提供使用 [**新增/移除程式**] 介面註冊應用程式的權杖。<br />-FUSION_REFCOUNT_FILEPATH_GUID：元件是由檔案系統中的檔案所代表的應用程式所參考。 `szIdentifier`欄位提供此檔案的路徑。<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID：元件是由只由不透明字串所表示的應用程式所參考。 `szIdentifier`欄位提供此不透明字串。 當您移除這個值時，全域組件快取不會檢查是否存在不透明的參考。<br />-FUSION_REFCOUNT_OSINSTALL_GUID：此值為 reserved。|  
|`szIdentifier`|唯一的字串，可識別在全域組件快取中安裝元件的應用程式。 它的值會根據欄位的值而定 `guidScheme` 。|  
|`szNonCanonicalData`|只有加入參考的實體才會瞭解的字串。 全域組件快取會儲存這個字串，但不會使用它。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合結構](fusion-structures.md)
- [全域組件快取](../../app-domains/gac.md)
