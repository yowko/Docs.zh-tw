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
ms.openlocfilehash: f77058ac0cb87d0316395bce1dfb11401a2ce806
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585337"
---
# <a name="wpf-community-feedback"></a>WPF 社群意見回應

Microsoft 會公開各種社群資源供您深入了解、 討論及在 Windows Presentation Foundation (WPF) 提供意見反應。 這些資源包括論壇並[Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)站台。 每一種社群資源分別提供不同的優點。 這些優點說明，是一組以確保最佳的回應來自社群及 Microsoft，特別是使用每個最佳作法。

> [!NOTE]
> 請勿使用位於每個頁面底部的意見區段來傳送產品意見反應。 這些連結僅適用於對文件的意見反應。

## <a name="forums"></a>論壇

[WPF 論壇](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=wpf)是討論與解決問題的主要社群資源。 論壇提供了一組完整的支援功能以進行討論及解決問題，包括：

- 搜尋。
- 討論追蹤。
- 豐富的文字和程式碼格式。
- Visual Studio 整合。
- 最有價值專家 (Most Valued Professional，MVP) 和社群的參與。
- 透過監視確定文章能夠在最快的時間內獲得回應。

若要詢問有關 WPF 社群的問題的另一個選項是[Stack Overflow](https://stackoverflow.com/questions/tagged/wpf)。

### <a name="forum-best-practices"></a>論壇最佳做法

使用下列最佳做法有助於解決的問題張貼到 WPF 論壇中最快的時間。 這些作法適用於所有的論壇。

#### <a name="search-existing-posts"></a>搜尋現有文章

某些問題經常發生，其他人也曾經遇到相同的問題。 因此，您可以快速解決問題，或是在現有的討論加上您的意見。

#### <a name="use-meaningful-titles"></a>使用有意義的標題

簡潔又有意義的標題會提升您文章的可搜尋性。 它們也方便判斷他們是否能夠解決您問題的其他 WPF 論壇社群成員。

#### <a name="include-appropriate-content"></a>加入適當的內容

說明此問題，以及您已嘗試透過它運作的方式。 可能的話，請加入支援程式碼片段，或是可示範問題的最簡短範例。 這些詳細資料將有助於增加問題迅速獲得解答的機會。

## <a name="visual-studio-developer-community"></a>Visual Studio 開發人員社群

某些問題可能不容易解決或根本無法解決。 發生這種情況的原因包括技術上的 Bug、將技術套用至特定案例時發生困難，或是缺乏特定案例的支援等。 這項資訊，請務必使用 Microsoft，並可以透過提供[Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)站台。

WPF 產品意見反應中心上張貼的項目會路由到 WPF 小組的內部 bug 資料庫。 因此，它是最可靠的方式，以取得您的意見反應給 WPF 功能擁有者。 此外，您可以驗證和追蹤建議與 bug，以及投票，以協助 WPF 小組決定問題的優先順序。

### <a name="developer-community-best-practices"></a>開發人員社群的最佳做法

當張貼文章至 Visual Studio 開發人員社群，搜尋現有文章、 提供有意義的標題和適當的內容會是重要的最佳作法，就如同它們張貼文章到 WPF 論壇。 以下是您應該採用的其他最佳做法。

#### <a name="search-existing-posts"></a>搜尋現有文章

某些問題經常發生，其他人也曾經遇到相同的問題。 因此，您可以快速解決問題，或者您可以加入您意見傳送到現有的問題。

#### <a name="use-meaningful-titles"></a>使用有意義的標題

簡潔又有意義的標題增加您的問題導向到最適當的 WPF 小組在最短時間內的機會。 這是特別重要的一項技術，例如 WPF 中，其中包含許多相互關聯的功能。

#### <a name="describe-how-to-reproduce-your-bug"></a>說明如何重現 bug

當您張貼有關 Bug 的文章時，請務必加入下列各項相關資訊：

- 提供的 Bug 詳細描述。
- 使用程式碼片段輔助說明 Bug。
- 提供示範如何重現 Bug 的步驟清單。
- 加入可重現 Bug 的最簡單程式碼範例。
- 說明 Bug 是否能以相同的方式重現。
- 加入相關的例外狀況資訊。

 如果 Bug 與安裝或設定相關，請附上相關的安裝記錄和快照 (位於您 %temp% 資料夾中開頭有 "dd_" 的檔案)。

 若為編譯或組建問題，請附上組建記錄檔。 MSBuild 系統可以設定為支援使用各種詳細等級進行記錄，使用 /v： 參數，從命令列，或藉由設定適當的層級從整合式開發環境 (IDE) 如 Visual Studio。

#### <a name="provide-environment-information"></a>提供環境資訊

背景資訊通常有助於增加文章的內容。 特別是，更別提作業系統平台、 處理器系列和架構，例如 「 Windows 10 版本 1709，intel （) mhz,8 x64。 」

如果張貼的問題與轉譯有關，在可能的情況下，您也應該加入圖形卡和驅動程式的詳細資料。 這項資訊非常重要的因為 WPF 是一種展示架構。

#### <a name="provide-solution-or-project-information"></a>提供方案或專案資訊

Bug 可能與您用來開發和建置應用程式的工具，以及您所建置的應用程式類型有關。 因此，列出下列資訊可能會有幫助：

- 您所建置的應用程式類型，例如：
  - 應用程式 (*.exe*) 或程式庫 (*.dll*)
  - Extensible Application Markup Language (XAML) 瀏覽器應用程式 (XBAP)
  - 鬆散的 XAML 應用程式
  - 安裝的獨立應用程式
  - 獨立 ClickOnce 部署的應用程式
- 開發工具，例如：
  - MSBuild
  - Expression Graphic Designer
  - Expression Interactive Designer
  - Visual Studio
- 方案設定，例如：
  - 解決方案
  - 單一專案
  - 具有多個相依專案的方案
- 您的應用程式是否有特定語言或非語言相關的資源。 例如，您是否指定了 `Application`、`Page` 和 `Resource` 等類型的 `UICulture` 專案屬性或可當地語系化的中繼資料？
- 您是否在 AssemblyInfo.cs 或 AssemblyInfo.vb 檔案中使用了非語言相關的設定。

#### <a name="provide-scenario-and-impact-information"></a>提供案例和影響資訊

提供資訊清單的 bug 和其影響的案例的相關資訊。 它會決定是否時機及方式解決問題，或者是否改為使用可接受的因應措施時，非常重要的 WPF 小組這項資訊。

一般來說，當機和資料遺失案例的影響較大，因此也最容易設定優先權。 不過，某些 Bug 僅會在罕見的案例中出現，而這些案例可能是某些情況的主線案例。 提供的案例和影響的相關內容可以幫助 WPF 小組做出正確的決策。

## <a name="see-also"></a>另請參閱

- [如何回報在使用 Visual Studio 2017 時發生的問題](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
