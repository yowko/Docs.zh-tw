---
title: WPF 社區意見反應
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ebeae3e51cedd3add2de4062c8914693ac94f7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197002"
---
# <a name="wpf-community-feedback"></a>WPF 社區意見反應

Microsoft 會公開各種不同的社區資源，讓您瞭解、討論和提供有關 Windows Presentation Foundation （WPF）的意見反應。 這些資源包括論壇和[Visual Studio 的開發人員社區](https://developercommunity.visualstudio.com/)網站。 每一種社群資源分別提供不同的優點。 這裡描述這些優點，這是一組最佳作法，可讓您使用每個來確保來自大型和 Microsoft 的社區做出最佳回應。

> [!NOTE]
> 請勿使用位於每個頁面底部的 [意見反應] 區段來傳送產品意見反應。 這些連結僅適用於對文件的意見反應。

## <a name="forums"></a>論壇

[WPF 論壇](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wpf)是討論和解決問題的主要「社區」資源。 論壇提供了一組完整的支援功能以進行討論及解決問題，包括：

- 搜尋。
- 討論追蹤。
- 豐富的文字和程式碼格式。
- Visual Studio 整合。
- 最有價值專家 (Most Valued Professional，MVP) 和社群的參與。
- 透過監視確定文章能夠在最快的時間內獲得回應。

還有另一個選項，可讓您向關於 WPF 的社區詢問問題[Stack Overflow](https://stackoverflow.com/questions/tagged/wpf)。

### <a name="forum-best-practices"></a>論壇最佳做法

使用下列最佳作法有助於在最快的可能時間內解決張貼到 WPF 論壇的問題。 這些作法適用於所有的論壇。

#### <a name="search-existing-posts"></a>搜尋現有的文章

某些問題經常發生，其他人也曾經遇到相同的問題。 因此，您可以快速解決問題，或是在現有的討論加上您的意見。

#### <a name="use-meaningful-titles"></a>使用有意義的標題

簡潔、有意義的標題可改善您的文章的可搜尋性。 此外，也可讓其他 WPF 論壇社區成員更輕鬆地判斷是否能解決您的問題。

#### <a name="include-appropriate-content"></a>包含適當的內容

描述問題，以及您如何嘗試進行此作業。 可能的話，請加入支援程式碼片段，或是可示範問題的最簡短範例。 這些詳細資料將有助於增加問題迅速獲得解答的機會。

## <a name="visual-studio-developer-community"></a>Visual Studio 開發人員社群

某些問題可能不容易解決或根本無法解決。 發生這種情況的原因包括技術上的 Bug、將技術套用至特定案例時發生困難，或是缺乏特定案例的支援等。 這項資訊對 Microsoft 很重要，並可透過 Visual Studio 的[開發人員社區](https://developercommunity.visualstudio.com/)網站來提供。

在 WPF 產品意見反應中心張貼的專案會路由傳送至 WPF 小組的內部 bug 資料庫。 因此，將您的意見反應提供給 WPF 功能擁有者是最可靠的方法。 此外，您可以驗證和追蹤建議和 bug，以及對其進行投票，以協助 WPF 小組排定問題的優先順序。

### <a name="developer-community-best-practices"></a>開發人員社區最佳做法

張貼到 Visual Studio 的開發人員社區時，搜尋現有的文章、提供有意義的標題和適當的內容，都是重要的最佳作法，就像張貼到 WPF 論壇一樣。 以下是您應該採用的其他最佳做法。

#### <a name="search-existing-posts"></a>搜尋現有的文章

某些問題經常發生，其他人也曾經遇到相同的問題。 因此，您可以快速解決您的問題，也可以將您的輸入新增至現有的問題。

#### <a name="use-meaningful-titles"></a>使用有意義的標題

簡潔、有意義的標題會增加您的問題在最短的時間內導向至最適當的 WPF 小組的機會。 這對於 WPF 這類技術而言特別重要，其中包含許多相關的功能。

#### <a name="describe-how-to-reproduce-your-bug"></a>描述如何重現 bug

當您張貼有關 Bug 的文章時，請務必加入下列各項相關資訊：

- 提供的 Bug 詳細描述。
- 使用程式碼片段輔助說明 Bug。
- 提供示範如何重現 Bug 的步驟清單。
- 加入可重現 Bug 的最簡單程式碼範例。
- 說明 Bug 是否能以相同的方式重現。
- 加入相關的例外狀況資訊。

 如果 Bug 與安裝或設定相關，請附上相關的安裝記錄和快照 (位於您 %temp% 資料夾中開頭有 "dd_" 的檔案)。

 若為編譯或組建問題，請附上組建記錄檔。 MSBuild 系統可以設定為支援使用各種 verbosities 的記錄，方法是從命令列使用/v： switch，或從整合式開發環境（IDE）（例如 Visual Studio）設定適當的層級。

#### <a name="provide-environment-information"></a>提供環境資訊

背景資訊通常有助於增加文章的內容。 特別要提的是作業系統平臺、處理器系列和架構，例如「Windows 10 版本1709、Intel （R）（r），是 x64」。

如果張貼的問題與轉譯有關，在可能的情況下，您也應該加入圖形卡和驅動程式的詳細資料。 這項資訊很重要，因為 WPF 是展示架構。

#### <a name="provide-solution-or-project-information"></a>提供方案或專案資訊

Bug 可能與您用來開發和建置應用程式的工具，以及您所建置的應用程式類型有關。 因此，列出下列資訊可能會有幫助：

- 您所建置的應用程式類型，例如：
  - 應用程式（ *.exe*）或程式庫（ *.dll*）
  - Extensible Application Markup Language （XAML）瀏覽器應用程式（XBAP）
  - 鬆散 XAML 應用程式
  - 獨立安裝的應用程式
  - 獨立的 ClickOnce 部署應用程式
- 開發工具，例如：
  - MSBuild
  - 運算式圖形設計工具
  - 運算式互動式設計工具
  - Visual Studio
- 方案設定，例如：
  - 解決方案
  - 單一專案
  - 具有多個相依專案的方案
- 您的應用程式是否有特定語言或非語言相關的資源。 例如，您是否指定了 `Application`、`Page` 和 `Resource` 等類型的 `UICulture` 專案屬性或可當地語系化的中繼資料？
- 您是否在 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案中使用了非語言相關的設定。

#### <a name="provide-scenario-and-impact-information"></a>提供案例和影響資訊

提供資訊清單和其影響之案例的相關資訊。 這項資訊對於 WPF 小組而言非常重要，因為它會決定是否、何時和如何修正問題，或是否可以改用可接受的因應措施。

一般來說，當機和資料遺失案例的影響較大，因此也最容易設定優先權。 不過，某些 Bug 僅會在罕見的案例中出現，而這些案例可能是某些情況的主線案例。 提供案例和影響的內容，可協助 WPF 小組做出正確的決策。

## <a name="see-also"></a>請參閱

- [如何回報 Visual Studio 的問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
