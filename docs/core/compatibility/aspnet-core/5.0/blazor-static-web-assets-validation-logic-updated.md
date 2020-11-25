---
title: 重大變更： Blazor：已更新靜態 web 資產的驗證邏輯
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor：已更新靜態 web 資產的驗證邏輯
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f201818c0130739e8da4f42e7b1f3a1987f70d1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760661"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a>Blazor：已更新靜態 web 資產的驗證邏輯

ASP.NET Core 3.1 和 Blazor WebAssembly 3.2 中的靜態 web 資產發生衝突驗證時發生問題。 問題：

* 從 Razor 類別庫 (RCLs) 和 Blazor WebAssembly 應用程式之間，防止主機資產和資產之間有適當的衝突偵測。
* 大部分會影響 Blazor WebAssembly 應用程式，因為在預設情況下，RCLs 中的靜態 web 資產會在前置詞下提供服務 `_content/$(PackageId)` 。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="old-behavior"></a>舊的行為

在開發期間，RCL 的靜態 web 資產可能會以無訊息方式在相同主機路徑上以主專案資產覆寫。 請考慮已定義要在 */folder/file.txt* 提供服務之靜態 web 資產的 RCL。 如果主機將檔案放在 *wwwroot/資料夾/file.txt*，伺服器上的檔案會以無訊息方式已覆寫 RCL 或 Blazor WebAssembly 應用程式上的檔案。

## <a name="new-behavior"></a>新的行為

ASP.NET Core 正確地偵測到此問題發生的時間。 它會通知您（使用者）衝突，讓您可以採取適當的動作。

## <a name="reason-for-change"></a>變更的原因

靜態 web 資產不會被專案的 *wwwroot* 主機上的檔案覆寫。 允許覆寫這些檔案可能會導致難以診斷的錯誤。 結果可能是已發佈應用程式中未定義的行為變更。

## <a name="recommended-action"></a>建議的動作

根據預設，RCL 檔不會與主機上的檔案發生衝突。 RCL 檔案前面會加上 `_content/${PackageId}` 。 Blazor WebAssembly 檔會放在主機 URL 空間的根目錄中，這樣會更容易發生衝突。 例如，Blazor WebAssembly apps 包含 *favicon .ico* 檔案，該檔案的主機也可能包含在它的 *wwwroot* 資料夾中。

如果衝突的來源是 RCL 檔案，通常表示程式碼正在將資產從程式庫複製到專案的 *wwwroot* 資料夾。 撰寫程式碼來複製檔案，會破壞靜態 web 資產的主要目標。 這是在更新內容而不需要觸發新的編譯時，在瀏覽器上取得更新的基本概念。

您可以選擇保留這種行為，並維護主機上的檔案。 若要這樣做，請從具有自訂 MSBuild 目標的靜態 web 資產清單中移除該檔案。

若要使用 RCL 的檔案或 Blazor WebAssembly 應用程式的檔案，而不是主專案的檔案，請從主專案中移除該檔案。

## <a name="affected-apis"></a>受影響的 API

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
