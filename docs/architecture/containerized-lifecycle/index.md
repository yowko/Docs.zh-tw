---
title: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
description: 取得使用 Docker 和 Microsoft 平臺和工具開發和部署容器化應用程式的開發和部署程式的概要說明。
ms.date: 01/06/2021
ms.openlocfilehash: 94c277e349bacee9b9fc7b160043005dd4135958
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970111"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a>Microsoft 平台和工具的容器化 Docker 應用程式生命週期

![書籍封面](./media/devops-book-cover-large-we.png)

**版本5.0 版** -更新為 ASP.NET Core 5。0

請參閱 [變更記錄](https://aka.ms/DockerLifecycleEbookChangelog) ，以取得書籍更新和社區貢獻。

本指南是使用 Microsoft 平臺和工具，透過 Docker 開發和部署容器化 ASP.NET Core 應用程式的一般總覽。 本指南包含 Azure DevOps 的高階簡介，可用於執行 CI/CD 管線，以及 Azure Container Registry (ACR) 和 Azure Kubernetes Services 部署的 AKS。

針對低層級、開發相關的詳細資料，您可以看到 [.Net 微服務：容器化 .Net 應用程式的架構](../microservices/index.md) 指南和 it 相關的參考應用程式 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)。

## <a name="send-us-your-feedback"></a>將您的意見反應傳送給我們！

本指南的撰寫目的是為了協助您了解 .NET 中的容器化應用程式和微服務架構。 本指南和相關參考應用程式會不斷改進，因此歡迎您提供寶貴的意見反應！ 如果您有關于如何改進本指南的意見，請在中提交意見反應 <https://aka.ms/ebookfeedback> 。

## <a name="credits"></a>學分

作者︰

> **Cesar de la Torre**，Sr. Microsoft Corp. .NET 產品小組 PM

收購編輯器：

> **Janine 派翠克**

開發編輯器：

> Microsoft 的 Microsoft 解決方案專業人員 **Bob Russell**
>
> [**八進位發行，Inc。**](http://www.octalpub.com/)

編輯生產：

> [Dianne Russell](http://www.octalpub.com/)
>
> **八進位發行，Inc。**

Copyeditor:

> Microsoft 的 Microsoft 解決方案專業人員 **Bob Russell**

參與者和檢閱者：

> **Nish Anil**，Microsoft NET 小組資深方案經理
>
> 以簡單的概念 **Miguel Veloso** 軟體發展工程師
>
> Neudesic 提供的首席顧問 **Sumit Ghosh**

## <a name="copyright"></a>著作權

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

&copy;Microsoft Corporation 的著作權2021

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處描述的一些範例僅供說明之用，純屬虛構。 並未影射或關聯任何真實的人、事、物。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

Docker whale 標誌是 Docker，Inc. 所用的注冊商標。

所有其他商標和標誌屬於其各自擁有者的財產。

>[!div class="step-by-step"]
>[下一步](introduction-to-containers-and-docker.md)
