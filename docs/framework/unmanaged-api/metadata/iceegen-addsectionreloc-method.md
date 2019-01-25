---
title: ICeeGen::AddSectionReloc 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8e270f45300bd5f8c2e6cd87f9b84f31ec42320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722188"
---
# <a name="iceegenaddsectionreloc-method"></a>ICeeGen::AddSectionReloc 方法
將程式碼基底.reloc 指令。  
  
 這個方法已經過時，不應使用。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `section`  
 [in]要加入.reloc 指令的記憶體中程式碼區段。  
  
 `offset`  
 [in]此區段的位移。  
  
 `relativeTo`  
 [in]這一節`offset`參考。  
  
 `relocType`  
 [in]其中一個[CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)值，表示將.reloc 指令的類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
