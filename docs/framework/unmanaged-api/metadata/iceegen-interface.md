---
title: ICeeGen 介面
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fb081c48abf899b44da1c1351efa3f6036f1c8d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176120"
---
# <a name="iceegen-interface"></a>ICeeGen 介面
提供動態程式碼編譯的方法。  
  
 這個介面已經過時，不應使用。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AddSectionReloc 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|已過時。 將程式碼基底.reloc 指令。|  
|[AllocateMethodBuffer 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|已過時。 建立方法中，指定大小的緩衝區，並取得方法的相對虛擬位址。|  
|[ComputePointer 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|已過時。 判斷指定的程式碼區段的緩衝區。|  
|[EmitString 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|已過時。 程式碼基底到發出指定的字串。|  
|[GenerateCeeFile 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|已過時。 產生程式碼基底檔案，其中包含目前載入到這個程式碼基底`ICeeGen`。|  
|[GenerateCeeMemoryImage 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|已過時。 在記憶體中的程式碼基底，會產生映像。|  
|[GetIlSection 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|已過時。 取得指定的控制代碼所參考的基底中繼語言程式碼區段。|  
|[GetIMapTokenIface 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|已過時。 取得指定語彙基元所參考的介面。|  
|[GetMethodBuffer 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|已過時。 取得方法的適當大小的緩衝區，在指定的相對虛擬位址。|  
|[GetSectionBlock 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|已過時。 取得區段的區塊程式碼基底。|  
|[GetSectionCreate 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|已過時。 產生並取得使用指定的名稱和旗標值的程式碼區段。|  
|[GetSectionDataLen 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|已過時。 取得指定的區段長度。|  
|[GetString 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|已過時。 取得儲存在指定的相對虛擬位址的字串。|  
|[GetStringSection 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|已過時。 取得指定的控制代碼所參考的程式碼區段的字串表示。|  
|[TruncateSection 方法](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|已過時。 將指定的程式碼區段捨去指定的長度。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
