---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619958"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>分析工具不會列舉 COR_PRF_GC_ROOT_HANDLE

#### <a name="details"></a>詳細資料

在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 會錯誤地永不傳回 <code>COR_PRF_GC_ROOT_HANDLE</code> (而是傳回為 <code>COR_PRF_GC_ROOT_OTHER</code>)。 從 .NET Framework 4.6 開始，已修正此問題。

#### <a name="suggestion"></a>建議

此問題在 .NET Framework 4.6 中已修正，因此可藉由升級至該版 .NET Framework 來解決。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5.1|
|類型|執行階段|
