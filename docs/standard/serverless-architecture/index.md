---
title: 無伺服器應用程式：架構、模式和 Azure 實作
description: 無伺服器架構指南。 了解實作企業應用程式的無伺服器架構 (與基礎結構即服務 [IaaS] 或平台即服務 [PaaS] 相對) 的時機、原因和方式。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 6/26/2018
ms.openlocfilehash: 89e5f387e218703a2f6311ef848b3d613a9279f7
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404813"
---
![](./media/Cover.jpg)

# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a>無伺服器應用程式：架構、模式和 Azure 實作

> 下載：<https://aka.ms/serverless-ebook>

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2018 by Microsoft Corporation

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處所描述的一些範例僅供說明，純屬虛構。 任何實際關聯或連結純屬巧合。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

所有其他商標和標誌屬於其各自擁有者的財產。

作者: 

> **[Jeremy Likness](https://twitter.com/jeremylikness)**，Microsoft Corp. APEX 資深雲端開發大使

參與者：

> **[Cecil Phillip](https://twitter.com/cecilphillip)**，Microsoft Corp. APEX 雲端開發大使 II

編輯者：

> **[Bill Wagner](https://twitter.com/billwagner)**，Microsoft Corp. APEX 資深內容開發人員

> **[Maira Wenzel](https://twitter.com/mairacw)**，Microsoft Corp. APEX 資深內容開發人員

參與者和檢閱者：

> **[Steve Smith](https://twitter.com/ardalis)**，Ardalis Services 負責人。

## <a name="introduction"></a>簡介

無伺服器旨在朝純雲端機器碼的方向發展雲端平台。 無伺服器可帶領開發人員更貼近商務邏輯，同時讓他們需擔心基礎結構。 這種模式並不代表「沒有伺服器」，而是「少掉伺服器」。 無伺服器程式碼由事件驅動。 程式碼可能因任何項目 (從傳統 HTTP Web 要求到計時器) 或上傳檔案，而受到觸發。 無伺服器背後的基礎結構可立即調整，以符合彈性需求，及提供微帳單以真正「支付您所使用項目的費用」。 無伺服器需要您以新的思考方式和方法建置應用程式，且並不是適合所有問題的解決方案。 身為開發人員，您必須決定：

* 無伺服器的優缺點為何？
* 為什麼您應該考慮為自己的應用程式使用無伺服器？
* 您如何建置、測試、部署和維護無伺服器程式碼？
* 在現有應用程式中將程式碼移轉到無伺服器的理由為何，以及完成此轉換的最佳方式是什麼？

## <a name="about-this-guide"></a>關於本指南

本指南著重使用無伺服器之應用程式的雲端原生開發。 本書會在開發無伺服器應用程式的部分，特別說明優點和指出可能的缺點，並提供無伺服器架構的介紹。 也會說明許多無伺服器使用方式範例，以及各種不同無伺服器設計模式。

本指南說明 Azure 無伺服器平台的元件，並會特別說明如何使用 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) 實作無伺服器。 您會了解觸發程序和繫結程序，以及如何使用永久的函式實作依賴狀態的無伺服器應用程式。 最後，商務範例和案例研究會提供內容和參考框架，有助您判斷無伺服器是否為適合您專案的方法。

## <a name="evolution-of-cloud-platforms"></a>雲端平台的演進

無伺服器是雲端平台多次反覆演進的高峰。 這項演進從資料中心內的實體電腦開始，逐漸發展為基礎結構即服務 (IaaS) 和平台即服務 (PaaS)。

![演進：從內部部署至無伺服器](./media/serverless-evolution-iaas-paas.png)

在發展雲端以前，開發與作業之間的界限非常明確。 部署應用程式代表要回答無數個問題，如：

* 應該安裝什麼硬體？
* 如何保護電腦的實體存取？
* 資料中心需要不斷電供應系統 (UPS) 嗎？
* 儲存體備份傳送至何處？
* 應該具有備用電力嗎？

這份清單還不只如此，而且額外負荷也很龐大。 在許多情況下，IT 部門不得已，必須處理許多浪費的資源。 浪費的原因是配置太多伺服器作為災害復原用的備份電腦和用於相應放大的待命伺服器。幸運的是，在隨著虛擬機器 (VM) 推出虛擬化技術後 (例如 [Hyper-V](/virtualization/hyper-v-on-windows/about/))，產生了基礎結構即服務 (IaaS)。 虛擬化的基礎結構可讓作業設定一組標準的伺服器作為骨幹，而創造出彈性的環境，可「視需求」佈建唯一的伺服器。 更重要的是，虛擬化為使用雲端提供虛擬機器「作為服務」創造了很棒的條件。 公司可以不用擔心備用電力或實體電腦。 相反地，則是以虛擬環境為重心。

因為作業仍需負責處理各種工作，所以 IaaS 仍然需要龐大的額外負荷。 這些工作包括：

* 修補和備份伺服器。
* 安裝套件。
* 保持最新的作業系統。
* 監視應用程式。

下一階段的演進則提供平台即服務 (PaaS)，以減少額外負荷。 利用 PaaS，雲端提供者可處理作業系統、安全性修補程式，甚至是必要套件，以支援特定平台。 開發人員並不需要建置 VM，然後設定 .NET Framework 和 Internet Information Services (IIS) 伺服器，只要選擇「平台目標」，如「Web 應用程式」或「API 端點」，然後直接部署程式碼。 基礎結構問題已減少為：

* 需要何種大小的服務？
* 服務如何相應放大 (新增更多伺服器或節點)？
* 服務如何相應增加 (增加裝載伺服器或節點的容量)？

無伺服器以事件驅動的程式碼為重心，進一步將伺服器抽象化。 開發人員所專注的部分不是平台，而是執行單一事項的微服務。 建置無伺服器程式碼的兩大關鍵問題為：

* 何者觸發程式碼？
* 程式碼會執行什麼工作？

使用無伺服器，基礎結構會抽象化。 在某些情況下，開發人員完全不用再擔心主機。 不論 IIS、Kestrel、Apache 或一些其它 Web 伺服器的執行個體是否在執行，以管理 Web 要求，開發人員都可專注在 HTTP 觸發程式上。 觸發程序會為要求提供標準的跨平台承載。 承載不僅可簡化開發過程，還可協助測試，並在某些情況下，使程式碼容易跨平台移植。

無伺服器的另一項功能就是微帳單。 Web 應用程式通常會裝載 Web API 端點。 在傳統裸機中，對於 IaaS 甚至是 PaaS 的實作，需要持續為要裝載 API 的資源付費。 這表示即使未存取這些資源，您仍要付費才可裝載端點。 通常您會發現其中一個 API 的呼叫次數比其他 API 多，所以整個系統會為了支援常用的端點而有所調整。 無伺服器可讓您個別調整每個端點，並依據使用量付費，所以當您未呼叫 API 時，就不會產生任何費用。 在許多情況下，移轉可大幅降低持續產生的費用，以支援端點。

## <a name="what-this-guide-doesnt-cover"></a>本指南未說明的內容

本指南特別說明架構方法和設計模式，但不會深入說明 Azure Functions、[Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)或其他無伺服器平台的實作詳細資料。 例如，本指南不會說明，Logic Apps 的進階工作流程或 Azure Functions 的功能，例如設定跨原始來源資源共用 (CORS)、套用自訂網域，或上傳 SSL 憑證。 這些詳細資料都可透過線上 [Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions/functions-reference)取得。

### <a name="additional-resources"></a>其他資源

* [Azure 架構中心](https://docs.microsoft.com/azure/architecture/)
* [雲端應用程式的最佳做法](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a>誰應該使用本指南

本指南專為想要以 .NET 建置可在內部部署或雲端使用無伺服器元件之企業應用程式的開發人員和解決方案架構設計人員所撰寫。 它適合具有下列興趣的開發人員、架構設計人員和技術決策者：

* 了解無伺服器開發的優缺點
* 了解如何處理無伺服器架構
* 無伺服器應用程式的實作範例

## <a name="how-to-use-the-guide"></a>如何使用本指南

本指南的第一部分會比較數個不同的架構方法，來探究為何無伺服器是可行的選項。 因為軟體開發的所有層面都會受到架構決策所影響，所以其會同時探究技術和開發生命週期。 接著本指南會探究使用案例和設計模式，並包含使用 Azure Functions 的參考實作。 每個章節都會包含其他資源以深入了解特定領域。 最後本指南會提供無伺服器實作的逐步解說與實際操作探索資源。

## <a name="send-your-feedback"></a>傳送您的意見反應

本指南和相關範例會不斷改進，因此歡迎您提供意見反應！ 如果您想提出如何改進本指南意見，請使用 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。

>[!div class="step-by-step"]
[下一步](architecture-approaches.md)