---
title: "爭用 ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: 7
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 931a3f7d5cbc441a3cae2b7359d129dff02afd44
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="contention-etw-events"></a>爭用 ETW 事件
只要爭用執行階段所使用的 <xref:System.Threading.Monitor?displayProperty=fullName> 鎖定或原生鎖定，就會引發爭用事件。 如果某個執行緒等待鎖定，而另一個執行緒擁有該鎖定，則會發生爭用。  
  
 下表顯示引發爭用事件的關鍵字以及事件層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`ContentionKeyword` (0x4000)|告知性 (4)|  
  
 下表顯示事件資訊。  
  
|事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|81|爭用開始。 此事件未包含執行緒等候取得鎖定之前的微調時間量；只有在執行緒等候取得鎖定時才會引發此事件。|  
|`ContentionStop`|81|爭用結束。|  
  
 下表顯示事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|旗標|win:UInt8|0 表示 Managed；1 表示原生。|  
|ClrInstanceID|win:UInt16|CLR 執行個體的唯一識別碼。|  
  
## <a name="see-also"></a>另請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)

