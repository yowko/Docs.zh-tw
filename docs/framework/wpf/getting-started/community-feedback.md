---
title: WPF 社群意見回應
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6394bda1c2bcd4a42f76579d541173e65ecd2dc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557832"
---
# <a name="wpf-community-feedback"></a>WPF 社群意見回應

Microsoft 會公開各種不同的社群資源供您深入了解、 討論及在 Windows Presentation Foundation (WPF) 提供意見反應。 這些資源包括論壇和[Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)站台。 每一種社群資源分別提供不同的優點。 這些優點如下所示，還有一組以確保最佳回應從 Microsoft 和社群，特別是使用每個最佳作法。

> [!NOTE]
> 傳送產品意見反應，請勿使用位於每個頁面底部的意見反應區段。 這些連結僅適用於對文件的意見反應。

## <a name="forums"></a>論壇

[WPF 論壇](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=wpf)是主要的社群資源來討論和解決問題。 論壇提供了一組完整的支援功能以進行討論及解決問題，包括：

- 搜尋。
- 討論追蹤。
- 豐富的文字和程式碼格式。
- Visual Studio 整合。
- 最有價值專家 (Most Valued Professional，MVP) 和社群的參與。
- 透過監視確定文章能夠在最快的時間內獲得回應。

若要詢問有關 WPF 社群的另一個選項是[堆疊溢位](https://stackoverflow.com/questions/tagged/wpf)。

### <a name="forum-best-practices"></a>論壇最佳作法

使用下列最佳作法至 WPF 論壇張貼在最快時間內解決問題的說明。 這些作法適用於所有的論壇。

#### <a name="search-existing-posts"></a>搜尋現有的文章

某些問題經常發生，其他人也曾經遇到相同的問題。 因此，您可以快速解決問題，或是在現有的討論加上您的意見。

#### <a name="use-meaningful-titles"></a>使用有意義的標題

簡潔的有意義的標題改善文章的探索能力。 它們也更輕鬆判斷他們是否能夠解決問題的其他 WPF 論壇社群成員。

#### <a name="include-appropriate-content"></a>加入適當的內容

描述問題，您已嘗試透過它運作的方式。 可能的話，請加入支援程式碼片段，或是可示範問題的最簡短範例。 這些詳細資料將有助於增加問題迅速獲得解答的機會。

## <a name="visual-studio-developer-community"></a>Visual Studio 開發人員社群

某些問題可能不容易解決或根本無法解決。 發生這種情況的原因包括技術上的 Bug、將技術套用至特定案例時發生困難，或是缺乏特定案例的支援等。 此資訊給 Microsoft，很重要，可以透過提供[Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)站台。

張貼 WPF 產品意見反應中心上的項目會路由傳送至 WPF 小組內部的 bug 資料庫。 因此，它是最可靠的方式，以取得您的意見反應給 WPF 功能擁有者。 此外，您可以驗證和追蹤的建議和 bug，以及投票，進而協助 WPF 小組優先處理的問題。

### <a name="developer-community-best-practices"></a>開發人員社群的最佳作法

當公佈到 Visual Studio 開發人員社群，搜尋現有的文章，提供有意義的標題和適當的內容會是重要的最佳作法，就如同它們公佈至 WPF 論壇。 以下是您應該採用的其他最佳做法。

#### <a name="search-existing-posts"></a>搜尋現有的文章

某些問題經常發生，其他人也曾經遇到相同的問題。 因此，您可以快速解決問題，或者您可以加入您的輸入現有的問題。

#### <a name="use-meaningful-titles"></a>使用有意義的標題

簡潔的有意義的標題增加您的問題導向到最適當的 WPF 小組在最短的時間內的機會。 這是特別重要的技術，例如 WPF 中，其中包含許多相關聯的功能。

#### <a name="describe-how-to-reproduce-your-bug"></a>說明如何重現 bug

當您張貼有關 Bug 的文章時，請務必加入下列各項相關資訊：

- 提供的 Bug 詳細描述。
- 使用程式碼片段輔助說明 Bug。
- 提供示範如何重現 Bug 的步驟清單。
- 加入可重現 Bug 的最簡單程式碼範例。
- 說明 Bug 是否能以相同的方式重現。
- 加入相關的例外狀況資訊。

 如果 Bug 與安裝或設定相關，請附上相關的安裝記錄和快照 (位於您 %temp% 資料夾中開頭有 "dd_" 的檔案)。

 若為編譯或組建問題，請附上組建記錄檔。 MSBuild 系統可以設定為支援使用各種 verbosities 記錄使用 /v 參數從命令列，或藉由設定適當的層級從整合式開發環境 (IDE) 類似 Visual Studio。

#### <a name="provide-environment-information"></a>提供環境資訊

背景資訊通常有助於增加文章的內容。 特別是，有提及作業系統平台、 處理器系列和架構，例如 「 Windows 10 版本 1709 intel （) Xeon(R) x64。 」

如果張貼的問題與轉譯有關，在可能的情況下，您也應該加入圖形卡和驅動程式的詳細資料。 這項資訊非常重要的因為 WPF 是展示架構。

#### <a name="provide-solution-or-project-information"></a>提供的方案或專案的資訊

Bug 可能與您用來開發和建置應用程式的工具，以及您所建置的應用程式類型有關。 因此，列出下列資訊可能會有幫助：

- 您所建置的應用程式類型，例如：
  - 應用程式 (*.exe*) 或程式庫 (*.dll*)
  - Extensible Application Markup Language (XAML) 瀏覽器應用程式 (XBAP)
  - 鬆散的 XAML 應用程式
  - 安裝的獨立應用程式
  - 獨立 ClickOnce 部署應用程式
- 開發工具，例如：
  - MSBuild
  - 運算式圖形設計人員
  - 運算式互動式的設計工具
  - Visual Studio
- 方案設定，例如：
  - 方案
  - 在單一專案中
  - 在方案中使用多個相依的專案
- 您的應用程式是否有特定語言或非語言相關的資源。 例如，您是否指定了 `Application`、`Page` 和 `Resource` 等類型的 `UICulture` 專案屬性或可當地語系化的中繼資料？
- 您是否在 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案中使用了非語言相關的設定。

#### <a name="provide-scenario-and-impact-information"></a>提供的案例和影響資訊

提供資訊清單的 bug 和其影響的案例的相關資訊。 這項資訊，請務必高 WPF 小組決定如果何時嘗試及如何解決問題，或者是否改為使用可接受的因應措施。

一般來說，當機和資料遺失案例的影響較大，因此也最容易設定優先權。 不過，某些 Bug 僅會在罕見的案例中出現，而這些案例可能是某些情況的主線案例。 提供內容周圍的案例和影響，幫助 WPF 小組做出適當的決策。

## <a name="see-also"></a>另請參閱

[如何回報在使用 Visual Studio 2017 時發生的問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
