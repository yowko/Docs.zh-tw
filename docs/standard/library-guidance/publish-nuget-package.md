---
title: 發行 NuGet 套件
description: 發行 .NET 程式庫到 NuGet 的最佳做法建議。
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744564"
---
# <a name="publishing-a-nuget-package"></a>發行 NuGet 套件

NuGet 套件發行之後可從套件存放庫取用。 雖然 NuGet.org 是最廣為人知且最常被使用的存放庫，還有許多其他可以發佈 NuGet 套件的地方：

* **[NuGet.org](https://www.nuget.org/)** 是 NuGet 套件的主要線上存放庫。 NuGet.org 上的所有套件都可供大眾使用。 根據預設，Visual Studio 使用 NuGet.org 做為套件來源，而且對許多開發人員而言，NuGet.org 是他們與其互動的唯一套件存放庫。 NuGet.org 是發行穩定套件與您想要從社群取得意見反應之發行前版本套件的最佳位置。

* **[MyGet](https://myget.org/)** 是一個存放庫服務，它支援為開放原始碼專案自訂套件摘要。 MyGet 公用自訂摘要是發行由您的 CI 服務建立之發行前版本套件的理想位置。 MyGet 也提供商業用私人摘要。

* **[本機摘要](/nuget/hosting-packages/local-feeds)** 可讓您將資料夾視為套件存放庫，並讓該資料夾中的 `*.nupkg` 檔案可由 NuGet 存取。 在將 NuGet 套件發行到 NuGet.org 之前進行測試時，本機摘要很實用。

> [!NOTE]
> 一旦套件上傳，NuGet.org 便[不允許刪除套件](/nuget/policies/deleting-packages)。 您可以將套件取消列出，這樣它在 UI 中就不會被大眾看見，但還原時仍能下載 `*.nupkg`。 此外，nuget.org 也不允許重複的套件版本。 若要修正發生錯誤的 NuGet 套件，您必須取消列出不正確的套件、累加版本號碼，然後發行新版本的套件。

✔️要[發佈穩定的套件和發行前版本套件](/nuget/create-packages/publish-a-package)，讓您想要 NuGet.org 的社區意見反應。

✔️考慮將發行前版本的套件發行至持續整合組建中的 MyGet 摘要。

✔️考慮使用本機摘要或 MyGet，在開發環境中測試套件。 檢查套件是否正常運作並將它發行到 NuGet.org。

## <a name="nugetorg-security"></a>NuGet.org 安全性

請務必透過適當機制保護您的 NuGet 帳戶，避免惡意使用者上傳您程式庫的惡意版本。 NuGet.org 提供套件發行時的雙因素驗證與電子郵件通知。 登入 NuGet.org 之後在 [帳戶設定] 頁面上啟用這些功能。

![替代文字](./media/publish-nuget-package/nuget-2fa.png "NuGet 帳戶安全性")

✔️使用 Microsoft 帳戶登入 NuGet。

✔️啟用雙因素驗證以存取 NuGet。

✔️在發佈套件時啟用電子郵件通知。

>[!div class="step-by-step"]
>[上一頁](sourcelink.md)
>[下一頁](versioning.md)
