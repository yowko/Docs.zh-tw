---
title: Blazor 應用程式裝載模型
description: 瞭解裝載 Blazor 應用程式的不同方式，包括在 WebAssembly 或伺服器上的瀏覽器中。
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 3196c9ff284a23e61bdfec98e56da3f66180a18e
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183823"
---
# <a name="blazor-app-hosting-models"></a>Blazor 應用程式裝載模型

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Blazor apps 可以裝載于 IIS 中，就像 ASP.NET Web Forms 應用程式一樣。 Blazor apps 也可透過下列其中一種方式來裝載：

* 在 WebAssembly 的瀏覽器中的用戶端。
* ASP.NET Core 應用程式中的伺服器端。 

## <a name="blazor-webassembly-apps"></a>Blazor WebAssembly 應用程式

Blazor WebAssembly apps 會直接在 WebAssembly 型 .NET 執行時間的瀏覽器中執行。 Blazor WebAssembly apps 的運作方式類似于前端 JavaScript 架構，例如角度或反應。 不過，不是撰寫您撰寫C#的 JavaScript。 .NET 執行時間會隨應用程式一起下載，以及應用程式元件和任何必要的相依性。 不需要瀏覽器外掛程式或擴充功能。 

下載的元件是一般的 .NET 元件，就像您會在任何其他 .NET 應用程式中使用一樣。 由於執行時間支援 .NET Standard，因此您可以使用現有的 .NET Standard 程式庫搭配 Blazor WebAssembly 應用程式。 不過，這些元件仍然會在瀏覽器安全性沙箱中執行。 某些功能可能會擲<xref:System.PlatformNotSupportedException>回，像是嘗試存取檔案系統或開啟任意的網路連接。 

當應用程式載入時，.NET 執行時間會啟動並指向應用程式元件。 應用程式啟動邏輯會執行，而根元件則會呈現。 Blazor 會根據元件所呈現的輸出來計算 UI 更新。 接著會套用 DOM 更新。

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

Blazor WebAssembly 應用程式純粹是以用戶端執行。 這類應用程式可以部署至靜態網站裝載解決方案，例如 GitHub 頁面或 Azure 靜態網站裝載。 伺服器上完全不需要 .NET。 應用程式元件的深層連結通常需要伺服器上的路由解決方案。 路由解決方案會將要求重新導向至應用程式的根目錄。 例如，您可以在 IIS 中使用 URL 重寫規則來處理此重新導向。

若要取得 Blazor 和完整堆疊 .NET 網頁程式開發的所有優點，請使用 ASP.NET Core 裝載您的 Blazor WebAssembly 應用程式。 藉由在用戶端和伺服器上使用 .NET，您可以輕鬆地共用程式碼，並使用一組一致的語言、架構和工具來建立應用程式。 Blazor 提供便利的範本，讓您設定同時包含 Blazor WebAssembly 應用程式和 ASP.NET Core 主專案的解決方案。 建立解決方案時，Blazor 應用程式內建的靜態檔案是由已設定 fallback 路由的 ASP.NET Core 應用程式所裝載。

## <a name="blazor-server-apps"></a>Blazor 伺服器應用程式

回想一下[Blazor 架構](architecture-comparison.md#blazor)討論，Blazor 元件會將其輸出轉譯為名為的`RenderTree`中繼抽象概念。 然後，Blazor 架構會比較呈現的內容與先前轉譯的內容。 這些差異會套用至 DOM。 Blazor 元件會與其呈現輸出的套用方式分離。 因此，元件本身不需要與更新 UI 的進程在相同的進程中執行。 事實上，它們甚至不需要在同一部電腦上執行。

在 Blazor 伺服器應用程式中，元件會在伺服器上執行，而不是在瀏覽器中的用戶端上執行。 在瀏覽器中發生的 UI 事件會透過即時連線傳送至伺服器。 事件會分派至正確的元件實例。 元件會轉譯，而匯出的 UI diff 會序列化並傳送至它套用至 DOM 的瀏覽器。

![Blazor 伺服器](media/hosting-models/blazor-server.png)

如果您已使用 ASP.NET AJAX 和<xref:System.Web.UI.UpdatePanel>控制項，Blazor 伺服器裝載模型可能會很熟悉。 `UpdatePanel`控制項會處理部分頁面更新的套用，以回應頁面上的觸發程式事件。 觸發時， `UpdatePanel`會要求部分更新，然後套用它，而不需要重新整理頁面。 UI 的狀態是使用`ViewState`來管理。 Blazor 伺服器應用程式稍有不同，因為應用程式需要與用戶端使用中的連接。 此外，所有 UI 狀態都會保留在伺服器上。 除了這些差異之外，這兩個模型在概念上類似。

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>如何選擇正確的 Blazor 裝載模型

如[Blazor 裝載模型](https://docs.microsoft.com/aspnet/core/blazor/hosting-models#server-side)檔中所述，不同的 Blazor 裝載模型會有不同的取捨。

Blazor WebAssembly 裝載模型具有下列優點：

* 沒有 .NET 伺服器端相依性。 應用程式會在下載至用戶端之後完全正常運作。
* 用戶端資源和功能都可以充分運用。
* 工作會從伺服器卸載至用戶端。
* 不需要 ASP.NET Core web 伺服器來裝載應用程式。 無伺服器部署案例可行（例如，從 CDN 提供應用程式）。

Blazor WebAssembly 裝載模型的缺點如下：

* 瀏覽器功能會限制應用程式。
* 需要支援的用戶端硬體和軟體（例如 WebAssembly 支援）。
* 下載大小較大，且應用程式需要較長的時間來載入。
* .NET 執行時間和工具支援較不成熟。 例如， [.NET Standard](../../standard/net-standard.md)支援和偵錯工具中有一些限制。

相反地，Blazor 伺服器裝載模型提供下列優點：

* 下載大小遠小於用戶端應用程式，且應用程式載入速度會更快。
* 應用程式會充分利用伺服器功能，包括使用任何 .NET Core 相容的 Api。
* 伺服器上的 .NET Core 是用來執行應用程式，因此現有的 .NET 工具（例如，「偵測」）會如預期般運作。
* 支援瘦用戶端。 例如，伺服器端應用程式會使用不支援 WebAssembly 的瀏覽器，以及在資源限制的裝置上。
* 應用程式的 .NET/C#程式碼基底（包括應用程式的元件代碼）不會提供給用戶端。

Blazor 伺服器裝載模型的缺點如下：

* 較高的 UI 延遲。 每個使用者互動都牽涉到網路躍點。
* 沒有離線支援。 如果用戶端連線失敗，應用程式就會停止運作。
* 對於具有許多使用者的應用程式而言，擴充性是極具挑戰性的。 伺服器必須管理多個用戶端連接並處理用戶端狀態。
* 需要 ASP.NET Core 伺服器才能服務應用程式。 無伺服器部署案例無法進行。 例如，您無法從 CDN 服務應用程式。

前述的取捨清單可能會恐嚇，但您的裝載模型稍後可以變更。 不論選取的 Blazor 裝載模型為何，元件模型都*相同*。 原則上，相同的元件可以與任一裝載模型搭配使用。 您的應用程式代碼不會變更;不過，導入抽象概念是個很好的作法，讓您的元件保持裝載不受模型限制。 抽象概念可讓您的應用程式更輕鬆地採用不同的裝載模型。

## <a name="deploy-your-app"></a>部署您的應用程式

ASP.NET Web Forms 應用程式通常裝載于 Windows Server 電腦或叢集上的 IIS。 Blazor apps 也可以：

* 以靜態檔案或 ASP.NET Core 應用程式的形式裝載在 IIS 上。
* 利用 ASP.NET Core 的彈性，裝載在各種平臺和伺服器基礎結構上。 例如，您可以使用[Nginx](/aspnet/core/host-and-deploy/linux-nginx)或[Apache](/aspnet/core/host-and-deploy/linux-apache) On Linux 裝載 Blazor 應用程式。 如需有關如何發佈和部署 Blazor 應用程式的詳細資訊，請參閱 Blazor[裝載和部署](/aspnet/core/host-and-deploy/blazor/)檔。

在下一節中，我們將探討如何設定 Blazor WebAssembly 和 Blazor 伺服器應用程式的專案。

>[!div class="step-by-step"]
>[上一頁](architecture-comparison.md)
>[下一頁](project-structure.md)
