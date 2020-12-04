---
title: 監視鎖定爭用運行時間事件
description: 請參閱收集監視器鎖定爭用特定資訊的 ETW 事件。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "96586638"
---
# <a name="net-runtime-contention-events"></a>.NET 執行時間爭用事件

這些運行時間事件會捕捉有關監視器鎖定爭用的資訊，例如 with `Monitor.Enter` 或 c # lock 關鍵字。 如需如何基於診斷目的使用這些事件的詳細資訊，請參閱[記錄和追蹤 .net 應用程式](../../core/diagnostics/logging-tracing.md)。

## <a name="contentionstart_v1-event"></a>ContentionStart_V1 事件

此事件是在監視器鎖定爭用開始時發出。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|監視器鎖定爭用隨即啟動。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` 針對 managed; `1` 適用于原生。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|

## <a name="contentionstop_v1-event"></a>ContentionStop_V1 事件

此事件是在監視器鎖定爭用結束時發出。

|引發事件的關鍵字|層級|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|告知性 (4)|

 下表顯示事件資訊。

|事件|事件識別碼|引發的時機|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|91|監視器鎖定爭用結束。|

|欄位名稱|資料類型|描述|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|`0` 針對 managed; `1` 適用于原生。|
|`ClrInstanceID`|`win:UInt16`|CoreCLR 實例的唯一識別碼。|
|`DurationNs`|`win:Double`|爭用的持續時間（以毫微秒為單位）。|
