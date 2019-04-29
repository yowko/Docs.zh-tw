---
title: 爭用 ETW 事件-.NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95f56a6c8b51c58ed36d5d0de428bf57b728009c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723936"
---
# <a name="contention-etw-events"></a>爭用 ETW 事件

只要爭用執行階段所使用的 <xref:System.Threading.Monitor?displayProperty=nameWithType> 鎖定或原生鎖定，就會引發爭用事件。 如果某個執行緒等待鎖定，而另一個執行緒擁有該鎖定，則會發生爭用。

下表顯示引發爭用事件的關鍵字以及事件層級。 如需詳細資訊，請參閱 < [CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|告知性 (4)|

下表顯示事件資訊：

|Event - 事件|事件 ID|引發的時機|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|爭用開始。 此事件未包含執行緒等候取得鎖定之前的微調時間量；只有在執行緒等候取得鎖定時才會引發此事件。|
|`ContentionStop`|91|爭用結束。|

下表顯示事件資料：

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|旗標|win:UInt8|0 表示 Managed；1 表示原生。|
|ClrInstanceID|win:UInt16|CLR 執行個體的唯一識別碼。|

## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](clr-etw-events.md)
