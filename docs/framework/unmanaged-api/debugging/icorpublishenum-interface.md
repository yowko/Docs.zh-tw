---
title: ICorPublishEnum 介面
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: 7d083655326333f18ee98f8e84fff2ed182dde6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103455"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum 介面
做為列舉值的抽象基底介面，這些列舉值是用來發行進程和應用程式域的相關資訊。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|建立這個 `ICorPublishEnum` 物件的複本。|  
|[GetCount 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|取得列舉中的專案數。|  
|[Reset 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|將的資料指標移至列舉的開頭。|  
|[Skip 方法](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|在列舉中，將資料指標向後移動指定的專案數。|  
  
## <a name="remarks"></a>備註  
 下列枚舉器衍生自 `ICorPublishEnum`：  
  
- [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorPub .idl，CorPub。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [CorpubPublish Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
