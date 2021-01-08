---
title: 雲端原生應用程式呢？
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |Cloud-Native 的應用程式呢？
ms.date: 12/21/2020
ms.openlocfilehash: 700d23c6b44f4eb48b3f6ec20569323280682082
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025182"
---
# <a name="what-about-cloud-native-applications"></a>雲端原生應用程式呢？

雖然 [雲端原生](https://azure.microsoft.com/overview/cloudnative/) 應用程式並不是本指南的主要焦點，但瞭解此現代化成熟度層級，並將其與 Cloud-Optimized 的應用程式區別是很有説明的。

圖4-3 將 Cloud-Native 應用程式置於應用程式現代化成熟度等級：

![顯示如何定位雲端原生應用程式的圖表。](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**圖4-3。** 定位 Cloud-Native 的應用程式

Cloud-Native 現代化成熟度等級通常需要新的開發投資。 移至 Cloud-Native 層級，通常是由商務需求來將應用程式現代化，以大幅改善大型應用程式的規模，方法是建立自發子系統 (微服務) ，這些子系統可以與應用程式的其他區域分開部署和調整，並提高這些自發應用程式元件的演進靈活性，以提供明顯的競爭優勢。

Cloud-Native 應用程式的主要要素是以微服務架構方法為基礎，而這種方法可以在整合至內部部署或雲端環境的整合型架構中，以彈性和規模調整規模來發展。

圖4-4 顯示 Cloud-Native 模型的主要特性。

![列出主要雲端原生特性的圖表。](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**圖4-4。** Cloud-Native 特性

此外，您可以藉由新增其他服務（例如人工智慧 (AI) 、machine learning (ML) 和 IoT）來擴充基本的新式 web 應用程式和雲端原生應用程式。 您可以使用這些服務中的任何一種，來擴充任何可能的 Cloud-Optimized 方法。

Cloud-Native 層級應用程式的基本差異在於應用程式架構中。 雲端原生應用程式是根據定義，以微服務為基礎的應用程式。 相較于整合型 web 應用程式或傳統的多層式應用程式，雲端原生應用程式需要特殊的架構、技術和平臺。

## <a name="cloud-native-applications-details"></a>雲端原生應用程式詳細資料

針對大型和任務關鍵性應用程式，Cloud-Native 是更先進或成熟的狀態。 Cloud-Native 的應用程式通常需要從頭建立的架構和設計，而不是現代化現有的應用程式。 Cloud-Native 應用程式和簡單 Cloud-Optimized web 應用程式之間的主要差異，是在雲端原生方法中使用微服務架構的建議。 Cloud-Optimized apps 也可以是整合型 web 應用程式或多層式應用程式。

[十二要素應用程式](https://12factor.net/) (與微服務方法密切相關的模式集合) 也會被視為雲端原生應用程式架構的需求。

[雲端原生運算基礎 (CNCF) ](https://www.cncf.io/)是雲端原生原則的主要升級。 Microsoft 是 [CNCF 的成員](https://azure.microsoft.com/blog/announcing-cncf/)。

如需如何設計和開發雲端原生應用程式的詳細指引，請閱讀下列免費電子書：

* [架構 Cloud-Native 適用于 Azure 的 .NET 應用程式](../../cloud-native/introduction.md)
* [.Net 微服務：容器化 .net 應用程式的架構](../../microservices/index.md)。

如果您將完整應用程式遷移至雲端原生模型，最重要的因素就是您必須重新架構至以微服務為基礎的架構。 這種方法顯然需要大量開發的投資，因為涉及大型重構程式。 此選項通常是針對需要新層級的擴充性和長期靈活性的任務關鍵性應用程式所選擇。 但是，您可以藉由只針對幾個新案例新增微服務來開始移往雲端原生，最後將應用程式完全重構為微服務。 此步驟是在某些案例中最好選擇的方法。

## <a name="what-about-microservices"></a>微服務呢？

當您考慮組織的雲端原生應用程式時，瞭解微服務及其運作方式是很重要的。

微服務架構是一種先進的方法，可讓您用於從頭建立的應用程式，或將現有的應用程式發展到雲端原生應用程式。 您可以從將一些微服務新增至現有的應用程式開始，以瞭解新的微服務範例。 但很明顯地，您需要架構設計和撰寫程式碼，特別是此類型的架構方法。

不過，對於新的或新式應用程式來說，微服務並不是必要的。 微服務不是「魔術專案符號」，而是建立每個應用程式的單一、最佳方式。 使用微服務的方式和時機取決於您需要建立的應用程式類型。

微服務架構即將成為分散式和大型或複雜的任務關鍵性應用程式的慣用方法，這些應用程式是以自發服務形式的多個獨立子系統為基礎。 在以微服務為基礎的架構中，應用程式會建立為服務的集合，這些服務可以獨立開發、測試、建立版本、部署及調整。 這種方法可以包含每個微服務的任何相關、自主資料庫。

若要深入瞭解您可以使用 .NET 來執行的微服務架構，請參閱可下載的 PDF 電子書 [.net 微服務：容器化 .net 應用程式的架構](https://aka.ms/microservicesebook)。 本指南也可在 [線上](../../microservices/index.md)取得。

但即使在微服務提供功能強大的功能獨立部署、強式子系統界限和技術多樣性的情況下，也會引發許多新的挑戰。 挑戰與分散式應用程式開發有關，例如分散和獨立的資料模型。實現微服務之間的復原通訊;最終一致性的需求;和操作複雜度。 相較于傳統的整合型應用程式，微服務引入了較高的複雜度層級。

由於微服務架構的複雜度，因此只有特定的案例和特定的應用程式類型適用于微服務型應用程式。 這些應用程式包括具有多個演進子系統的大型且複雜的應用程式。 在這些情況下，值得投資更複雜的軟體架構，以提升長期的靈活性及更有效率的應用程式維護。 但是針對較不復雜的案例，使用整合型應用程式方法或較簡單的多層式方法，可能會比較好。

最後一點要注意的是，即使有重複關於此概念的風險，您也不應該考慮在應用程式中使用微服務做為「全功能或根本沒有東西」。 您可以根據微服務新增小型案例，來擴充及發展現有的整合型應用程式。 您不需要從頭開始著手使用微服務架構方法。 事實上，我們建議您藉由新增新的案例，從使用現有的整合型或多層式應用程式演進。 最後，您可以將應用程式細分為自主元件或微服務。 您可以逐步開始發展整合型應用程式的微服務方向。

在任何情況下，本指南的其餘部分著重于「無微服務型應用程式」，因為本指南主要是針對通常具有整合型或多層式架構的現有應用程式現代化。

> [!div class="step-by-step"]
> [上一個](microsoft-technologies-in-cloud-optimized-applications.md) 
> [下一步](deploy-existing-net-apps-as-windows-containers.md)
