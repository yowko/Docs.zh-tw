---
title: 架構適用于 Azure 的雲端原生 .NET 應用程式
description: 建立雲端原生應用程式的指南，利用 Azure 的容器、微服務和無伺服器功能。
author: ardalis
ms.date: 03/07/2019
ms.openlocfilehash: 7f14a690d0153edc43f0ce7f4e91c9e9cd2c6858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696782"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a>架構適用于 Azure 的雲端原生 .NET 應用程式

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

![封面影像](./media/cover.png)

發行者

Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組

Microsoft Corporation 部門

One Microsoft Way

Redmond, Washington 98052-6399

Copyright © 2019 by Microsoft Corporation

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。

本書是以「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。

此處所描述的一些範例僅供說明，純屬虛構。 任何實際關聯或連結純屬巧合。

Microsoft 與列於 https://www.microsoft.com 「商標」網頁的商標是 Microsoft 集團的商標。

Mac 與 macOS 是 Apple Inc. 的商標。

Docker 鯨魚標誌是 Docker, Inc. 的註冊商標。使用需要許可。

所有其他商標和標誌屬於其各自擁有者的財產。

製作

> **Steve "ardalis" Smith** - 軟體架構設計人員和講師 - [Ardalis.com](https://ardalis.com)
>
> **Vettor** -Microsoft-主要雲端系統架構師/IP 架構設計人員- [RobVettor.com](https://robvettor.com)

參與者和審核者：

> **Cesar De La Torre**，首席計畫經理，.net 小組，Microsoft
>
> **Nish Anil**，Microsoft NET 小組資深方案經理

編輯者：

> **Maira Wenzel**，Microsoft 的資深內容開發人員，.net 團隊

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

本指南的物件主要是開發人員、開發組長和架構設計人員，有興趣學習如何建立專為雲端設計的應用程式。

次要物件是技術決策者，他們打算選擇是否要使用雲端原生方法來建立應用程式。

## <a name="how-you-can-use-this-guide"></a>此指南的使用方式

本指南一開始會定義雲端原生，並介紹使用雲端原生原則和技術建立的參考應用程式。 除了這前兩個章節以外，本書的其餘部分會細分為著重于大部分雲端原生應用程式常見主題的特定章節。 您可以跳至下列任一章節，以瞭解雲端原生方法：

- 資料和資料存取
- 通訊模式
- 調整和擴充性
- 應用程式復原
- 監視與健康狀態
- 身分識別與安全性
- DevOps

本指南以 PDF 形式和線上版本提供。 請隨意將本檔或其線上版本的連結轉寄給您的小組，以協助確保這些主題的一般瞭解。 大部分的主題都是以一致的方式瞭解基礎原則和模式，以及與這些主題相關的決策所牽涉到的取捨。 本檔的目標是要為小組及其領導者提供針對其應用程式架構、開發和裝載做出明智決策所需的資訊。

>[!div class="step-by-step"]
>[下一個](introduction.md)
