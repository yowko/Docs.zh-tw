---
title: WriteableMetadataUpdateMode 列舉
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
ms.openlocfilehash: 1553e18da10844da28bbaf84ba76bc5c34ca49b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725296"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>WriteableMetadataUpdateMode 列舉

[.NET Framework 4.5.2 與更新版本提供支援]  
  
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
|`LegacyCompatPolicy`|在對中繼資料可見性進行記憶體中更新時，維護與舊版 .NET Framework 的相容性。 如需詳細資訊，請參閱＜備註＞一節。|  
|`AlwaysShowUpdates`|針對可讓偵錯工具看見的中繼資料進行記憶體中更新。|  
  
## <a name="remarks"></a>備註  

 列舉的成員 `WriteableMetadataUpdateMode` 可以傳遞至 [SetWriteableMetadataUpdateMode](icordebugprocess7-setwriteablemetadataupdatemode-method.md) 方法，以控制偵錯工具是否可以看到目標進程中中繼資料的記憶體中更新。  
  
 `LegacyCompatPolicy` 選項會強制執行與 .NET Framework 4.5.2 之前版本中相同的行為。 這通常就表示看不到更新的中繼資料。 不過，呼叫數個偵錯方法會將偵錯工具隱含強制轉型為可看見更新。 例如，如果偵錯工具傳遞 [ICorDebugILFrame：： GetLocalVariable](icordebugilframe-getlocalvariable-method.md) 在方法的原始中繼資料中找不到的變數索引，則模組的所有中繼資料都會更新至符合進程目前狀態的快照集。 換句話說，若使用 `LegacyCompatPolicy` 選項，偵錯工具可能看不到、看到部分或所有可用的中繼資料更新，取決於其使用 Unmanaged 偵錯 API 其他部分的方式。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode 方法](icordebugprocess7-setwriteablemetadataupdatemode-method.md)
