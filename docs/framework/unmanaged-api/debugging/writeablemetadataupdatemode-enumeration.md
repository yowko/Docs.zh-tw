---
title: "WriteableMetadataUpdateMode 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: WriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b32eca0bec61e6c7b6fcf83bb05650c30c2f9f16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode 列舉
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 提供值來指定偵錯工具是否可以看見對中繼資料的記憶體中更新。  
  
## <a name="syntax"></a>語法  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>成員  
  
|成員名稱|描述|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|在對中繼資料可見性進行記憶體中更新時，維護與舊版 .NET Framework 的相容性。 如需詳細資訊，請參閱「備註」一節。|  
|`AlwaysShowUpdates`|針對可讓偵錯工具看見的中繼資料進行記憶體中更新。|  
  
## <a name="remarks"></a>備註  
 成員`WriteableMetadataUpdateMode`列舉可以傳遞至[SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)方法，以控制是否在記憶體中更新目標處理序中的中繼資料會顯示偵錯工具。  
  
 `LegacyCompatPolicy` 選項會強制執行與 .NET Framework 4.5.2 之前版本中相同的行為。 這通常就表示看不到更新的中繼資料。 不過，呼叫數個偵錯方法會將偵錯工具隱含強制轉型為可看見更新。 例如，如果偵錯工具傳遞[icordebugilframe:: Getlocalvariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)中找不到方法的原始中繼資料，所有中繼資料的模組會更新為符合目前狀態的快照集之變數的索引程序。 換句話說，若使用 `LegacyCompatPolicy` 選項，偵錯工具可能看不到、看到部分或所有可用的中繼資料更新，取決於其使用 Unmanaged 偵錯 API 其他部分的方式。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [SetWriteableMetadataUpdateMode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
