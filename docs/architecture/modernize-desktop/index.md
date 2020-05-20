---
title: 使用 .NET Core 3.1 在 Windows 10 上現代化桌面應用程式
description: 瞭解如何使用 .NET Core 3.1 現代化現有的桌面應用程式
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423233"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a>使用 .NET Core 3.1 在 Windows 10 上現代化桌面應用程式

![顯示現代化桌面應用程式電子書的螢幕擷取畫面。](./media/modernizing-existing-desktop-apps-ebook-cover.png)

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

Microsoft Corporation 的著作權©2020

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處描述的一些範例僅供說明之用，純屬虛構。 並未影射或關聯任何真實的人、事、物。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

所有其他商標和標誌屬於其各自擁有者的財產。

共同作者：

> **Olia Gavrysh**，Microsoft 的計畫經理，.net 團隊

> **Miguel 天使 Castejón Dominguez**，創新架構師，Kabel

參與者和檢閱者：

> **Maira Wenzel**，Microsoft 的資深計畫經理，.net 團隊

> **Gorge**，Microsoft 的資深內容開發人員，.net 檔團隊

> **Miguel Ramos**，Microsoft 資深計畫經理，Windows 開發人員平臺小組

> **Adam Braden**，首席程式經理，Windows 開發人員平臺小組，Microsoft

> **Ricardo Minguez Pablos**，Microsoft 資深計畫經理，Azure IoT 團隊

> **Nish Anil**，Microsoft 的資深計畫經理，.net 團隊

> Microsoft 資深產品行銷經理**Beth Massi**

> **Scott Hunter**，合作夥伴總監計畫經理，.net 小組，Microsoft

> **Marta Fuentes Lara**、Kabel

> **Raúl Fernández De Córdoba**，Kabel

> **Antonio Manuel Fernández Cantos**，Kabel

## <a name="introduction"></a>簡介

本書是關於透過現代化的途徑來移動現有的桌面應用程式，以及納入最新的執行時間、語言和平臺功能時，您可以採用的策略。 您會發現，因為每個應用程式都不同，所以沒有任何獨特的配方，因此您的需求和喜好設定。 好消息是，您可以套用一些常用的方法，在應用程式中加入新的功能和功能。 其中一些甚至不需要對程式碼進行重大修改。 在本書中，我們將展示這些功能在幕後的運作方式，並說明其實現的機制。 此外，您還可以找到現代化詳細顯示的現有桌面應用程式的一些常見案例，讓您可以找出演變專案的靈感。

Microsoft 現代化現有應用程式的方法，是讓您彈性地建立自己的自訂路徑。 本書中所述的所有現代化策略大多都是獨立的。 您可以選擇與您的應用程式相關的專案，並略過其他對您不重要的部分。 換句話說，您可以混搭並符合您的應用程式需求的最佳處理策略。

## <a name="who-should-use-the-book"></a>誰應該使用本書

我們為想要現代化現有 Windows Forms 和 WPF 桌面應用程式的開發人員和解決方案架構師寫本書，以利用 .NET Core 和 Windows 10 的優勢。

如果您是技術決策者，例如企業架構師或開發組長或主管，想要瞭解更新現有桌面應用程式的優點，您也可能會發現這本書很有用。

## <a name="how-to-use-the-book"></a>如何使用本書

本書解決了「原因」-您可能想要將現有的應用程式現代化，以及使用 NET Core 3.1 和 MSIX 將桌面應用程式現代化所得到的特定權益。 本書的內容是專為想要總覽，但不需要專注于執行和技術、逐步詳細資料的架構師和技術決策者所設計。

在不同的章節中，會提供範例執行程式碼片段和螢幕擷取畫面，其中第5章專門用來展示範例應用程式的完整遷移流程。

## <a name="what-this-book-doesnt-cover"></a>本書未涵蓋的內容

本書涵蓋了一組特定的案例，著重于隨即轉移案例，並概述在不需要重寫程式碼的情況下，取得現代化優勢的方式。

本書不是關於從頭開始使用 .NET Core 來開發現代化應用程式，或 Windows Forms 和 WPF 入門。 它著重于如何使用最新的桌面開發技術來更新現有的桌面應用程式。

## <a name="samples-used-in-this-book"></a>本書中使用的範例

為了強調執行現代化的必要步驟，我們將使用名為的範例應用程式 `eShopModernizing` 。 此應用程式有兩種類別，Windows Forms 和 WPF，我們將示範如何對 .NET Core 執行其現代化的逐步程式。

此外，在本書的 GitHub 存放庫中，您會發現程式的結果，如果您決定遵循逐步教學課程，就可以向您詢問。

## <a name="send-your-feedback"></a>傳送您的意見反應

這本書與相關範例不斷演進，所以您的意見反應歡迎！ 如果您有關于如何改進這本書的意見，請使用[GitHub 問題](https://github.com/dotnet/docs/issues)上任何網頁底部的 [意見反應] 區段。

>[!div class="step-by-step"]
>[下一步](why-modern-applications.md)
