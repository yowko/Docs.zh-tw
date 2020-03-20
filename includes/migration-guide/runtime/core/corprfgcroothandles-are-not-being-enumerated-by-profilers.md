---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858521"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE

|   |   |
|---|---|
|詳細資料|在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。 從 .NET Framework 4.6 開始，已修正此問題。|
|建議|此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。|
|影響範圍|Minor|
|版本|4.5.1|
|類型|執行階段|
