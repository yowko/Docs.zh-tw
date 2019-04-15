---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235127"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a>分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE

|   |   |
|---|---|
|詳細資料|在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。 從 .NET Framework 4.6 開始，已修正此問題。|
|建議|此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。|
|範圍|次要|
|版本|4.5.1|
|類型|執行階段|
