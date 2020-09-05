---
ms.openlocfilehash: 26539011f0650c7a3bac9e1c41847561905fff58
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496714"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>.NET Framework 1.1 和 2.0 的受控瀏覽器裝載控制項已封鎖

#### <a name="details"></a>詳細資料

Internet Explorer 中已封鎖裝載這些控制項。

#### <a name="suggestion"></a>建議

Internet Explorer 將無法啟動使用 Managed 瀏覽器裝載控制項的應用程式。 可還原先前行為的方式包括：在 x86 系統和 x64 系統的 32 位元處理序上，將登錄子機碼 <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> 的 EnableIEHosting 值設為 <code>1</code>，在 x64 系統的 64 位元處理序上，將登錄子機碼 <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> 的 <code>EnableIEHosting</code> 值設為 <code>1</code>。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
