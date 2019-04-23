---
ms.openlocfilehash: 0358450024607a985f38564ec9743ba964949e8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803442"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce 在 4.0 為目標的應用程式上支援 SHA-256

|   |   |
|---|---|
|詳細資料|先前，具有使用 SHA-256 簽署之憑證的 ClickOnce 應用程式，需要有 .NET Framework 4.5 或更新版本存在，即使應用程式是以 4.0 為目標。 現在，即使使用 SHA-256 簽署，以 .NET Framework 4.0 為目標的 ClickOnce 應用程式也可以在 .NET Framework 4.0 上執行。|
|建議|這項變更移除了該相依性，並允許使用 SHA-256 憑證來簽署以 .NET Framework 4 和更早版本為目標的 ClickOnce 應用程式。|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|
