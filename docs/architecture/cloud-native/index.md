---
title: 為 Azure 建構雲本機 .NET 應用程式
description: 利用 Azure 的容器、微服務和無伺服器功能構建雲本機應用程式的指南。
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: cf3be07f0d37aacf4f0252ef2f4d922b7be93eee
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989060"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>為 Azure 建構雲本機 .NET 應用程式

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![封面影像](./media/cover.png)

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

版權&copy;所有 2019 由微軟公司

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。

此處描述的一些範例僅供說明之用，純屬虛構。 並未影射或關聯任何真實的人、事、物。

Microsoft 與列於 https://www.microsoft.com「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

Docker 鯨魚標誌是 Docker, Inc. 經許可使用的註冊商標。

所有其他商標和標誌屬於其各自擁有者的財產。

作者：

> **Steve "ardalis" Smith** - 軟體架構設計人員和講師 - [Ardalis.com](https://ardalis.com)
>
> **羅布維托 -** 微軟 - 首席雲系統架構師/IP 架構師 - [thinkingincloudnative.com](http://thinkingincloudnative.com/about/)

參與者和審閱者:

> **塞薩爾·德拉托雷**,微軟.NET團隊首席項目經理
>
> **Nish Anil**，Microsoft NET 小組資深方案經理

編輯者：

> **Maira Wenzel**, Sr. 內容開發人員, .NET 團隊, 微軟

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

本指南的讀者主要是開發人員、開發主管和架構師,他們有興趣學習如何構建專為雲設計的應用程式。

次要受眾是計劃選擇是否使用雲原生方法構建應用程式的技術決策者。

## <a name="how-you-can-use-this-guide"></a>此指南的使用方式

本指南首先定義雲本機,並介紹使用雲原生原則和技術構建的參考應用程式。 除了前兩章之外,本書的其餘部分被分解為特定章節,重點討論大多數雲原生應用程式共有的主題。 您可以跳轉到以下任一章節,瞭解雲本機方法:

- 資料與資料存取
- 通訊模式
- 擴充和可擴充性
- 應用程式恢復能力
- 監視與健康狀態
- 身份和安全
- DevOps

本指南以 PDF 格式和連線形式提供。 請隨時將本文檔或指向其在線版本的連結轉發給您的團隊,以幫助確保對這些主題達成共識。 這些主題大多得益於對基本原則和模式的一致理解,以及與這些主題相關的決策所涉及的權衡。 本文件的目標是為團隊及其領導者提供所需的資訊,以便對其應用程式的體系結構、開發和託管做出明智的決策。

>[!div class="step-by-step"]
>[下一步](introduction.md)
