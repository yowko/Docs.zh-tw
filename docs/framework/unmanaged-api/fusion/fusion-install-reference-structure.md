---
title: "FUSION_INSTALL_REFERENCE 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FUSION_INSTALL_REFERENCE
api_location: fusion.dll
api_type: COM
f1_keywords: FUSION_INSTALL_REFERENCE
helpviewer_keywords: FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36321606fe208233fb6114fe9568b655f0e1b400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE 結構
表示應用程式建立應用程式已安裝在全域組件快取中的組件的參考。  
  
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
|`guidScheme`|加入參考的實體。 這個欄位可以有下列值之一：<br /><br /> -FUSION_REFCOUNT_MSI_GUID： 使用 Microsoft Windows Installer 已安裝的應用程式所參考的組件。 `szIdentifier`欄位設定為`MSI`，而`szNonCanonicalData`欄位設定為`Windows Installer`。 這種配置適用於 Windows 的並存組件。<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID： 會出現在應用程式參考的組件**新增/移除程式**介面。 `szIdentifier`欄位提供的語彙基元註冊此應用程式與**新增/移除程式**介面。<br />-FUSION_REFCOUNT_FILEPATH_GUID： 應用程式由檔案系統中的檔案所參考的組件。 `szIdentifier`欄位會提供這個檔案的路徑。<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID： 應用程式只能由不透明的字串表示所參考的組件。 `szIdentifier`欄位提供的不透明的字串。 全域組件快取不會檢查不透明參考存在，當您移除此值。<br />-FUSION_REFCOUNT_OSINSTALL_GUID： 保留此值。|  
|`szIdentifier`|識別在全域組件快取中安裝組件的應用程式的唯一字串。 它的值而定的值`guidScheme`欄位。|  
|`szNonCanonicalData`|字串，只會將參考加入的實體了解。 全域組件快取會儲存這個字串，但不是會使用它。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [融合結構](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [全域組件快取](../../../../docs/framework/app-domains/gac.md)
