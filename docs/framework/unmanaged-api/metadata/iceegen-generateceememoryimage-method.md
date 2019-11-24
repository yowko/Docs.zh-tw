---
title: ICeeGen::GenerateCeeMemoryImage 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GenerateCeeMemoryImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GenerateCeeMemoryImage
helpviewer_keywords:
- ICeeGen::GenerateCeeMemoryImage method [.NET Framework metadata]
- GenerateCeeMemoryImage method [.NET Framework metadata]
ms.assetid: b3847495-0ae6-4a72-b496-65ce2424afc6
topic_type:
- apiref
ms.openlocfilehash: a15b9bf5612e18196fc57266d60ec7be3691c682
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436353"
---
# <a name="iceegengenerateceememoryimage-method"></a>ICeeGen::GenerateCeeMemoryImage 方法
Generates an image in memory for the code base.  
  
 This method is obsolete and should not be used.  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GenerateCeeMemoryImage (  
    [out] void    **ppImage  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppImage`  
 [out] A pointer to the generated image.  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICeeGen 介面](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
