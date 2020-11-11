---
title: 設計適用于 Azure 的雲端原生 .NET 應用程式
description: 利用 Azure 的容器、微服務和無伺服器功能來建立雲端原生應用程式的指南。
author: ardalis
ms.date: 11/10/2020
ms.openlocfilehash: 673bfef27c3767f68b1c30d4383cee010ba377f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506645"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>設計適用于 Azure 的雲端原生 .NET 應用程式

![封面影像](./media/cover.png)

**1.0 版**

請參閱 [變更記錄](https://aka.ms/cn-ebook-changelog) ，以取得書籍更新和社區貢獻。

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

&copy;Microsoft Corporation 的著作權2020

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。

此處描述的一些範例僅供說明之用，純屬虛構。 並未影射或關聯任何真實的人、事、物。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

Docker whale 標誌是 Docker，Inc. 所用的注冊商標。

所有其他商標和標誌屬於其各自擁有者的財產。

作者：

> **Vettor** ，首席雲端系統架構設計師/IP 架構師- [thinkingincloudnative.com](https://thinkingincloudnative.com/about/)，Microsoft
>
> **Steve "ardalis" Smith** 、軟體架構設計人員和講師- [Ardalis.com](https://ardalis.com)

參與者和審核者：

> **Cesar De La Torre** ，首席計畫經理，.net 團隊，Microsoft
>
> **Nish Anil** ，Microsoft 資深專案經理，.net 團隊
>
> **Jeremy Likness** ，Microsoft 資深專案經理，.net 團隊
>
> Microsoft 資深雲端提倡者 **Cecil Phillip**

編輯者：

> **Maira Wenzel** ，Microsoft 的專案經理，.net 團隊

## <a name="version"></a>版本

本指南已撰寫成涵蓋 **.Net core 3.1** 版本，以及許多與相同「wave」技術相關的其他更新 (也就是，Azure 和其他協力廠商技術) 導致及時使用 .net Core 3.1 版本。

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

本指南的物件主要是開發人員、開發組長和架構設計人員，想要瞭解如何建立針對雲端設計的應用程式。

次要物件是技術決策者，其打算選擇是否要使用雲端原生方法來建立應用程式。

## <a name="how-you-can-use-this-guide"></a>此指南的使用方式

本指南一開始會定義雲端原生，並介紹使用雲端原生原則和技術建立的參考應用程式。 除了前兩個章節之外，本書的其餘部分會細分為著重于大部分雲端原生應用程式常見主題的特定章節。 您可以跳到上述任何章節，以瞭解雲端原生方法：

- 資料和資料存取
- 通訊模式
- 調整規模和擴充性
- 應用程式復原
- 監視與健康狀態
- 身分識別與安全性
- DevOps

您可以在 [PDF](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf) 表單和線上取得本指南。 您可以將這份檔或其線上版本的連結，提供給您的小組，以協助確保對這些主題有大致的瞭解。 這些主題大多都是從一致瞭解基礎原則和模式，以及與這些主題相關的決策相關的取捨中獲益。 本檔的目標是要讓小組和領導人擁有針對其應用程式架構、開發和裝載做出明智決策所需的資訊。

## <a name="send-your-feedback"></a>傳送您的意見反應

本書和相關的範例不斷演進，所以您的意見反應歡迎！ 如果您有關于如何改進本書的意見，請使用內建于 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。

>[!div class="step-by-step"]
>[下一步](introduction.md)
