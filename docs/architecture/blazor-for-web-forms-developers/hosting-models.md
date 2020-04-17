---
title: 布拉佐應用程式託管模型
description: 瞭解託管 Blazor 應用的不同方式,包括在 WebAssembly 上的瀏覽器或伺服器上。
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 77a022b01efba01038790c9601ea03f315a28fdf
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607928"
---
# <a name="blazor-app-hosting-models"></a>布拉佐應用程式託管模型

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Blazor 應用可以像 ASP.NET Web 窗體應用一樣託管在 IIS 中。 Blazor 應用程式也可以以以下方式之一託管:

- WebAssembly 瀏覽器中的用戶端。
- ASP.NET核心應用中的伺服器端。

## <a name="blazor-webassembly-apps"></a>布拉佐爾網路裝配應用程式

Blazor WebAssembly 應用直接在瀏覽器中基於 Web 大會的 .NET 運行時執行。 Blazor WebAssembly 應用程式的工作方式與前端 JavaScript 框架(如"角"或"反應")類似。 但是,您編寫 C# 時不是編寫 JavaScript。 .NET 運行時隨應用以及應用程式集和任何必需的依賴項一起下載。 無需瀏覽器外掛程式或擴展。

下載的程式集是正常的 .NET 程式集,就像在任何其他 .NET 應用中使用一樣。 由於運行時支援 .NET 標準,因此您可以將現有的 .NET 標準庫與 Blazor WebAssembly 應用一起使用。 但是,這些程式集仍將在瀏覽器安全沙箱中執行。 某些功能可能會引發<xref:System.PlatformNotSupportedException>,例如嘗試存取檔案系統或打開任意網路連接。

當應用載入時,將啟動 .NET 執行時並指向應用程式集。 應用啟動邏輯運行,並呈現根元件。 Blazor 根據元件呈現的輸出計算 UI 更新。 然後應用 DOM 更新。

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

Blazor WebAssembly 應用程式運行純用戶端。 此類應用可以部署到靜態網站託管解決方案(如 GitHub 頁面或 Azure 靜態網站託管)。 伺服器根本不需要 .NET。 深度連結到應用的某些部分通常需要伺服器上的路由解決方案。 路由解決方案將請求重定向到應用的根目錄。 例如,可以使用 IIS 中的 URL 重寫規則來處理此重定向。

要獲得 Blazor 和全堆疊 .NET Web 開發的所有優勢,請使用 ASP.NET 核心託管 Blazor WebAssembly 應用程式。 通過在用戶端和伺服器上使用 .NET,可以輕鬆地共用代碼並使用一組一致的語言、框架和工具構建應用。 Blazor 提供了方便的範本來設置包含 Blazor WebAssembly 應用和ASP.NET核心主機專案的解決方案。 生成解決方案後,Blazor 應用中生成的靜態檔由已設置回退路由的ASP.NET酷睿應用託管。

## <a name="blazor-server-apps"></a>布拉佐爾伺服器應用程式

回想一下[Blazor架構](architecture-comparison.md#blazor)討論,Blazor元件將其輸出呈現為`RenderTree`稱為的中間抽象。 然後,Blazor 框架將呈現的內容與以前呈現的內容進行比較。 差異應用於 DOM。 Blazor 元件與其呈現輸出的應用方式分離。 因此,元件本身不必在更新 UI 的進程相同的進程中運行。 事實上,他們甚至不必在同一台計算機上運行。

在 Blazor Server 應用中,元件在伺服器上運行,而不是在瀏覽器中用戶端運行。 瀏覽器中發生的 UI 事件透過即時連接發送到伺服器。 事件將發送到正確的元件實例。 元件渲染和計算的 UI 差異被序列化並發送到瀏覽器,並將其應用於 DOM。

![Blazor 伺服器](media/hosting-models/blazor-server.png)

如果您使用了ASP.NETAJAX和控制,Blazor<xref:System.Web.UI.UpdatePanel>伺服器託管模型聽起來可能很熟悉。 控制件`UpdatePanel`處理應用部分頁面更新以回應以觸發頁面上的事件。 觸發時,請求`UpdatePanel`部分更新,然後應用它,而無需刷新頁面。 使用管理 UI`ViewState`的狀態 。 Blazor Server 應用略有不同,因為應用需要與用戶端建立活動連接。 此外,伺服器上維護所有 UI 狀態。 除了這些差異之外,這兩個模型在概念上是相似的。

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>如何選擇正確的布拉佐託管模式

如[Blazor 託管模型文檔](/aspnet/core/blazor/hosting-models)中所述,不同的 Blazor 託管模型有不同的權衡。

Blazor WebAssembly 託管模型具有以下優點:

- 沒有 .NET 伺服器端依賴項。 應用程式在下載到用戶端後已完全正常運行。
- 充分利用客戶端資源和功能。
- 工作從伺服器卸載到用戶端。
- ASP.NET 酷網路伺服器不需要託管應用。 可以使用無伺服器部署方案(例如,從CDN為應用提供服務)。

Blazor WebAssembly 託管模型的缺點有:

- 瀏覽器功能限制應用。
- 需要有能力的用戶端硬體和軟體(例如,Web 組裝支援)。
- 下載大小較大,並且載入應用需要更長的時間。
- .NET 運行時和工具支援不太成熟。 例如[,.NET 標準](../../standard/net-standard.md)支持和調試存在限制。

相反,Blazor 伺服器託管模型具有以下優點:

- 下載大小比用戶端應用小得多,並且應用程式的載入速度也快得多。
- 該應用程式充分利用了伺服器功能,包括使用任何 .NET 核心相容 API。
- 伺服器上的 .NET Core 用於運行應用,因此現有的 .NET 工具(如調試)按預期工作。
- 支援精簡用戶端。 例如,伺服器端應用適用於不支援 WebAssembly 和資源受限的設備上的瀏覽器。
- 應用程式的 .NET/C++ 代碼庫(包括應用的元件代碼)不提供給用戶端。

Blazor 伺服器託管模型的缺點有:

- 更高的 UI 延遲。 每個使用者交互都涉及網路躍點。
- 沒有離線支援。 如果用戶端連接失敗,應用將停止工作。
- 對於許多用戶的應用來說,可擴充性具有挑戰性。 伺服器必須管理多個用戶端連接並處理用戶端狀態。
- 需要ASP.NET核心伺服器才能為應用提供服務。 無法使用無伺服器部署方案。 例如,不能從 CDN 為應用提供服務。

前面的權衡清單可能很嚇人,但您的託管模型可以在以後更改。 無論選擇了何種 Blazor 託管模型,元件模型都是*相同的*。 原則上,相同的元件可用於任一託管模型。 你的應用代碼不會更改;但是,你的應用代碼不會更改。但是,引入抽象是一個很好的做法,這樣您的元件將保持與模型無關的託管。 這些抽象允許你的應用更容易採用不同的託管模型。

## <a name="deploy-your-app"></a>部署您的應用程式

ASP.NET Web 窗體應用通常託管在 Windows 伺服器電腦或群集上的 IIS 上。 Blazor 應用程式還可以:

- 託管在IIS上,作為靜態檔或作為ASP.NET核心應用。
- 利用 ASP.NET Core 的靈活性,託管在各種平台和伺服器基礎架構上。 例如,您可以在 Linux 上使用[Nginx](/aspnet/core/host-and-deploy/linux-nginx)或[Apache](/aspnet/core/host-and-deploy/linux-apache)託管 Blazor 應用程式。 有關如何發佈和部署 Blazor 應用的詳細資訊,請參閱 Blazor[託管和部署](/aspnet/core/host-and-deploy/blazor/)文檔。

在下一節中,我們將介紹如何設置 Blazor WebAssembly 和 Blazor Server 應用的專案。

>[!div class="step-by-step"]
>[前一個](architecture-comparison.md)
>[下一個](project-structure.md)
