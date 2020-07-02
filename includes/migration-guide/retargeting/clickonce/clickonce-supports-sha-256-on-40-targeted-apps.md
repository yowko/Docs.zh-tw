---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615619"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce 在 4.0 為目標的應用程式上支援 SHA-256

#### <a name="details"></a>詳細資料

先前，具有使用 SHA-256 簽署之憑證的 ClickOnce 應用程式，需要有 .NET Framework 4.5 或更新版本存在，即使應用程式是以 4.0 為目標。 現在，即使使用 SHA-256 簽署，以 .NET Framework 4.0 為目標的 ClickOnce 應用程式也可以在 .NET Framework 4.0 上執行。

#### <a name="suggestion"></a>建議

這項變更移除了該相依性，並允許使用 SHA-256 憑證來簽署以 .NET Framework 4 和更早版本為目標的 ClickOnce 應用程式。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.6         |
| 類型    | 正在重定目標 |
