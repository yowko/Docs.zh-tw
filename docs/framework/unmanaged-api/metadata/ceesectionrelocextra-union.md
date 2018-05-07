---
title: CeeSectionRelocExtra 等位
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7634ec801a30aa7ba07954c1df0c3d37ec279eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ceesectionrelocextra-union"></a>CeeSectionRelocExtra 等位
表示所使用的位址位移[ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)介面來重新配置區段。  
  
## <a name="syntax"></a>語法  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`highAdj`|區段上限位址調整。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**包含做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料等位](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
