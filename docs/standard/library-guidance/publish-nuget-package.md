---
title: 發行 NuGet 套件
description: 發佈至 NuGet 的.NET 程式庫的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0602712311411ef3d59825bec8c5e550bc8d8265
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369799"
---
# <a name="publishing-a-nuget-package"></a>發行 NuGet 套件

NuGet 套件發行，且從套件存放庫取用。 雖然 NuGet.org 最廣泛是已知且使用的儲存機制，有許多地方，若要發佈 NuGet 套件：

* **[NuGet.org](https://www.nuget.org/)** 是 NuGet 套件的主要線上存放庫。 公開提供給所有人在 NuGet.org 上的所有封裝都。 根據預設，Visual Studio NuGet.org 與套件來源，並且適用於許多開發人員 NuGet.org 是唯一的套件存放庫會與它們進行互動。 NuGet.org 是穩定的封裝和發行前版本封裝上想要的社群的意見反應所發行的最佳位置。

* **[MyGet](https://myget.org/)** 存放庫服務支援[開放原始碼專案的可用的自訂套件摘要](https://www.myget.org/opensource)。 MyGet 公開自訂摘要是一個理想位置來發佈您的 CI 服務所建立的發行前版本套件。 MyGet 也私用摘要會盡一切商業上的提供。

* A **[本機摘要](/nuget/hosting-packages/local-feeds)** 可讓您將像是套件存放庫的資料夾，並使`*.nupkg`nuget 的可存取資料夾中的檔案。 本機摘要可用於測試前將其發佈至 NuGet.org 的 NuGet 套件。

> [!NOTE]
> NuGet.org[不允許刪除封裝](/nuget/policies/deleting-packages)一旦上傳。 封裝可以是未列出，以便公開在 UI 中看不到但`*.nupkg`仍可以下載 [還原]。 此外，nuget.org 不允許重複的套件版本。 若要更正的錯誤，您必須取消列出不正確的套件的 NuGet 封裝，遞增版本號碼，並發行新版本的封裝。

**✔️ 嗎**[發行穩定的封裝和發行前版本封裝](/nuget/create-packages/publish-a-package)想社群的意見反應到 NuGet.org。

**請考慮 ✔️**發行前版本套件發行至 MyGet 摘要，從持續整合組建。

**請考慮 ✔️**使用本機摘要或 MyGet 開發環境中測試的封裝。 檢查封裝的運作方式，然後將它發行到 NuGet.org。

## <a name="nugetorg-security"></a>NuGet.org 安全性

很重要的不良執行者無法存取您的 NuGet 帳戶，並上傳您的程式庫的惡意版本。 發佈封裝時，NuGet.org 會提供雙因素驗證和電子郵件通知。 登入 NuGet.org 之後啟用這些功能，在**帳戶設定**頁面。

![替代文字](./media/publish-nuget-package/nuget-2fa.png "NuGet 帳戶安全性")

**請勿 ✔️**使用 Microsoft 帳戶登入 NuGet。

**請勿 ✔️**啟用雙因素驗證，以存取 NuGet。

**請勿 ✔️**發佈封裝時，啟用電子郵件通知。

>[!div class="step-by-step"]
[上一頁](./sourcelink.md)
[下一頁](./versioning.md)
