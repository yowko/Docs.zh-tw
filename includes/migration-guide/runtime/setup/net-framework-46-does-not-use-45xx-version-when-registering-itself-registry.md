---
ms.openlocfilehash: a9011514c7c4393ec44de2c7fae88768cdccf435
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497604"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 在登錄中註冊本身時不使用 4.5.x.x 版本

#### <a name="details"></a>詳細資料

如預期一般，.NET Framework 4.6 在登錄中的版本機碼設定 (位於 <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) 開頭為 '4.6'，而不是 '4.5'。 相依於這些登錄機碼以得知電腦上所安裝之 .NET Framework 版本的應用程式應該加以更新，才能了解 4.6 是新的可能版本，以及其與先前的 4.5.x 版相容。

#### <a name="suggestion"></a>建議

藉由尋找 4.5 登錄機碼來更新 .NET Framework 4.5 安裝的應用程式探查，使其也接受 4.6。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.6|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
