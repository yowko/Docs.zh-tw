---
title: Blazor 應用程式裝載模型
description: 瞭解用來裝載應用程式的不同方式 Blazor ，包括在或伺服器上的瀏覽器中 WebAssembly 。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 2ebb021d2fce46a91a006227ccf9ba0cbcc5eea5
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267603"
---
# <a name="no-locblazor-app-hosting-models"></a>Blazor 應用程式裝載模型

Blazor 應用程式可以裝載在 IIS 中，就像 ASP.NET Web Forms apps 一樣。 Blazor 您也可以透過下列其中一種方式來裝載應用程式：

- 瀏覽器中的用戶端 WebAssembly 。
- ASP.NET Core 應用程式中的伺服器端。

## <a name="no-locblazor-no-locwebassembly-apps"></a>BlazorWebAssembly應用程式

BlazorWebAssembly應用程式會直接在以 .net 執行時間為基礎的瀏覽器中執行 WebAssembly 。 BlazorWebAssembly應用程式的運作方式類似于前端 JavaScript 架構，例如角度或回應。 不過，您不需要撰寫 JavaScript，而是撰寫 c #。 .NET 執行時間會隨應用程式一起下載，以及應用程式元件和任何必要的相依性。 不需要瀏覽器外掛程式或延伸模組。

下載的元件是一般的 .NET 元件，就像您會在任何其他 .NET 應用程式中使用一樣。 因為執行時間支援 .NET Standard，所以您可以將現有的 .NET Standard 程式庫與您的 Blazor WebAssembly 應用程式搭配使用。 不過，這些元件仍會在瀏覽器安全性沙箱中執行。 有些功能可能會擲回 <xref:System.PlatformNotSupportedException> ，像是嘗試存取檔案系統或開啟任意網路連接。

當應用程式載入時，.NET 執行時間會啟動並指向應用程式元件。 應用程式啟動邏輯會執行，並且會呈現根元件。 Blazor 根據元件的轉譯輸出計算 UI 更新。 接著會套用 DOM 更新。

![：：：非 loc (Blazor) ：：：：：：非 loc (WebAssembly) ：：：](media/hosting-models/blazor-webassembly.png)

BlazorWebAssembly應用程式只會執行用戶端。 這類應用程式可以部署到靜態網站裝載解決方案，例如 GitHub 頁面或 Azure 靜態網站裝載。 伺服器上完全不需要 .NET。 深層連結到應用程式的元件通常需要在伺服器上使用路由解決方案。 路由解決方案會將要求重新導向至應用程式的根目錄。 例如，您可以使用 IIS 中的 URL 重寫規則來處理此重新導向。

若要取得 Blazor 和完整堆疊 .net 網頁程式開發的所有優點，請使用 ASP.NET Core 裝載您的 Blazor WebAssembly 應用程式。 藉由在用戶端和伺服器上使用 .NET，您就可以輕鬆地共用程式碼，並使用一組一致的語言、架構和工具來建立您的應用程式。 Blazor 提供方便的範本，以設定同時包含 Blazor WebAssembly 應用程式和 ASP.NET Core 主專案的方案。 建立解決方案時，應用程式內建的靜態檔案 Blazor 是由已設定 fallback 路由的 ASP.NET Core 應用程式所裝載。

## <a name="no-locblazor-server-apps"></a>Blazor 伺服器應用程式

回想一下，從[ Blazor 架構](architecture-comparison.md#blazor)討論，元件會將 Blazor 其輸出轉譯為中繼抽象概念，稱為 `RenderTree` 。 Blazor然後，架構會比較呈現的內容與先前轉譯的內容。 這些差異會套用至 DOM。 Blazor 元件會從其轉譯輸出的套用方式分離出來。 因此，元件本身不需要在與更新 UI 程式相同的進程中執行。 事實上，他們甚至不需要在同一部電腦上執行。

在 Blazor 伺服器應用程式中，元件會在伺服器上執行，而不是在瀏覽器中的用戶端上執行。 瀏覽器中發生的 UI 事件會透過即時連接傳送至伺服器。 事件會分派至正確的元件實例。 元件會轉譯，而計算的 UI 差異會序列化並傳送至瀏覽器套用至 DOM 的位置。

![：：：非 loc (Blazor) ：：： Server](media/hosting-models/blazor-server.png)

Blazor如果您已經使用 ASP.NET AJAX 和控制項，伺服器裝載模型可能會很熟悉 <xref:System.Web.UI.UpdatePanel> 。 `UpdatePanel`控制項會處理套用部分頁面更新，以回應頁面上的觸發程式事件。 觸發時， `UpdatePanel` 會要求部分更新，並在不需要重新整理頁面的情況下套用。 UI 的狀態是使用管理 `ViewState` 。 Blazor 伺服器應用程式稍有不同，因為應用程式需要與用戶端使用中的連接。 此外，伺服器上會維護所有的 UI 狀態。 除了這些差異之外，這兩個模型在概念上類似。

## <a name="how-to-choose-the-right-no-locblazor-hosting-model"></a>如何選擇正確的 Blazor 裝載模型

如[ Blazor 裝載模型](/aspnet/core/blazor/hosting-models)檔中所述，不同的 Blazor 裝載模型有不同的取捨。

Blazor WebAssembly 裝載模型有下列優點：

- 沒有 .NET 伺服器端相依性。 應用程式在下載至用戶端之後可完全正常運作。
- 用戶端資源和功能已完全運用。
- 工作會從伺服器卸載至用戶端。
- 不需要 ASP.NET Core web 伺服器來裝載應用程式。 無伺服器部署案例可能 (例如，從 CDN) 提供應用程式。

裝載模型的缺點 Blazor WebAssembly 如下：

- 瀏覽器功能會限制應用程式。
- 支援的用戶端硬體和軟體 (例如， WebAssembly 需要支援) 。
- 下載大小更大，而應用程式需要較長的時間才能載入。
- .NET 執行時間和工具支援較不成熟。 例如， [.NET Standard](../../standard/net-standard.md) 支援和偵錯工具有一些限制。

相反地， Blazor 伺服器裝載模型提供下列優點：

- 下載大小遠小於用戶端應用程式，而應用程式的載入速度更快。
- 應用程式會充分利用伺服器功能，包括使用任何 .NET Core 相容的 Api。
- 伺服器上的 .NET Core 可用來執行應用程式，因此現有的 .NET 工具（例如偵錯工具）會如預期般運作。
- 支援瘦用戶端。 例如，伺服器端應用程式會使用不支援 WebAssembly 和在資源受限裝置上的瀏覽器。
- 應用程式的 .NET/c # 程式碼基底（包括應用程式的元件程式碼）不會提供給用戶端。

Blazor伺服器裝載模型的缺點是：

- 更高的 UI 延遲。 每個使用者互動都牽涉到網路躍點。
- 沒有離線支援。 如果用戶端連接失敗，應用程式就會停止運作。
- 針對具有許多使用者的應用程式，擴充性相當困難。 伺服器必須管理多個用戶端連接並處理用戶端狀態。
- 需要 ASP.NET Core 伺服器才能提供應用程式。 無伺服器部署案例無法進行。 例如，您不能從 CDN 提供應用程式。

上述的取捨清單可能會很嚇人，但您可以稍後再變更您的裝載模型。 無論選取的 Blazor 裝載模型為何，元件模型都 *相同*。 在主體中，相同的元件可以搭配任一裝載模型使用。 您的應用程式程式碼不會變更;不過，建議您引入抽象概念，讓您的元件保持裝載模型無關。 抽象概念可讓您的應用程式更容易採用不同的裝載模型。

## <a name="deploy-your-app"></a>部署您的應用程式

ASP.NET Web Forms 的應用程式通常裝載于 Windows Server 電腦或叢集上的 IIS。 Blazor 應用程式也可以：

- 以靜態檔案或 ASP.NET Core 應用程式的形式裝載于 IIS 上。
- 利用 ASP.NET Core 的彈性裝載于各種平臺和伺服器基礎結構上。 例如，您可以 Blazor 在 Linux 上使用 [Nginx](/aspnet/core/host-and-deploy/linux-nginx) 或 [Apache](/aspnet/core/host-and-deploy/linux-apache) 來裝載應用程式。 如需有關如何發佈和部署應用程式的詳細資訊 Blazor ，請參閱 Blazor [裝載和部署](/aspnet/core/host-and-deploy/blazor/) 檔。

在下一節中，我們將探討如何 Blazor WebAssembly Blazor 設定和伺服器應用程式的專案。

>[!div class="step-by-step"]
>[上一個](architecture-comparison.md) 
>[下一步](project-structure.md)
