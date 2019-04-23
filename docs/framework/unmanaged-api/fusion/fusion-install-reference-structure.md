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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110361"
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE 結構
表示應用程式對應用程式已安裝在全域組件快取中的組件的參考。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`cbSize`|結構，以位元組為單位的大小。|  
|`dwFlags`|保留供未來擴充。 此值必須是 0 （零）。|  
|`guidScheme`|加入參考的實體。 這個欄位可以有下列值之一：<br /><br /> -FUSION_REFCOUNT_MSI_GUID:使用 Microsoft Windows Installer 所安裝的應用程式所參考的組件。 `szIdentifier`欄位設定為`MSI`，而`szNonCanonicalData` 欄位設為`Windows Installer`。 此配置會使用 Windows 並排顯示組件。<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID:會出現在應用程式所參考的組件**新增/移除程式**介面。 `szIdentifier`欄位提供與將應用程式註冊權杖**新增/移除程式**介面。<br />-FUSION_REFCOUNT_FILEPATH_GUID:組件參考的應用程式，由檔案系統中的檔案。 `szIdentifier`欄位會提供這個檔案的路徑。<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID:應用程式只能由不透明的字串表示所參考的組件。 `szIdentifier`欄位提供不透明的字串。 當您移除此值時，全域組件快取不會檢查存在的不透明的參考。<br />-FUSION_REFCOUNT_OSINSTALL_GUID:這個值已保留。|  
|`szIdentifier`|唯一的字串，可識別在全域組件快取中安裝組件的應用程式。 其值的值取決於`guidScheme`欄位。|  
|`szNonCanonicalData`|只要加入參考的實體會辨識字串。 全域組件快取會儲存這個字串中，但不會使用它。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [融合結構](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [全域組件快取](../../../../docs/framework/app-domains/gac.md)
